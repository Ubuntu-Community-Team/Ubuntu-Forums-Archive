---
title: "Removing Kmail screwed everything - Can't reverse"
date: 2014-02-26
forum: General Help
---

### Post by bjngchn on 2014-02-26
Installed new kubuntu on new computer (eventually, after some problems). Everything was ok. Computer makes some unexplainable noise, so I decide to remove programs I never use. I was thinking uninstalling unused programs was safe. WHAT HAPPENED: sudo apt-get remove kmail ; strangely it requires internet connection. 300 MB would be freed , great. so ok'ed it. Then I saw it was removing everything. It is like burning house while lighting a cigarette. So did ctrl+C or ctrl+Z to stop this process. But damage was done already. Now all programs I care about, except firefox, including terminal and dolphin don't work. How will all this be reversed now? Also how can I know some innocent looking action, like uninstalling a never-to-be-used program can do such big damage. .. btw a similar thing happened while editing firefox before.

---

### Post by ian-weisser on 2014-02-26
Yeah, that's why the package manager tells you what it wants to remove, and gives you a chance to abort.
300MB of removed packages should be a big flare-lit warning that you probably should abort.
I read those lists of proposed installs/removes. Every time.

Since installing kubuntu from .iso marks many other KDE applications as manually-installed (protecting them and their dependencies from autoremoval), your problematic install was likely related to your problematic uninstall.

Reverse is simple. Install what you do use: Terminal, dolphin, etc.

Did the removal fix your unexplainable noise?

If you cannot use a terminal in Kubuntu, use a tty (CTRL+ALT+F1) to reinstall your terminal. When complete, use (CTRL+ALT+F7) to return to Kubuntu.

---

### Post by bjngchn on 2014-02-27
Thanks for reply. I will try to try. But I can't even open the computer now.  The disk driver for /dev/mapper/kubuntu--vg-swap_1 is not ready or nor present. Wait, Skip, or Manual recovery. None works.... Noise, I suspect might be due to a hardware spy working all the time. Computer is new but world is dirty.

---

### Post by bjngchn on 2014-02-27
Ok, I can use command line after CTRL+ALT+F1 and install stuff with sudo. But I still can't login normally: I don't get login screen, and have the same error (more precisely, nothing happens) I mentioned above. Should I do sudo apt-get install kmail ?

---

### Post by monkeybrain20122 on 2014-02-27
Why don't you just use phonon instead of the terminal? It is much more explicit and intuitive especially when you are not sure what you are installing and/or removing.
BTW, KDE is not modular so removing some 'unused programs" may break KDE (one reason that I hate it :)) . Better to leave them alone, they don't take up much space and won't slow you if they are not running (except for nepomuk which is always running and definitely cannot be removed)

---

### Post by ian-weisser on 2014-02-27
> **bjngchn said:**
> Should I do sudo apt-get install kmail ?

I wouldn't.
You are mixing up the original problem (your problematic install) with the event that brought the problem to your attention (kmail).
kmail was not the problem. kmail was a symptom of the problem.

Only install what you will actually use.

---

### Post by bjngchn on 2014-02-27
Problem now is: I can't login graphically, so I can't use the computer in any meaningful or useful way.. I didn't install kmail, it was already there. I don't know what I need. Basically I only need one thing:  to be able to login graphically (instead of using command line)..... I hadn't done anything unusual when installing kubuntu. I just installed directly. Previous versions of kubuntu didn't work, but last one (13.10) worked. Once, editing firefox screwed the system, and I had to follow instriuctions in another thread to fix it. There must be a similar fix here. ... I probably don't need terminal, because I can login with command line after CTRL+ALT+F1..... When I first started this thread, I was logged in graphically, was able to use firefox, but not dolphin or terminal or even reinstall them. Now I can install them, but I can't login graphically to use anything. So probably installing what I need won't fix the problem. There must be something which I don't need, but is required and associated to kmail in some way.

---

### Post by ian-weisser on 2014-02-27
The graphical login is provided by the *lightdm* package and/or the *kdm* package.
Install the *kde-workspace* package. It will include the appropriate graphical login package, plus others that form the minimum for a KDE install. You are probably missing it if your KDE system is not working.

If you really want to know which packages are associated with with other packages, see **man apt-cache**

---

### Post by bjngchn on 2014-02-27
Thanks , now graphical login is possible. I still get the same error, but after waiting I get the  login screen. After login not everything works properly. Computer is slow at the beginning. Starts with crash error, and kwin error (unstable kwin). Klauncher doesn't work, but after removing panel and adding it back it works. I don't see terminal when I search for it. I can use firefox or dolphin, but there is a problem.  They open at the left top corner. They can't be moved or closed. FIle-Edit-View... menu doesn't appear.  in Klauncher some programs don't have icons. ... So in any case there seems to be a basic problem related to displaying desktop now. Somewhere on the panel when I moved to cursor there, it said something like "showdesktop missing", or something like this.

---

