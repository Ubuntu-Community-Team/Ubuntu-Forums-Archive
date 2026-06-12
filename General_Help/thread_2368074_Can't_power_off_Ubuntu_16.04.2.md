---
title: "Can't power off Ubuntu 16.04.2"
date: 2017-08-06
forum: General Help
---

### Post by richard7893 on 2017-08-06
I have issues whenever I attempt to shut down my computer. Whenever I shut it down (using the GUI), the computer takes me off the main screen to the Ubuntu splash screen with the dots that illuminate one by one. This screen will not go away and the only way to shut down the computer is to hold the power button on the laptop. I do not wish to continue doing this because I am afraid of what it will do to my laptop. I have also tried shutting it down using different commands from the terminal, but I run into the same problem. Does anyone know how to fix this? Should I be worried that my laptop may be damaged if I hold the power button down at the splash screen to turn it off? Any help would be appreciated.

---

### Post by dragonfly41 on 2017-08-06
> [COLOR=#000000]Should I be worried that my laptop may be damaged if I hold the power button down at the splash screen to turn it off[/COLOR][COLOR=#000000]
Yes. Forced power down can corrupt your filesystem.
Until you receive further advice on how to figure out *why* you can't shutdown, use this controlled shutdown procedure:-

...

Press and hold down <Alt> key .. then slowly press in sequence (one key at a time) while holding down <Alt>:-

<Print Scrn> followed by ..
R
E
I
S
U
B

=========================

[Later edit]

Here is one thread which might help.
[URL="https://askubuntu.com/questions/762633/ubuntu-16-04-not-shutting-down"]
[/URL][/COLOR][https://askubuntu.com/questions/762633/ubuntu-16-04-not-shutting-down](https://askubuntu.com/questions/762633/ubuntu-16-04-not-shutting-down)

---

### Post by richard7893 on 2017-08-06
OK do I attempt the suggestion you made  <Alt> etc. at the Ubuntu Splash screen?

I tried the link thread you referred to. It did not work for me though

---

### Post by dragonfly41 on 2017-08-06
I would try the key sequence before the splash screen.

And sorry about broken link .. should be https:// .. trying again ..

[https://askubuntu.com/questions/762633/ubuntu-16-04-not-shutting-down](https://askubuntu.com/questions/762633/ubuntu-16-04-not-shutting-down)

---

### Post by richard7893 on 2017-08-06
OK. The link worked but it did not solve the problem I have.

The key sequence will be tough to do before the splash screen comes up. It appears very quickly as soon as I shutdown the computer using the GUI.

---

### Post by richard7893 on 2017-08-06
dragonfly,

I tried the key sequence. I tried it once before the splash screen came up as I powered down the computer. I also tried it once at the splash screen itself. All it did was restart my computer. The splash screen went away and my computer just rebooted, but didnt shut down. Any ideas of what to do next?

---

### Post by dragonfly41 on 2017-08-07
I use from time to time the Alt + PrntScrn,R,E,I,S,U,B key sequence when my desktop is frozen.
I do not use it after starting the menu option Power Off.
Here is a thread explaining it more fully.
[https://www.reddit.com/r/Ubuntu/comments/6qphtj/psa_use_reisub_when_ubuntu_stops_responding/](https://www.reddit.com/r/Ubuntu/comments/6qphtj/psa_use_reisub_when_ubuntu_stops_responding/)

You still have the problem of troubleshooting why you can't power off cleanly. Refer to the last thread which had ideas.   
And also look to the right of the [page]("https://askubuntu.com/questions/762633/ubuntu-16-04-not-shutting-down") to explore a list of several other threads with same theme.

When you next boot up can you try selecting Recovery mode from your GRUB menu?

======================================

[Later edit]

Having read [this linked thread]("https://askubuntu.com/questions/761280/my-system-is-not-shutting-down-after-installing-ubuntu-16-04-lts?rq=1") can you give more information on what laptop you are using?

---

### Post by richard7893 on 2017-08-12
OK I have a Toshiba Satellite A-215. The thread mentions a band-aid to for shutdown but no description. Do you have any band-aids solutions for this?

---

### Post by sonicwind on 2017-08-12
The Alt + Prt Screen R E I S U B is to reboot. To shut down instead, do Alt + Prt Screen R E I S U O

---

### Post by richard7893 on 2017-08-13
sonicwind

it doesnt seem to work

---

### Post by sonicwind on 2017-08-15
If you are still having problems, it just occured to me that you may not have the REISUB/REISUO stuff enabled.

You can easily check by typing this in the terminal:

```

cat /proc/sys/kernel/sysrq

```

If it returns a '1', it is enabled. If it returns a '0', you need to enable it.

You can do a one-time enable by typing this in the terminal:

```

echo "1" > /proc/sys/kernel/sysrq

```

The source for this information is here:  [https://www.howtogeek.com/119127/use-the-magic-sysrq-key-on-linux-to-fix-frozen-x-servers-cleanly-reboot-and-run-other-low-level-commands/](https://www.howtogeek.com/119127/use-the-magic-sysrq-key-on-linux-to-fix-frozen-x-servers-cleanly-reboot-and-run-other-low-level-commands/)

If you want to set it permanently and are comfortable with modifying system files, post #7 in this thread tells you how to do that: [https://ubuntuforums.org/showthread.php?t=2220356](https://ubuntuforums.org/showthread.php?t=2220356)

I realize this doesn't solve your problem of shutting down normally, but I hope it might help you to at least shut down in a safer manner when it happens.

Also, I don't think it will help this situation, but once enabled, holding down Alt while typing Prt Screen and then K will kick you out of your session back to the login screen. That is helpful in some situations.

I hope this helps.

---

### Post by VMC on 2017-08-15
Instead of trying these power-off concoctions, look at your "/var/log" files to see if something else is amiss. Also look into the 'journalctl' for any errors.

---

### Post by Mark_in_Hollywood on 2017-08-16
I had to update my BIOS to be able to have Ubuntu power off automatically.

---

### Post by richard7893 on 2017-08-23
VMC
How do I look for this, and how would I know if something is wrong, how to fix it?

---

### Post by richard7893 on 2017-08-23
MarkinHollywood,

I googled "update BIOS ubuntu" & found this 
[https://help.ubuntu.com/community/BIOSUpdate](https://help.ubuntu.com/community/BIOSUpdate)

[h=1]Toshiba[/h][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR]
[LIST]
[*=left][FONT=inherit]Toshiba has made available a BIOS .exe for certain models (ex. Toshiba Satellite L305D-S5934) that when executed, generates an ISO to burn to disc, and in turn allows one to boot to the disc to update the BIOS. This .exe was successfully run in Ubuntu via [WINE]("https://launchpad.net/~ubuntu-wine/+archive/ppa") to generate this ISO, the ISO burned in Ubuntu, and the BIOS updated successfully

What in the World am I supposed to go once I click on the Wine link?

Any help would be appreciated[/FONT]
[/LIST]

---

