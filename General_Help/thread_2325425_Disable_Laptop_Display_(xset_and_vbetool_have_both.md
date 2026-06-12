---
title: "Disable Laptop Display (xset and vbetool have both failed)"
date: 2016-05-22
forum: General Help
---

### Post by robo731 on 2016-05-22
I'm running Ubuntu Server on a Dell Inspiron 15R Laptop. I'd like to have the display turned off as it is unnecessary. I've tried using ```
xset dpms force off
``` which returns ```
xset: unable to open display ""
``` I've also tried ```
vbetool dpms off
``` which gives me ```
Real mode call failed
``` I've tried running these commands locally on the machine and achieved these same results so I don't believe SSH is the issue. From what I've read, I think vbetool's problem has something to do with the laptop lacking acpi support. I'm not sure what the problem is with xset. People who have had this problem with xset have all had an issue with trying to run it through SSH, but I ran it locally and encountered this problem. Any ideas on how I can do this?

---

