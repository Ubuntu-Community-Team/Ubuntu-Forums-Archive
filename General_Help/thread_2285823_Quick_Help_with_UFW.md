---
title: "Quick Help with UFW"
date: 2015-07-08
forum: General Help
---

### Post by neu5eeCh on 2015-07-08
My question: If I want to block a site, like Facebook, I do the following:

```
dig facebook.com +short 
```
173.252.120.6

Then:
```
whois 173.252.120.6 | grep OriginAS 
```       
OriginAS:       AS32934

Then:

```
whois -h whois.radb.net -- '-i origin AS32934' | grep ^route 
```
```
route:      204.15.20.0/22 
route:      69.63.176.0/20 
route:      66.220.144.0/20 
route:      66.220.144.0/21 
route:      69.63.184.0/21 
route:      69.63.176.0/21 
route:      74.119.76.0/22 
route:      69.171.255.0/24 
route:      173.252.64.0/18 
route:      69.171.224.0/19 
route:      69.171.224.0/20 
route:      103.4.96.0/22 
route:      69.63.176.0/24 
route:      173.252.64.0/19 
route:      173.252.70.0/24 
route:      31.13.64.0/18 
route:      31.13.24.0/21 
route:      66.220.152.0/21 
route:      66.220.159.0/24 
route:      69.171.239.0/24 
route:      69.171.240.0/20 
route:      31.13.64.0/19 
route:      31.13.64.0/24 
route:      31.13.65.0/24 
route:      31.13.67.0/24 
route:      31.13.68.0/24 
route:      31.13.69.0/24 
route:      31.13.70.0/24 
route:      31.13.71.0/24 
route:      31.13.72.0/24 
route:      31.13.73.0/24 
route:      31.13.74.0/24 
route:      31.13.75.0/24 
route:      31.13.76.0/24 
route:      31.13.77.0/24 
route:      31.13.96.0/19 
route:      31.13.66.0/24 
route:      173.252.96.0/19 
route:      69.63.178.0/24 
route:      31.13.78.0/24 
route:      31.13.79.0/24 
route:      31.13.80.0/24 
route:      31.13.82.0/24 
route:      31.13.83.0/24 
route:      31.13.84.0/24 
route:      31.13.85.0/24 
route:      31.13.86.0/24 
route:      31.13.87.0/24 
route:      31.13.88.0/24 
route:      31.13.89.0/24 
route:      31.13.90.0/24 
route:      31.13.91.0/24 
route:      31.13.92.0/24 
route:      31.13.93.0/24 
route:      31.13.94.0/24 
route:      31.13.95.0/24 
route:      69.171.253.0/24 
route:      69.63.186.0/24 
route:      31.13.81.0/24 
route:      179.60.192.0/22 
route:      179.60.192.0/24 
route:      179.60.193.0/24 
route:      179.60.194.0/24 
route:      179.60.195.0/24 
route:      185.60.216.0/22 
route:      45.64.40.0/22 
route:      185.60.216.0/24 
route:      185.60.217.0/24 
route:      185.60.218.0/24 
route:      185.60.219.0/24 
route:      129.134.0.0/16 
route:      157.240.0.0/16 
route:      204.15.20.0/22 
route:      69.63.176.0/20 
route:      69.63.176.0/21 
route:      69.63.184.0/21 
route:      66.220.144.0/20 
route:          69.63.176.0/20 
route6:     2620:0:1c00::/40 
route6:     2a03:2880::/32 
route6:     2a03:2880:fffe::/48 
route6:     2a03:2880:ffff::/48 
route6:     2620:0:1cff::/48 
route6:     2a03:2880:f000::/48 
route6:     2a03:2880:f001::/48 
route6:     2a03:2880:f002::/48 
route6:     2a03:2880:f003::/48 
route6:     2a03:2880:f004::/48 
route6:     2a03:2880:f005::/48 
route6:     2a03:2880:f006::/48 
route6:     2a03:2880:f007::/48 
route6:     2a03:2880:f008::/48 
route6:     2a03:2880:f009::/48 
route6:     2a03:2880:f00a::/48 
route6:     2a03:2880:f00b::/48 
route6:     2a03:2880:f00c::/48 
route6:     2a03:2880:f00d::/48 
route6:     2a03:2880:f00e::/48 
route6:     2a03:2880:f00f::/48 
route6:     2a03:2880:f010::/48 
route6:     2a03:2880:f011::/48 
route6:     2a03:2880:f012::/48 
route6:     2a03:2880:f013::/48 
route6:     2a03:2880:f014::/48 
route6:     2a03:2880:f015::/48 
route6:     2a03:2880:f016::/48 
route6:     2a03:2880:f017::/48 
route6:     2a03:2880:f018::/48 
route6:     2a03:2880:f019::/48 
route6:     2a03:2880:f01a::/48 
route6:     2a03:2880:f01b::/48 
route6:     2a03:2880:f01c::/48 
route6:     2a03:2880:f01d::/48 
route6:     2a03:2880:f01e::/48 
route6:     2a03:2880:f01f::/48 
route6:     2a03:2880:1000::/36 
route6:     2a03:2880:2000::/36 
route6:     2a03:2880:3000::/36 
route6:     2a03:2880:4000::/36 
route6:     2a03:2880:5000::/36 
route6:     2a03:2880:6000::/36 
route6:     2a03:2880:7000::/36 
route6:     2a03:2880:f020::/48 
route6:     2a03:2880:f021::/48 
route6:     2a03:2880:f022::/48 
route6:     2a03:2880:f023::/48 
route6:     2a03:2880:f024::/48 
route6:     2a03:2880:f025::/48 
route6:     2a03:2880:f026::/48 
route6:     2a03:2880:f027::/48 
route6:     2a03:2880:f028::/48 
route6:     2a03:2880:f029::/48 
route6:     2a03:2880:f02a::/48 
route6:     2a03:2880:f02b::/48 
route6:     2a03:2880:f02c::/48 
route6:     2a03:2880:f02d::/48 
route6:     2a03:2880:f02e::/48 
route6:     2a03:2880:f02f::/48 
route6:     2a03:2880:f030::/48 
route6:     2a03:2880:f031::/48 
route6:     2a03:2880:f032::/48 
route6:     2a03:2880:f033::/48 
route6:     2a03:2880:f034::/48 
route6:     2a03:2880:f035::/48 
route6:     2a03:2880:f036::/48 
route6:     2a03:2880:f037::/48 
route6:     2a03:2880:f038::/48 
route6:     2a03:2880:f039::/48 
route6:     2a03:2880:f03a::/48 
route6:     2a03:2880:f03b::/48 
route6:     2a03:2880:f03c::/48 
route6:     2a03:2880:f03d::/48 
route6:     2a03:2880:f03e::/48 
route6:     2a03:2880:f03f::/48 
route6:     2401:db00::/32 
route6:     2a03:2880::/36 
route6:     2803:6080::/32



```
So, my question is this:

