---
title: "Hangs after login"
date: 2007-02-19
forum: General Help
---

### Post by Moosetwik on 2007-02-19
I just installed Dapper for the first time today (never used it before) and I tried to configure my wireless. When I rebooted it says it is "Configuring Network Interface" but never goes anywhere, so I cancelled it. It then goes to the login screen. I login, and the screen just stays blank and nothing appears at all. (Mouse showing, and moveable)

---

### Post by senor_smile on 2007-02-19
I'm also having a very similar problem.  I have only recently been exposed to Linux.  I have installed Ubuntu 6.06 from the live cd.  It installed without a glitch.  I booted up and it found 216(MB) of updates to install.  That took several hours to download.  They all loaded.  I then rebooted and I was unable to get to the main gui.  The login screen appears and I enter my login and pass.  Then, it goes to a dark screen where I can move the mouse around, but it never loads the session.  I can, however, log into the Failsafe GNOME session.  I assume that some settings somewhere have become corrupt.  What should I be looking for to allow me to log in regularly? 

thanks

---

### Post by syspeck on 2007-02-20
I'm having similar problems...
"Configuring Network Interface"... only cancelling... I use wireless too.
After Login GUI don't initialize...  Only shows the mouse cursor and a dark screen.
However, I can open Firefox by a Multimedia key in my keyboard. Only this.
Please, if you find solution, show me please. Thanks.

---

### Post by senor_smile on 2007-02-22
I reinstalled ubuntu... now of course everything is working.  I wish I could have figured out how to fix the login problem before reinstalling the os though.

---

### Post by demauk on 2007-09-19
This is happening to me too. I have Xubuntu Feisty. Everything was working fine until I plugged in a wireless USB adapter, which slowed things down, eventually hanging. I removed the USB adapter and then I made the mistake of forcing a shutdown.

Anyway, I can access terminal logins, and the graphical login looks perfect, but once I authenticate I only get a grey/white background and a huge spinning mouse icon that actually responds to my mouse movements.

If I go on a terminal login and change the X resolution with [FONT="Courier New"]dpkg-reconfigure xserver-org[/FONT] the graphical login works as if nothing ever happened. But if I change the resolution again, it hangs again.

This definitely looks to me as if there's some sort of "corrupt session" file that keeps being loaded. Is there a way to get rid of all xsession information? Is it possible to re-configure the xserver so I can start with a brand new session?

---

### Post by demauk on 2007-09-20
I saw other threads with the same or similar problem. At least two of them suggested 
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```
(replace ubuntu-desktop with xubuntu-, kubuntu-, etc.)

Unfortunately this did not work for me.

I mentioned in my previous post that changing the resolution allowed me to log in, but I failed to mention that I also changed from the "nvidia" driver to the "nv" driver. So, in short, "nv" (in standard 1024x768 ) works, but "nvidia" (in my monitor's native 1440x900) doesn't. Again, the latter configuration used to work until I put in a wireless USB adapter and then forcibly did a hardware shut down.

I have even removed xubuntu-desktop and installed it again. And also fully removed nvidia-glx and installed it again. I keep thinking it must be some sort of corrupt xsession configuration, but so far I haven't found anything.

I've only had xubuntu installed for a few days, so I won't lose much by reinstalling the whole thing, but I don't want to do that every time I try out the wireless USB adapter.

---

### Post by demauk on 2007-09-25
Well, I had to reinstall, and this time I was more careful with my wireless setup. Everything has been running smoothly since.

I still wonder if there was another way ...

---

