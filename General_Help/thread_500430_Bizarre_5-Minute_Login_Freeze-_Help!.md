---
title: "Bizarre 5-Minute Login Freeze- Help!"
date: 2007-07-13
forum: General Help
---

### Post by Sewerbird on 2007-07-13
Hello!

Happily installed an Ubuntu partition on my Windows machine three weeks ago and have been slowly learning the ropes. I haven't had much in the way of problems, and have been particularly satisfied with Ubuntu. 

My problem began this morning. Every time I log in, everything works just fine: Firefox, music player, games, OpenOffice, internet. But only for five or so minutes, at which point the entire system freezes: keyboard, mouse, menus, everything. 

I don't know if this is related to my problem, but this morning, I was researching some "Ctrl+Alt+Delete"-like commands under linux to deal with a few of my Windows-under-wine programs locking up. I accidentally  locked up my computer with one of these commands (I think I did Ctrl+Alt+Esc on the desktop). No big deal, I just rebooted my computer. It was after this boot-up that my problem began.

It doesn't feel like a hardware problem, but perhaps a weird configuration problem or a memory leak somewhere. The problem *always* occurs: both on the normal setup and recovery setup. I'm running Feisty Fawn, and the kernel number ends in ".16", and am using a GeForce FX 5200 video card on a Dell Dimension4600 Desktop. Will provide any info that could help solve this problem, but I have no idea what info *would* be helpful. Totally out of ideas.

On my Windows partition, missing my new home of Ubuntu,
Sewerbird

---

### Post by Stephen Howard on 2007-07-14
when it freezes, can you press ctrl-alt-f1 to bring up a console and log in?

---

### Post by Sewerbird on 2007-07-14
Unfortunately, no. I went back to try it: my mouse was free to move around, but no input from keyboard or mouse buttons.

---

### Post by Stephen Howard on 2007-07-14
Hmm, maybe there's some clue in the logs.  have a look at /var/log/dmesg, kernel, syslog etc.

Does the same thing happen if you are in a console rather than X session?  The way to check might be to boot as you are now, but then bring up a console, then wait to see if it happens.  If it keeps working then we're looking at an X problem.

---

### Post by Sewerbird on 2007-07-14
Went through the syslog and kern.log files, but didn't see anything particularly strange at the end of each 5 minute section. I did press Ctrl+Alt+F1 to bring up a console, and the following message showed upon freezing:

"[307.174863] BUG: soft lockup detected on CPU#0"

I could have told you that! :roll:

But yeah, attached is the excerpt from my syslog from that boot. Nothing seems particularly astray :(

Thanks for helping!

---

### Post by milton1 on 2007-07-14
I know you said it doesn't feel like a hardware problem, but I once had these very same symptoms, and it turned out that my system was overheating.

---

### Post by Sewerbird on 2007-07-14
I don't know if there is a formal way to 'check' overheating, so I ran Ubuntu, had the same 5-minute problem, shutdown, and felt the side of my cpu and components in my case. Didn't burn any fingers: fans are running and the silicon is only slightly warm, well within bounds of normality. Room temperature is room temperature :)

---

### Post by Stephen Howard on 2007-07-14
Hmm, 

Do you have a wireless card?

How many processors?

Do you still get the problem if you select the recovery mode from grub?

---

### Post by Stephen Howard on 2007-07-14
And just to clarify, did you get the softlock error when using Ctrl-Alt-F1 before or after the apparent crash?  If you try to bring up a console at the earliest moment after booting, does it work then?

---

### Post by Sewerbird on 2007-07-15
I have a Linksys Wireless-G PCI Adapter (Model WMP54G) and one P4 2.40 GHZ processor. The lockup occurs under recovery modes and from Ctrl+Alt+F_ consoles brought up. The soft lock error seems to arrive independently of anything I do in one: I've even left it at the "tty2" login prompt and still had the error text appear at the 'appropriate' time. Could there be a log somewhere which recorded what software locked up?

Thanks for aiding me!

---

### Post by Sewerbird on 2007-07-16
Bumpage: would really like to get this fixed, or I'll have to consider dumping Ubuntu

---

### Post by Stephen Howard on 2007-07-16
It'll be a driver bug somewhere.

can you remove the wireless card and try again?

---

### Post by Sewerbird on 2007-07-16
Heya!

Took out my wireless card then logged into Ubuntu. The desktop ran for 15 minutes just fine, admittedly without internet, so it seems the freeze is connected to the wireless card! I suppose it is in line with the last thing in syslog being a DCHP check. 

I don't quite know what the problem is with the card though, and I hope it can be fixed via software: I'd hate to have to replace it. Any clues about how to proceed?

---

### Post by Stephen Howard on 2007-07-16
Excellent, now we're getting somewhere...

Do you use ndiswrapper?

---------------

Reinstall the card and post the output of:

```
lsmod
```

Also, if you can spot the one in the resultant list that looks like the driver, then post the output from the following command:

```
modinfo [name of driver]
```

-----------------

Also, run the following and attach the file:

less daemon.log | grep NetworkManager   > [outputfilenamegoeshere]

-----------------

An experiment to try while waiting a response:  with the card installed, wait until you think that a freeze is close, then type:

```
sudo /etc/init.d/networking restart
```

Does that stop the freeze from happening?  Alternatively, does it cause a freeze?

Also, does the card have a reset button or something similar sticking out the back?  If so, press it before you expect a freeze and see what happens.

---

### Post by Sewerbird on 2007-07-16
Allo!

Well, there has been a very positive result out of this, although I don't know what the problem was. I booted into linux, and quickly accessed 'lsmod' and saved it to file. I looked up ndiswrapper and learned that I didn't have it installed, so I did so. I also did the /networking restart command at the terminal, and it worked in what I'd expect is a normal way: DHCP discoveries and such.

The result is my wonderful Ubuntu being up and running again! Although I am very happy, I do wonder if the problem is solved or just 'patched' for the moment. Did ndiswrapper fix the problem? Did my remove-reattaching of the wireless card trigger a Driver update or similar 'fix' process? Did the /networking restart command clear out bad info in my wireless configuration? I don't know, but something went right: I've been online (in both senses of the word) for a good hour now, with no sign of degeneration.

Thanks Stephan: I doubt this could have happened without your patient and useful help! It is *truly* appreciated =D>

Now just to know what was going on :confused:

---

### Post by Stephen Howard on 2007-07-16
By installing ndiswrapper you essentially changed drivers for the card - lucky there was a choice!

---

