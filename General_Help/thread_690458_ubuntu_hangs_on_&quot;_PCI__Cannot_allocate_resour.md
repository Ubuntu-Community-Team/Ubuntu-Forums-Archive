---
title: "ubuntu hangs on &quot; PCI : Cannot allocate resource region 7 of bridge&quot;"
date: 2008-02-07
forum: General Help
---

### Post by dresen on 2008-02-07
Hello, i've recently installed ubuntu and everything is working our very well, except for the fact that it gives me these two errors on boot:

 PCI : Cannot allocate resource region 7 of bridge
 PCI : Cannot allocate resource region 8 of bridge

then the screen goes black and it hangs there, HOWEVER, If I press ctrl+alt+f1 it goes back to booting up normally and everything works fine, so obviously what ever is causing it to stop isn't hanging the entire system and I can recover it easily but it is still kind of annoying, anyone know of a solution to this?

---

### Post by jakelute on 2008-02-07
Hi there. Your problem is similar to mine -- see my post here [http://ubuntuforums.org/showthread.php?t=690122&highlight=cannot+allocate+resource+region](http://ubuntuforums.org/showthread.php?t=690122&highlight=cannot+allocate+resource+region) -- like you, I've had no replies to my question -- I've been trying various things and reading various other forums -- one possible thing worth trying might be to make sure your system BIOS are updated to the latest version -- I'm trying to do the same at the moment.
good luck! I'd be delighted to know if you find anything useful, and likewise, I'll pass any findings on to you.

---

### Post by meazz1 on 2008-02-07
jakelute, I was getting the same exact error.
I installed startupmanager and configured it. That fixed my problem.

$sudo apt-get install startupmanager

Once it has installed, you can configure it under System-> Administration.
Change the color to 16 or 24 bit, and screen size to 800X600.

I have a 20" Wide screen and I was having the same problem.

I am a new to Linux and above steps helped me, while I was searching this forum for Splash screen fix.

---

### Post by jakelute on 2008-02-07
Thank you very much, I'll look into that!
J.

---

