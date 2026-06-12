---
title: "Gonna install Vista... anything I should know before?"
date: 2007-02-02
forum: General Help
---

### Post by limitedmage on 2007-02-02
Hi,

I'm currently running a dual-boot machine with Ubuntu 6.10 and Windows XP. I want to install a clean version of Vista as soon as I get it, in a partition I have already separated for it.

I've only posted here to see if anyone has had any issues of the Vista installation affecting the MBR and Grub. I don't want to be stuck with only Vista for the time I take fixing the problem.

If there is any issue, how can I prevent it or easily repair it? Does Grub automatically detect a new OS or do I have to add it in myself? I have no problem in editing configuration files, so any sort of help would be useful.

Thanks in advance.

~LimitedMage

---

### Post by llamakc on 2007-02-02
Grub doesn't automatically recognize another installation of an o/s upon boot. The Ubuntu Install does a good job of recognizing XP, but I have no idea about Vista. Good luck, back up your data, and then install e17 in Ubuntu.

---

### Post by limitedmage on 2007-02-03
What's e17?

---

### Post by llamakc on 2007-02-03
[http://www.google.com/search?q=e17&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=e17&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a)

It is Enlightenment and comes up with a search of Google. 

[http://www.enlightenment.org/](http://www.enlightenment.org/)

Here's what I was referring to:

[http://www.enlightenment.org/Enlightenment/DR17/](http://www.enlightenment.org/Enlightenment/DR17/)

---

### Post by bodhi.zazen on 2007-02-03
I am not following the e17 recommendation ... although I think ELive is a great distro ...

After you install Vista you will need to re-install grub to boot Ubuntu.

See this how-to:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Also some people like supergrub:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

post if you have problems ...

---

### Post by jeremy on 2007-02-03
You should know that Vista is the latest iteration of a thing called "windows", and that it is highly susceptable to virus and other nasties!

---

### Post by shironeko on 2007-02-03
As far as I know, vista smashes grub completely and you'll have to reinstall it.

BTW, why do you want VISTA?
It's been tested and XP performs much better than Vista. The only reason you could have is DirectX10 for playing games....

---

