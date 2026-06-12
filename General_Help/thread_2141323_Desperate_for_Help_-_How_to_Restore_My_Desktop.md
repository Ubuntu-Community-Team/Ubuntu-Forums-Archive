---
title: "Desperate for Help - How to Restore My Desktop?"
date: 2013-05-02
forum: General Help
---

### Post by kepz on 2013-05-02
I know I know... let me say this before you all give me lectures.  I should have validated that the instructions I was following on the internet would work to install something I was trying to work on.

Yes, I found some instructions to get VNC Remote working on my desktop so I can remote to my Android device.  But the instructions I read made me install something to with gdm I think and now it has reset my logon as if I'm starting a whole new logon.  It hasn't deleted my 'Home' folder though but this new logon doesn't have a home folder.  It's like I'm running in a similar logon in Safe mode because I can't log out of it and it won't let me do other things but it doesn't have a resolution of Safemode.  I can't find the webpage that I was folling insrtructions... but the instructions bought up a BIOS instructions which asked me to select GDM or (from memory, I wasn't reading properly) lgdm?  But I selected GDM and that's when it went all stupid and I had to force reboot.

Can someone help me get it back to how I had if you understand what's going on here please.  Desperate for help.

---

### Post by grahammechanical on 2013-05-02
I do not think that the instructions brought up BIOS. I think that you were asked to choose either GDM (Gnome Display Manager) or LightDM (standard login manager for Ubuntu). What version of Ubuntu are you using? Did you see something similar to what is illustrated here?

[http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html](http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html)

Can you login and get a working desktop? This may help you:

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

You may need to run these two commands

```
sudo stop gdm
``` ```
sudo start lightdm
```

Regards.

---

### Post by kepz on 2013-05-02
That 2nd screen is similar to what I saw but had more writing.  That's my technical word to describe what I saw lol.

But the login I'm at the moment won't allow me to run Terminal.  What's going on?  Is it some safemode I'm in or some restricted logon?  How can I get terminal to work and get my default desktop back?

I'm using Ubuntu 13.04.

---

### Post by grahammechanical on 2013-05-02
Here is what I suggest. It seems complicated but it is the simplest way of doing this that I know.

1) At the Grub menu select Advance Options for Ubuntu and then select Recovery Mode.
2) At the next screen select Resume. That sometimes gets us to a desktop. At least its worth a try.
3) If resume does not work try Recovery mode again and select Failsafex.
4) At the next screen press Esc to back out of Failsafex to the first Recovery mode screen.
5) Now select Root - Drop to a root shell prompt.

Why the messing around? Recovery mode>Root only gives us a file system in read only mode. Cannot change anything. But Recovery mode Failsafex sets the file system in read/write mode. So, go into and then out of failsafex to get a file system in read/write mode when we choose Root shell prompt.

at the root shell prompt you can try those two command I gave earlier. Followed by ```
startx
``` or you can reboot with ```
shutdown -r now
```

Another command to try is

```
dpkg-reconfigure lightdm
```

Some of these commands require sudo but as we are at a root shell prompt we do not need sudo. If this seems like guessing, then you are right but that reconfigure lightdm command should bring up a configuration dialog like the first one you saw. Notice also, that we first need to stop one display manager before starting another one. I am guessing that failure to do that may have caused this.

Oh, by the way, [code]shutdown -h now{/code] shuts down the machine. when run from a terminal it needs sudo.

See how you go. Regards.

---

### Post by kepz on 2013-05-02
OK Mr Mechanical... here it goes.  I'm getting this thread up on my tablet so I can read the direct and informative instructions. BRB...

EDIT:  P.S.Thank you so much replying so promptly to help me.  People like I wish we had more of on the internet.  Cheers!

---

### Post by kepz on 2013-05-02
Guess what I found when I logged onto my Tablet?  Fantastic how Chrome syncs from desktop to mobile devices.  Chrome had remembered the website I found and followed instructions.

[http://www.webhostingtalk.com/showthread.php?t=1029327](http://www.webhostingtalk.com/showthread.php?t=1029327)

I only got as far as "sudo /etc/init.d/gdm start" and had that prompted I mistakenly described it as a bios screen.  It hung when I selected GDM and I had to restart my machine and that's where I now get the desktop I currently have and cannot start Terminal or logout.

Does the above help my case?

I also tried what you've posted and I still get the desktop I'm currently using which is restricted.

---

### Post by kepz on 2013-05-05
> **grahammechanical said:**
> Here is what I suggest. It seems complicated but it is the simplest way of doing this that I know.

1) At the Grub menu select Advance Options for Ubuntu and then select Recovery Mode.
2) At the next screen select Resume. That sometimes gets us to a desktop. At least its worth a try.
3) If resume does not work try Recovery mode again and select Failsafex.
4) At the next screen press Esc to back out of Failsafex to the first Recovery mode screen.
5) Now select Root - Drop to a root shell prompt.

Why the messing around? Recovery mode>Root only gives us a file system in read only mode. Cannot change anything. But Recovery mode Failsafex sets the file system in read/write mode. So, go into and then out of failsafex to get a file system in read/write mode when we choose Root shell prompt.

at the root shell prompt you can try those two command I gave earlier. Followed by ```
startx
``` or you can reboot with ```
shutdown -r now
```

Another command to try is

```
dpkg-reconfigure lightdm
```

Some of these commands require sudo but as we are at a root shell prompt we do not need sudo. If this seems like guessing, then you are right but that reconfigure lightdm command should bring up a configuration dialog like the first one you saw. Notice also, that we first need to stop one display manager before starting another one. I am guessing that failure to do that may have caused this.

Oh, by the way, [code]shutdown -h now{/code] shuts down the machine. when run from a terminal it needs sudo.

See how you go. Regards.

Finally got it back to normal.  Because I struggled to get a terminal, I couldn't do any of that.  So what I did was just switched from GUI to console (ctrl-alt-f1) and then typed in what you've suggested Mr.Mechanical [dpkg-reconfigure lightdm] and then rebooted my machine.  Voila!

Again, thank you heaps!

---

### Post by kepz on 2013-05-05
How do I mark this thread as 'SOLVED'?

---