In order to block Facebook at the firewall (let's say) would I have to block every IP listed? If I do, is there quick and easy way (rather than entering each IP individually? Like so:

```
ufw reject out to 204.15.20.0/22 
```

& etc...

 And if not, how do I know which IP to block with UFW?

---

### Post by neu5eeCh on 2015-07-08
Okay, I thought up an ugly (probably) solution, which is to copy & paste the IPs into LibreOffice, and after some *finding and replacing*, this:

  ```
[COLOR=#000000][FONT=monospace]sudo ufw reject out to 204.15.20.0/22 && sudo ufw reject out to 69.63.176.0/20 && sudo ufw reject out to 66.220.144.0/20 && sudo ufw reject out to 66.220.144.0/21 && sudo ufw reject out to 69.63.184.0/21 && sudo ufw reject out to 69.63.176.0/21 && sudo ufw reject out to 74.119.76.0/22 && sudo ufw reject out to 69.171.255.0/24 && sudo ufw reject out to 173.252.64.0/18 && sudo ufw reject out to 69.171.224.0/19 && sudo ufw reject out to 69.171.224.0/20 && sudo ufw reject out to 103.4.96.0/22 && sudo ufw reject out to 69.63.176.0/24 && sudo ufw reject out to 173.252.64.0/19 && sudo ufw reject out to 173.252.70.0/24 && sudo ufw reject out to 31.13.64.0/18 && sudo ufw reject out to 31.13.24.0/21 && sudo ufw reject out to 66.220.152.0/21 && sudo ufw reject out to 66.220.159.0/24 && sudo ufw reject out to 69.171.239.0/24 && sudo ufw reject out to 69.171.240.0/20 && sudo ufw reject out to 31.13.64.0/19 && sudo ufw reject out to 31.13.64.0/24 && sudo ufw reject out to 31.13.65.0/24 && sudo ufw reject out to 31.13.67.0/24 && sudo ufw reject out to 31.13.68.0/24 && sudo ufw reject out to 31.13.69.0/24 && sudo ufw reject out to 31.13.70.0/24 && sudo ufw reject out to 31.13.71.0/24 && sudo ufw reject out to 31.13.72.0/24 && sudo ufw reject out to 31.13.73.0/24 && sudo ufw reject out to 31.13.74.0/24 && sudo ufw reject out to 31.13.75.0/24 && sudo ufw reject out to 31.13.76.0/24 && sudo ufw reject out to 31.13.77.0/24 && sudo ufw reject out to 31.13.96.0/19 && sudo ufw reject out to 31.13.66.0/24 && sudo ufw reject out to 173.252.96.0/19 && sudo ufw reject out to 69.63.178.0/24 && sudo ufw reject out to 31.13.78.0/24 && sudo ufw reject out to 31.13.79.0/24 && sudo ufw reject out to 31.13.80.0/24 && sudo ufw reject out to 31.13.82.0/24 && sudo ufw reject out to 31.13.83.0/24 && sudo ufw reject out to 31.13.84.0/24 && sudo ufw reject out to 31.13.85.0/24 && sudo ufw reject out to 31.13.86.0/24 && sudo ufw reject out to 31.13.87.0/24 && sudo ufw reject out to 31.13.88.0/24 && sudo ufw reject out to 31.13.89.0/24 && sudo ufw reject out to 31.13.90.0/24 && sudo ufw reject out to 31.13.91.0/24 && sudo ufw reject out to 31.13.92.0/24 && sudo ufw reject out to 31.13.93.0/24 && sudo ufw reject out to 31.13.94.0/24 && sudo ufw reject out to 31.13.95.0/24 && sudo ufw reject out to 69.171.253.0/24 && sudo ufw reject out to 69.63.186.0/24 && sudo ufw reject out to 31.13.81.0/24 && sudo ufw reject out to 179.60.192.0/22 && sudo ufw reject out to 179.60.192.0/24 && sudo ufw reject out to 179.60.193.0/24 && sudo ufw reject out to 179.60.194.0/24 && sudo ufw reject out to 179.60.195.0/24 && sudo ufw reject out to 185.60.216.0/22 && sudo ufw reject out to 45.64.40.0/22 && sudo ufw reject out to 185.60.216.0/24 && sudo ufw reject out to 185.60.217.0/24 && sudo ufw reject out to 185.60.218.0/24 && sudo ufw reject out to 185.60.219.0/24 && sudo ufw reject out to 129.134.0.0/16 && sudo ufw reject out to 157.240.0.0/16 && sudo ufw reject out to 204.15.20.0/22 && sudo ufw reject out to 69.63.176.0/20 && sudo ufw reject out to 69.63.176.0/21 && sudo ufw reject out to 69.63.184.0/21 && sudo ufw reject out to 66.220.144.0/20 && sudo ufw reject out to 69.63.176.0/20[/FONT][/COLOR]


```

Is there a more elegant way? And do I really need to block them all? Thanks! :-)

---

