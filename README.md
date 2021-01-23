![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of Shame (2021-01-23)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
62.102.148.68|-|10
171.25.193.77|tor-exit1-readme.dfri.se|10
171.25.193.78|tor-exit4-readme.dfri.se|10
171.25.193.20|tor-exit0-readme.dfri.se|10
77.247.181.162|chomsky.torservers.net|9
185.220.100.252|tor-exit-1.zbau.f3netze.de|8
51.178.52.245|tor-exit-node.neowutran.ovh|8
51.75.144.43|ns3129517.ip-51-75-144.eu|8
167.88.7.134|the-windy-onion.tor-exits.alec.ninja|8
185.220.101.24|-|8
185.220.102.4|communityexit.torservers.net|8
185.220.102.253|tor-exit-relay-7.anonymizing-proxy.digitalcourage.de|8
185.220.101.206|-|8
185.220.102.243|185-220-102-243.torservers.net|7
185.220.102.248|tor-exit-relay-2.anonymizing-proxy.digitalcourage.de|7
185.220.102.249|tor-exit-relay-3.anonymizing-proxy.digitalcourage.de|7
94.142.241.194|tor-exit.vrij-heid.nl|7
167.172.169.44|-|7
45.154.255.147|cust-147.keff.org|7
185.220.100.253|tor-exit-2.zbau.f3netze.de|7
185.220.100.254|tor-exit-3.zbau.f3netze.de|7
94.230.208.147|tor3e1.digitale-gesellschaft.ch|7
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|7
185.130.44.108|tor-exit-se1.privex.cc|7
185.220.101.215|-|7
174.138.12.116|-|7
185.220.101.193|-|7
162.247.74.27|-|7
104.244.77.101|LuxembourgTor8.lu|7
51.77.135.89|ns31066279.ip-51-77-135.eu|7
104.244.76.13|tor-exit-node.spongebob.nicdex.com|7
62.102.148.69|-|7
185.129.62.62|tor01.zencurity.dk|7
167.172.161.10|-|7
185.220.100.247|tor-exit-8.zbau.f3netze.de|7
185.220.100.242|tor-exit-15.zbau.f3netze.de|7
185.220.101.13|-|7
107.189.10.251|-|7
185.220.100.241|tor-exit-14.zbau.f3netze.de|7
195.206.105.217|zrh-exit.privateinternetaccess.com|7
104.248.29.6|-|7
94.102.49.190|flower.census.shodan.io|7
185.191.124.151|-|7
185.191.124.150|-|7
185.220.101.9|-|7
185.220.101.8|-|7
167.172.161.171|-|7
80.82.77.139|dojo.census.shodan.io|7
185.220.101.22|-|7
185.220.101.21|-|7
185.220.101.16|-|7
77.247.181.165|politkovskaja.torservers.net|7
176.10.104.240|tor1e1.digitale-gesellschaft.ch|7
176.10.99.200|accessnow.org|7
159.89.110.115|-|7
138.197.179.100|-|7
185.100.86.182|-|7
95.211.230.211|-|7
149.202.238.204|204.238.202.149.fr-sbg.flexcloud.seflow.it|7
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|7
159.89.30.109|-|7
199.19.226.67|sldrottr.xyz|7
