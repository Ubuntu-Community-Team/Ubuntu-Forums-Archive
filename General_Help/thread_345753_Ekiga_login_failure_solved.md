---
title: "Ekiga login failure solved"
date: 2007-01-24
forum: General Help
---

### Post by cblanquer on 2007-01-24
If your Ekiga account cannot be reached when launching Ekiga softphone it maybe due to your  firewall.
What if both your hard and soft firewalls are disabled, any advice falls in those categories but your Ekiga sip account is still not reachable.

After several searches I found a different kind of problem and solution. I post it as maybe this can help you.

When re-reading for the 4th time Ekiga's manual ([http://www.gnomemeeting.org/documentation/ekiga.pdf](http://www.gnomemeeting.org/documentation/ekiga.pdf)) I decided to have a look to "gconf-editor" that I have not used up till now.

Instead of dealing with the ports used and so on, I had a general review and could easily discover that **Ekigas setup was using a wrong network device**.
Instead of my WiFi "ra0" it was trying to work with "eth0".
I did not find a way to change this from Ekiga's interface.
So simply changing the value in "gconf-editor" and restarting Ekiga, I could immediately log in to the SIP account in ekiga.net.
 (have a look to the screenshot)

---

