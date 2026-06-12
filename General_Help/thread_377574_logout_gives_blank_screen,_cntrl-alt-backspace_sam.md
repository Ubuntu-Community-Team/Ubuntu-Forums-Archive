---
title: "logout gives blank screen, cntrl-alt-backspace same"
date: 2007-03-06
forum: General Help
---

### Post by sdowney717 on 2007-03-06
What should I check for.
At the blank screen, it appears to lock up, 
(keyboard numlock light wont change etc...)

At which point all I can do is pull the plug and reboot system.

I had installed beryl and XGL but then removed it
Also, why then is the beryl manger still in the panel and it still runs the beryl manager?
How do I really get rid of it.
[http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/XGL)

I had followed this link

---

### Post by teaker1s on 2007-03-06
if this is since a kernel update then boot options such as
NOAPIC NOAPCI may help. I had logout issue with feisty and xorg 7.2
If it's a beryl issue I'm not sure

---

### Post by sdowney717 on 2007-03-07
turned out it was a botched ATI video driver install.
prior to this, I had attempted to install ATI driver as an unknown xwindows install, that failed and installed using envy, went on to beryl and then noticed problems.
So I restored the partition with a backup
Then I ran envy ATI video installer
And its ok.

I can't emphasize enough how keeping good working backups have saved me time and again.

---

