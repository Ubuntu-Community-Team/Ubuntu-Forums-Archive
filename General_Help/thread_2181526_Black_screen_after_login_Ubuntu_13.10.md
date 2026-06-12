---
title: "Black screen after login Ubuntu 13.10"
date: 2013-10-18
forum: General Help
---

### Post by Arne_Reijntjes on 2013-10-18
Hello Ubuntu forums,
I know my way around Linux, so I'm not a complete noob but still, I don't know that much...

So, last monday, I decided to install Windows 7 on my PC and I figured, I'll wait a few days for Ubuntu 13.10 to launch so I can dual-boot it.
I cleanly installed Windows 7 over XP and it worked flawlessly. So naturally, I shrank my volume for 25 GB and installed Ubuntu 13.10.
When I boot my PC the Grub menu shows up, I select Ubuntu and everything works fine...
But then, after I login with my password the screen goes black with only the mouse still on it. It works for a few seconds, then freezes, and finally disappears.
Here am I with my black screen... Nothing to do but restart. 

I think this is a driver problem with my nVidia Graphics card (Specs below). But I was amazed when I found out the live CD works just fine.
So maybe something went wrong with the installation? *NOTE* I didn't install the 3rd party drivers.

Conclusion: I want to fix my black screen but I can't install any additional software from within Ubuntu, because I can't do anything in Ubuntu.
Is there a way to fix this?

Thanks in advance.

Specs:
CPU: AMD Athlon Dual Core 7550 2.5 GHz
RAM: 2 Gb
GPU: nVidia GeForce 6150se nForce 430

EDIT:
I forgot to mention that I used Windows XP and Ubuntu 11.04 installed with WUBI and it worked just fine.

---

### Post by BenTurpin on 2013-10-19
Hello, unlike Arne, I am new to Ubuntu and I upgraded yesterday from 13.04 to 13.10.  All seemed to go well and after rebooting I could work on old documents and after some time I shut down. This afternoon I opened my PC, and booting with Ubuntu (I also have windows 7) things looked well and I entered my password and then the black screen with the mouse.
I tried booting with Advanced booting but whatever I tried, I never got any further. Right now I have no idea what to do. If I install fresh from Windows, will I be able to open the documents that are right now in my computer? They are now hidden when I open Windows. 

I have an Intel Pentium 4 CPU 3.20 GHz Processor
2 GB Ram
and a NVidia GeForce 210

So my question is: can I re-install Ubuntu through Windows and then somehow overriding the existing one?
ton baars

---

### Post by mörgæs on 2013-10-19
Normally we prefer to deal with one question in each thread, but as both of you are using Nvidia we might be able to do it in one go.

First, I am not sure I understand completely. Are these installs dual-boot (Buntu next to Windows) or Wubi (Buntu running in Windows)?

---

### Post by BenTurpin on 2013-10-19
Thanks for this, I installed mine through Windows, and I have seen the word WUBI, so I guess that is what I did. As I mentioned I am rather new and especially some termonology is beyond my current understanding. When I open the computer I get to a black screen with the choice between booting using Window or Ubuntu. I was able to make Ubuntu the default boot.

---

### Post by mörgæs on 2013-10-19
I don't know Wubi as I don't have any Windows installations. Your best option is the [Wubi megatread]("http://ubuntuforums.org/showthread.php?t=1639198").

---

### Post by Mathew_Shires on 2013-10-20
[SIZE=2]this happened to me after upgrading from 13.04, I held down the windows key and everything appeared and works fine, it may not be a permanent fix but its a walkaround.[/SIZE]

---

### Post by howefield on 2013-10-20
Believe Wubi is not supported for 13.10

[http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows](http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows)

---

### Post by hakuna_matata on 2013-10-20
> **howefield said:**
> Believe Wubi is not supported for 13.10
Maybe not supported, but released...

[LIST]
[*][URL="http://releases.ubuntu.com/saucy/wubi.exe"]http://releases.ubuntu.com/saucy/wubi.exe
[/URL] 
[*][http://releases.ubuntu.com/saucy/ubuntu-13.10-desktop-amd64.list](http://releases.ubuntu.com/saucy/ubuntu-13.10-desktop-amd64.list)[URL="http://http://releases.ubuntu.com/saucy/ubuntu-13.10-desktop-amd64.list"]
[/URL] 
[/LIST]

[URL="http://releases.ubuntu.com/saucy/wubi.exe"]
[/URL]

---

### Post by BenTurpin on 2013-10-24
After trying several things I decided to un install and re install and now it boots up normally. I did loose a few photos and documents that I made with the first set up, so in the future I hope that I won't have to do this again, or have a back up system in place. Thanks for suggestions.
ton baars

---

### Post by ||0BL1v10N|| on 2013-10-24
Have the same issue but only for a few seconds. Appears to be affecting other users!

---

### Post by Atcold on 2013-11-03
> **||0BL1v10N|| said:**
> Have the same issue but only for a few seconds. Appears to be affecting other users!
Yeah, here's the same. Windows 7 plus Wubi. Ubuntu 13.04 was running fine, then, after the update to 13.10, I do have a temporal black screen with pointer and then everything gets back to normality.

---

### Post by daboross on 2013-11-30
I am having this same thing, but only first time I log in. if I go into tty1 and `sudo restart lightdm`. Today I noticed when I ran `ps ux | less`, I found that `sleep 60` was one of the processes. I waited till it ended, and when I went back to x, unity had started.

Is there any reason that unity would be running `sleep 60` before starting?

On another note I am kind of hijacking this thread, but I also have a nvidia GeForce (GT 555M) although I also have a optimus.

Also wondering if any of you can find 'sleep' in your processes when it is frozen? Like if you run `ps ux | grep -v grep | grep sleep` do you get any output?

---

### Post by demian2 on 2014-03-01
Bump. I too have this problem in Ubuntu 13.10. No Wubi though, and no nvidia. 
But I do have dual boot (Win8.1.) 
The problem only occurs on one of my 3 accounts, namely the 1st (admin) account. My Guest accound, and a secondary basic account are working fine without issues.
I wonder what to do?

---

