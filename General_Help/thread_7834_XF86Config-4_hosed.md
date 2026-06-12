---
title: "XF86Config-4 hosed"
date: 2004-12-11
forum: General Help
---

### Post by Freakwitch on 2004-12-11
Ok, the first thing to understand is that I did something very, very stupid. ;-)

I accidentally erased my XF86Config-4 file. Long story; I thought I was doing so for another Linux distro I have installed on another partitition, but I hosed the Ubuntu config file by mistake. (Note to self: /dev/hda5/etc/X11/XF86Config-4 != /dev/hda6/etc/X11/XF86Config-4). ;-)

So what I'm wondering is, can I regenerate this file automatically? Of course I didn't have a backup. Or do I need to reinstall Ubuntu? There must be a way...

I also need to get my lilo.conf (from the other distro) to recognize the Ubuntu kernel for boot....

I'm running Ubuntu on a Toshiba Satellite M35X-S149 laptop, which I wrote about at [http://jwl.freakwitch.net/Linux_Toshiba_M35X-S149.html](http://jwl.freakwitch.net/Linux_Toshiba_M35X-S149.html) .

Silly me, can anyone help? 

I'm very enthusiastic about Ubuntu thus far.....very cool distro, even if it does use GNOME... ;-)

---

### Post by Freakwitch on 2004-12-12
> **Freakwitch]Ok, the first thing to understand is that I did something very, very stupid.  said:**
> http://jwl.freakwitch.net/Linux_Toshiba_M35X-S149.html[/url] .

Silly me, can anyone help? 

I'm very enthusiastic about Ubuntu thus far.....very cool distro, even if it does use GNOME... ;-)
 OK, to answer my own question for posterity: the answer is yes the file can be regenerated. The solution is here:
[http://www.ubuntulinux.org/wiki/XautoconfigurationDebug/view?searchterm=XF86Config-4](http://www.ubuntulinux.org/wiki/XautoconfigurationDebug/view?searchterm=XF86Config-4)

---

### Post by kdavison007 on 2004-12-19
Well, I hosed my XF86Config-4 file as well.  It's completely empty so I followed your link, but all I see is something about running the DEBUG command.  When I do that on the CLI it doesn't rocognize that as a command.  And yes, I'm using sudo in front.  I've tried running it as user root as well, but it doesn't take that command.  What am I doing wrong?

---

### Post by WW on 2004-12-19
kdavison007,

I think you are referring to this part:
```
DEBUG_XFREE86_PACKAGE=yes XF86FORCEPROBE=yes dpkg-reconfigure xserver-xfree86
```
The command being run here is **dpkg-reconfigure**.  The stuff in front of the command defines two environment variables, DEBUG_XFREE86_PACKAGE and XF86FORCEPROBE.  I don't know what you typed, so this is just a guess, but this command  will not work if you change the underscores to spaces, or if you put extra spaces before or after the = characters.

---

### Post by kdavison007 on 2004-12-19
Thanks for the reply.  I'll give it another try.  I'm pretty sure I typed it all in correctly, obeying the underscores, spaces, and cases.  I think it's trying to run DEBUG as a command.  Do I need to start with dpkg?

---

### Post by kdavison007 on 2004-12-19
Well, tried just running dpkg-reconfigure xfree-86 and it walked me through the configuration process, but when I was all done it didn't recreate another XF86Config-4 file.  Ugh, this is annoying.

---

### Post by john280z on 2004-12-22
If you have access to a high speed internet connection, I have been able to recover an XF86Config-4 file by booting one of the small live CD's (such as dsl or insert - download and burn the iso image) ). The live CD creates its own XF86Config-4 file (in ram) that can then be copied to the correct directory - /etc/X11. 
   Just make sure to use a live CD that is from the same distro as Ubuntu!

---

### Post by jtapper on 2004-12-30
[QUOTE=kdavison007]Well, tried just running dpkg-reconfigure xfree-86 and it walked me through the configuration process, but when I was all done it didn't recreate another XF86Config-4 file.  Ugh, this is annoying.[/QUOTE]

This may be a little late, but have you tried 'xf86config' command?
It should do the trick.

---

### Post by kdavison007 on 2005-01-03
Thanks.  I remember that next time I'm in the same bind.  Actually, the best idea is to backup the file.  I had to return the laptop because it was having thermal problems anyway, but thanks for the suggestion.

---

### Post by ccsaxton on 2005-02-22
Sometimes you can recover an old XF86Config by going into /var/backups/xfree86...its saved me a few times!

---

