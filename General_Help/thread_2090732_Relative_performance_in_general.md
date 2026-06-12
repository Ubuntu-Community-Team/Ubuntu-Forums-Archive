---
title: "Relative performance in general"
date: 2012-12-03
forum: General Help
---

### Post by j8tennant on 2012-12-03
This is my first intstallation of Ubuntu, and I am not certain what to expect.  It seems to me that panels (windows, whatever) load quite slowly, and it seems to appear in three steps on the display.  (Using vbox on an Asus laptop.)

Also, the mouse cursor turns on and off (true, it is mostly on), and does not seem to maintain focus.  (Sometimes when I want to click in something in a window, I get something on the side-panel (or a balloon from the side-panel) instead of what I want.

I think this may be a timing issue, but sometimes samba is unable to connect to the host and machines connected through it.  It is obvious that samba sets up correctly "out of the  box", since often I can see the shares I expect.

The next comments should be posted in another thread.  But, as an absolute newbie to this, I'm not sure where.  When I attempt a "mount -t vboxsf", it tells me it doesn't know the type.  Other related threads seem to discuss groups (e.g., vboxsf group), but this seems a bit more basic than that.

Except for performance issues (and my unfamiliarity with Gnome and Unify (or Unity)), Ubunto seems to be an excellent distribution.  Previously, I used SuSE, but I can't get samba to work at all in that most recent distribution.

I can use my SuSE installation, since I've got the shared file system mounted (something I can't do in Ubuntu); I prefer the SuSE with respect to user interface and speed.

---

### Post by Cheesemill on 2012-12-03
What version of Ubuntu are you using?

---

### Post by HermanAB on 2012-12-03
Howdy,

If you want speed, install XFCE or LXDE.  The default Unity desktop environment makes any computer slow.

---

### Post by j8tennant on 2012-12-03
Ubuntu 12.10.  Virtual box 4.2.  

I'm not sure of the SuSE designation I'm using, but I'm pretty sure it is based on the same Linux base as Ubuntu.  

I've installed Kubuntu on another virtual machine, but haven't done much with it, since the performance issues seem (at first glance) to be the same as Ubuntu.

Thanks.

---

### Post by ibjsb4 on 2012-12-03
> **HermanAB said:**
> If you want speed, install XFCE or LXDE.  The default Unity desktop environment makes any computer slow.

+1; will be faster.

[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

---

### Post by Cheesemill on 2012-12-03
There is a known performance issue running 12.10 in VirtualBox.

[http://useranswer.com/answer/why-does-an-ubuntu-12-10-guest-in-virtualbox-run-very-very-slowly/](http://useranswer.com/answer/why-does-an-ubuntu-12-10-guest-in-virtualbox-run-very-very-slowly/)

You can either try the fix outlined in the above link or use Ubuntu 12.04 instead which doesn't have this issue.

---

### Post by ibjsb4 on 2012-12-03
> **Cheesemill said:**
> There is a known performance issue running 12.10 in VirtualBox.

[http://useranswer.com/answer/why-does-an-ubuntu-12-10-guest-in-virtualbox-run-very-very-slowly/](http://useranswer.com/answer/why-does-an-ubuntu-12-10-guest-in-virtualbox-run-very-very-slowly/)

You can either try the fix outlined in the above link or use Ubuntu 12.04 instead which doesn't have this issue.

Thanks Cheesemill; was not aware of that.

---

### Post by j8tennant on 2012-12-03
Thanks, everyone.  I'll look into the VirtualBox vs. 12.10 performance issue.  However, I installed lubuntu (using the light desktop manager), and it works very, very satisfactorily.

I was disappointed that samba did not work "out of the box," but, for no particular reason, I installed "smb4k", and samba is now working.  (I did glance at what was being installed, and the base samba package did happen.)

On the whole, I am a bit disappointed by software package management, which seems more awkward than the equivalent provided by SuSE.  I also haven't really found how and where to do system administration tasks.  On the other hand, I do now (thanks to this thread) have a system which works adequately.

Thank you all.

---

### Post by oldos2er on 2012-12-03
What are your hardware specs?

---

