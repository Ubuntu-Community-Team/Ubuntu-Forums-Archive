---
title: "My Own IP  and Loopback Listed as Connected Domains when accessing a Website"
date: 2019-11-26
forum: General Help
---

### Post by maglin2 on 2019-11-26
When I go to this online bank login page
[https://www.rbsdigital.com/Login.aspx](https://www.rbsdigital.com/Login.aspx)
uBlock origin indicates the following domains connected


rbsdigital.com
[www.rbsdigital.com]("http://www.rbsdigital.com")
127.0.0.1
xx.xx.xx.xx ----my own IP
adobedtm.com
assets.adobedtm.com
rbs.co.uk
[www.rbs.co.uk]("http://www.rbs.co.uk")

I'm not sure what it means, but I have never seen the 127.0.0.1 loopback IP and my own IP listed in the connected domains for any other site I visit - including other bank login pages.

It happens with firefox and chromium.

Can anyone shed any light on what it might mean? 

Thanks
Dave
(I have no reason to think this is an ubuntu issue - so feel free to move (or remove) the post if it is non-compliant on this board).

---

### Post by maglin2 on 2019-11-30
I think it's probably conducting some sort of security scan  - looking for eg VNC remote access connections or open ports typically used by trojans. I'm not clever enough to read the js to find out though. There is a discussion of similar activity by Halifax (and other banks) here [https://www.theregister.co.uk/2018/08/07/halifax_bank_ports_scans/](https://www.theregister.co.uk/2018/08/07/halifax_bank_ports_scans/)


Suppose they found something. This being a bank, do you think they would either:


(a) warn me, and help me to improve my security setup, or


(b) keep it on file so that if my account is ever defrauded they can deny responsibility, blame me, and say they have evidence that my online login security practices were poor.
[COLOR=#494C4F][FONT=arial]
[/FONT][/COLOR]

---

