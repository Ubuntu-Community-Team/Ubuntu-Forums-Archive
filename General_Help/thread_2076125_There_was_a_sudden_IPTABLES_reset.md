---
title: "There was a sudden IPTABLES reset"
date: 2012-10-25
forum: General Help
---

### Post by Okturion on 2012-10-25
Hello!
Some months ago I configured IPTABLES on my ubuntu machine and added some basic rules. It was running quite good and I had no problems.
Always when I opened a ssh connection to my server I had to wait 5 seconds until I could enter my password. Today it was much faster and I wondered why. Then I saw that all rules of my IPTABLES configuration (iptables -L) got reseted. How is this possible? And ideas?
Thanks in advance!

---

### Post by The Cog on 2012-10-25
If you directly enter iptables rules, they just go into memory. Next time you reboot, they are lost. If you want hte rules to be persistent, you have to arrange for a script to re-enter the rules every time the computer boots. I think the normal way to do this is to a create a script (e.g. /etc/firewall.rc) and add a line calling the script to /etc/rc.local.

---

### Post by Okturion on 2012-10-25
Yeah, maybe the server got restarted by the provider and so iptables configuration was reseted.
Thanks for your help, I will add a script then...

---

