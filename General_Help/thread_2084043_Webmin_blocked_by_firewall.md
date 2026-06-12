---
title: "Webmin blocked by firewall??"
date: 2012-11-14
forum: General Help
---

### Post by geekJuice on 2012-11-14
Hi,

I am in the process of setting up my first server through Rackspace. Due to not being 100% comfortable with the command line I have tried to install webmin. I can access it through ssh using lynx and the url "localhost:10000" but I would like to access it through my web browser on my desktop but get a 105 error "Web Page Unavailable"

Below is the output from iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
REJECT     all  --  anywhere             127.0.0.0/8          reject-with icmp-p                                                                                                             ort-unreachable
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTA                                                                                                             BLISHED
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere             state NEW tcp dpt:                                                                                                             51234
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
LOG        all  --  anywhere             anywhere             limit: avg 5/min b                                                                                                             urst 5 LOG level debug prefix "iptables denied: "
REJECT     all  --  anywhere             anywhere             reject-with icmp-p                                                                                                             ort-unreachable
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:webmin

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
REJECT     all  --  anywhere             anywhere             reject-with icmp-p                                                                                                             ort-unreachable

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere

Could anyone please tell me if that is set up correctly to allow webmin. I have also tried disabling iptables using "sudo service ufw stop" but it hasn't helped.

Many thanks

---

