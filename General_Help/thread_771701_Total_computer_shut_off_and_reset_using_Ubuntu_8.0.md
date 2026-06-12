---
title: "Total computer shut off and reset using Ubuntu 8.04"
date: 2008-04-27
forum: General Help
---

### Post by davidchat1971 on 2008-04-27
Hello all,

I just wanted to introduce myself as I am new here and I'd like to take the time to say hello and let everyone know that I have quite the expertise using various Linux environments, especially Ubuntu.   I will help out whenever time permits for me to use this forum.

With that said, I am facing a problem using the latest release 8.04...

After installing, I was going through the various steps to install and add package software (Synaptic package installer). I updated my nVidia drivers, installed Pan Newsreader and installed Wine.  After installing Wine, I was running the Wine Configuration tool and just out of the blue the computer shuts down.  No restart, just a complete shut down.  After that, I rebooted, it took a while for the BIOS to kick in but I was able to get back up and running, started up Ubuntu and after another 2 minutes it shut down again.

Here is my computer configuration...

Pentium 4 2.8GHz, overclocked to 2.9
nVidia Geforce FX 5200 graphics card
nVidia Geforce MX 4000 graphics card (will not run dual monitor display)
160G EIDE Seagate Barracuda hard drive
500G SATA WD hard drive (36G linux partition set on this drive)
Sony DVD RW Drive
M-Audio Delta 1010LT Audio card
Floppy drive
3G Ram on dual channel ASUS motherboard
ASUS P4P800 M/board

This system still runs on Windows XP.  I've had no crashing problems using XP just with Ubuntu so that would tell me that that's not necessarily a hardware issue.  My GUESS is that it might have something to do with either the way I have the audio configured, or a discrepancy with the audio drivers or the way the video drivers are configured.  I know I had an issue with Ubuntu 7 using video drivers in conjunction with my nVidia card.  But that's just a guess.

Can anyone point me in the right direction as to what steps to take to prevent this from happening or maybe tell me if you've had the same issue.  My basic premise for using Ubuntu is to have a clean operating system providing basic security measures and I also want to access Newsgroups.

Other than this particular issue, I must say that this is by far the best Linux operating system so far!  Keep up the good work and keep it FREE!

Thank you in advance for any and all help.

Regards,
davidchat1971

---

### Post by ryanhaigh on 2008-04-28
You should probably run memtest from the install cd or grub menu to check for ram defects. Because of the way Linux uses memory rather than letting it sit there doing nothing you will notice this in ubuntu before you do in xp. My brother had this issue and it would only show up in xp when extracting a big file or trying to access a big cab file.

---

### Post by davidchat1971 on 2008-04-28
How long does it usually take for Memtest to run? Will this solve the problem once it has run or will I need to seek further remedy?

Thank you.

davidchat1971

---

### Post by davidchat1971 on 2008-04-28
So while I was running Memtest the same shut down happened!  Should I be taking some sort of hardware precautions, (i.e. keeping terminals clean, dust busting the internals, cleaning the case, etc.)?

---

### Post by Islington on 2008-04-28
anyway he can do the memtest in XP?

---

### Post by ryanhaigh on 2008-04-28
Memtest tests for bad memory, if you have bad memory you should recieve errors during the test I ussually run it for an hour but others have suggested longer. I have never had it shutdown on me though. Did you see any errors prior to the shutdown? Do you get power surges in the area? Does your system appear to be running to hot?

> anyway he can do the memtest in XP?
I don't know of any application but that doesn't mean there isn't one. When my brother had the issue the sytem would continue to operate but just throw weird errors and randomly bluescreen.

---

### Post by bingoUV on 2008-04-28
when you say it shut down, what exactly do you mean. Do you mean a proper, methodical shut down i.e. shutting down services, unmounting volumes etc. Do these messages (shuttiing down stuff) appear on the screen?

Or does it just die suddenly?

---

### Post by davidchat1971 on 2008-04-28
It just dies suddenly... no warning, no proper methods, just as if I'm pressing the power button and everything powers down!

---

### Post by Islington on 2008-04-28
try running the memtest from live cd? is it even on live cd?

---

### Post by rbmorse on 2008-04-28
You need to make the live memtest cd from the iso file you can download from [www.memtest86.com](www.memtest86.com) (chose the "free download" link on the left side of the page. You can, and should, send money later). 

This may be problematic for you since your machine keeps shutting down...perhaps try the download and burn from the Windows installation.

---

### Post by ryanhaigh on 2008-04-28
It was definately on the install cds for the older releases, I don't have a hardy install disk so I don't know if it on that.

---

### Post by davidchat1971 on 2008-04-29
I figured it out!  I set up a swap disk!  I didn't do that initially!  After letting the system sit for an hour, I came back and everything was still running so I'm figuring I'm good to go (knock on wood)...

Thank you for the help people!

davidchat1971

---

