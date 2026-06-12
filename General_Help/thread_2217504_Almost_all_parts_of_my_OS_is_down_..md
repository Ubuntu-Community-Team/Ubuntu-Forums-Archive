---
title: "Almost all parts of my OS is down ."
date: 2014-04-17
forum: General Help
---

### Post by Ardeshir on 2014-04-17
HI Everyone !
I had a great experience with Ubuntu until I installed Tor browser (vidalia) .
I'm not sure if vidalia is causing the problem , but the last thing I did was installing that .

1 - After a restart I noticed my network is down , at start up an error appears :
> **"Failed to apply network settings"**
> org.freedesktop.DBus.Error.Spawn.PremissionsInvalid: The permission of the setuid helper is not correct

You might not be able to connect to the Bluetooth network via this machine
So there is no network and I can't connect to internet .

2 - My fonts are not that beautiful bold theme , they are just normal texts .

3 - My terminal is not working properly . I cant type "su" and "sudo" commands . (Plus some other commands which I can't remember right now) . When I type run a command which is a "sudo" command , this error appears :
> sudo: effective udi is not 0, is sudo installed setuid root?
When I type "su" it prompts for password and when I enter my password , this error appears :
> setgid: Operation not premitted

4 - I don't have "Shutdown" and "Restart" anymore . Whether I choose to log out , restart or shutdown , I will see the log out menu which only consists of "Log Out" and "Lock" .
When I choose to log out , a DOS-LIKE or TERMINAL-LIKE screen appears with some texts on it , then it goes blank and a window appears :
> **The system is running in low-graphics mode**
> Your screen, graphics card and input device settings could not be detected correctly . You will need configure these yourself!
When I slect "OK" it goes to another page and these options are there to select :
> 1 - run in low graphics mode just for one session
2 - reconfigure graphics
3 - Troubleshoot the error
4 - Exit to console login

5 - I can't browse my USB Flash Drive and my CDs and DVDs . When I insert them no icon appears in the left . (Unity bar) (But I think Ubuntu can still read them , because I inserted a movie DVD and VLC media player could play it)

Thank you !

---

### Post by Ardeshir on 2014-04-20
HI !
I still need the answer .

Isn't there something like restore point ?
Or is there a way to copy my data into my USB flash disk and reinstall OS ?

Thnaks !

---

### Post by sdowney717 on 2014-04-20
You can do several things.
Boot a live usb, copy your data files you want, reinstall OS.

This install keep /home and / separate distinct partitions.
the '/' will be for system files
the /home will be for user files.
This way reinstall will be easy on you next time since you tell it to use the original /home for user and it is already there you never loose any data.
20gb is plenty space for '/' os files.

You can also boot to recovery prompt and use terminal commands to undo the tor install and reinstall system components.

You can also boot the liveusb and then chroot into your hard drive install which is like booting off the hard drive the original install.

---

