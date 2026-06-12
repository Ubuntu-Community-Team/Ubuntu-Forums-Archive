---
title: "transarent proxy"
date: 2008-02-03
forum: General Help
---

### Post by rcguzon on 2008-02-03
Hello Everyone, 
i dont know if this is the right place to post. But i do hope this is the right one.

I have a router, which acts as my gate way. and i want to administer a transparent proxy from 192.168.0.6. I used the tutorials i found for squid. 
            
          httpd_accel_host virtual
          httpd_accel_port 80
          httpd_accel_with_proxy on
          httpd_accel_uses_host_header on

          # iptables -t nat -I PREROUTING 1 -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

this works as a proxy, but it wont do transparency.
here are the addresses of my machines

an MP-11 connected to the DLINK wireless router with ip 192.168.0.1
3 3com baseline switch connected to the DLINK router.
my proxy server is connected to the Dlink router with ip 192.168.0.6

Can anyone help me with this one. I work in a laboratory which is trying to migrate to open source. my knwledge in linux is quite limited, but i can follow instructions. tnx

---

### Post by joebeasley on 2008-02-03
Set the other machines default gateway to 192.168.0.6 and add iptables rules allowing those boxes to connect outbound.

---

### Post by rcguzon on 2008-02-04
Set the other machines default gateway to 192.168.0.6 and add iptables rules allowing those boxes to connect outbound. 

am i getting this rigth: in the router i will set its default gateway to 192.168.0.6. How about the rules where should i place them? on the router or on the pc? tnx again

---

