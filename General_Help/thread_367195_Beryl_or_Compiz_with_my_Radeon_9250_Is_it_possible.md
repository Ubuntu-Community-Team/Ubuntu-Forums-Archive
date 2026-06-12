---
title: "Beryl or Compiz with my Radeon 9250: Is it possible?"
date: 2007-02-21
forum: General Help
---

### Post by Rippy on 2007-02-21
The title says it all.. apparently the ATI drivers don't have some key ability that Beryl requires. From what I'd read, there's a workaround, but it requires the latest drivers. The latest ATI drivers don't support my card.

So, it's as simple as that: should I even dream of getting Beryl or Compiz working on my PC?

Thanks,

-Rippy

---

### Post by kodoku on 2007-02-21
ATI cards are notorious for compatibility issues.

You could try using envy [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html") 

After installing the deb, just run "envy" in the terminal and follow the directions.  This script will detect the model of your graphics card (ATI and nVidia) and download proprietary drivers from their official websites.

Hopefully this works, if not, I'm sure there are plenty of ATI people floating around the forum who could help.

EDIT: Actually, ignore the above, try this -> [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI")

---

### Post by john.nicholls on 2007-02-22
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

This is what I used to get Beryl working on Edgy with a Radeon 9250. So yes, it's possible.

---

### Post by Waappu on 2007-02-22
Hi

This guide works on my ATI 9250
[http://ubuntuforums.org/showthread.php?t=338771](http://ubuntuforums.org/showthread.php?t=338771)

My script is based guide that john.nicholls's post

EDIT:

I want to say that I didn't get XGL working with my card but AIGLX works great. Script is for that and Beryl

---

### Post by Rippy on 2007-02-22
I think I'm gonna try that wiki guide. For it to work, do I need the regular fglrx driver, or the open-source one? It doesn't say anything about that.

From what I've read, using xgl has some issues, like slowdown caused by running both it and x.org at once, so I'd like to try with AIGLX first.

---

### Post by gwinston99 on 2007-02-22
I am running Edgy on a Dell Latitude C610.  Graphics card is ATI Radeon M6LY.

I followed the instructions in this thread.  After running the script, when I rebooted, x failed to start.  I rebooted into terminal mode and restored my xorg.conf from the backup.  This got my system up and running.

I really would like to run beryl (or compiz).  I am attaching the xorg.conf created by Envy to see if anyone can help me troubleshoot it and get it working.

Thanks in advance.

---

### Post by Rippy on 2007-03-04
Well, I used this guide:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
And it worked perfectly. Got Compiz running and everything, and no doubt I could get beryl running too, although for performance purposes I picked Compiz.

---

