---
title: "inetd where in 6.06?"
date: 2007-05-27
forum: General Help
---

### Post by doccpu on 2007-05-27
I want to run samba and swat under 6.06 desktop. But no connection to swat.
inetd is not running or even on the drive, so what does 6.06 use? how tell it to run swat? how restart inetd if its not even there? This is really getting frustrating as none of the info given by people is right. So where can i get a definitive manual for ubuntu 6.06 telling how it loads, what it loads , and how it is working?:(

---

### Post by tszanon on 2007-05-28
> **doccpu said:**
> I want to run samba and swat under 6.06 desktop. But no connection to swat.
inetd is not running or even on the drive, so what does 6.06 use? how tell it to run swat? how restart inetd if its not even there? This is really getting frustrating as none of the info given by people is right. So where can i get a definitive manual for ubuntu 6.06 telling how it loads, what it loads , and how it is working?:(
inetd is not installed by default. Run synaptic, search for it, and install it. I think it will set itself up to run on every boot.
You will notice that there is a package called xinetd. According to its description, it's better than inetd, and that's what I've installed. VMWare asked for inetd, I got xinetd, and no problems at all.

Edit: probably using "apt-get install xinetd" will do the job, instead of using synaptic. :)

---

