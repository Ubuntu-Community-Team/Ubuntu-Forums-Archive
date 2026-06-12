---
title: "cpu freezes only in ubuntu / Config BIOS"
date: 2024-01-19
forum: General Help
---

### Post by tfr8 on 2024-01-19
good afternoon. I have a problem with my Ubuntu. When I'm not using the PC, after a few hours, it freezes. When I use the same hardware with Windows on another disk, I don't have any problems. I already tried Ubuntu on another disk and I have the same problem. Hardware: Asus Maximus VIII Motherboard, Intel I5-6500. I tried changing the processor for a weaker one, and I haven't had any problems. conclusion: as the i5-6500 processor works without problems in Windows, I think there is some configuration in the motherboard's bios that makes this processor not work well with ubuntu. The problem only happens when I'm not using the PC and its consumption is low. After a few hours it freezes. Can anyone help me? Ths

---

### Post by dragonfly41 on 2024-01-19
I am afraid that you will have to hone your detective skills.

[https://www.goodreads.com/quotes/1196-when-you-have-eliminated-all-which-is-impossible-then-whatever](https://www.goodreads.com/quotes/1196-when-you-have-eliminated-all-which-is-impossible-then-whatever)
  
I often hit freezes and other issues on Ubuntu 20.04 which work in Windows or other Ubuntu.

Try leaving a LiveUSB for a few hours in "Try Ubuntu" mode to see if it freezes likewise.  

Try closing applications and running just brower with extensions off. 

The list goes on and on.  If you are trying to find cause with lots of apps running it will be difficult to see the wood from the trees.  Currently I have a mouse issue which freezes and I resume work by hitting Ctrl + Alt + F1 to login again to session. I limp along until next freeze. Meanwhile migrating to fresh Ubuntu .. over time.

---

### Post by Princey on 2024-01-19
Have you tried looking to see if the issue is with your power saving mode? From what you've said, it looks like that only happens when the system is idle. What are your settings like for when the system is idle? (sleep, monitor time out, power saving mode)

---

### Post by oldfred on 2024-01-19
Not an issue with my CPU.
[FONT=monospace][COLOR=#000000]Intel(R) Core(TM) i5-6500 CPU @ 3.20GHz

But I only typically open a few tabs in Firefox or have a few apps running at once.

Anything in logs?
[/COLOR][/FONT]grep -Ei 'warn|error' /var/log/*log |less
I get as much as a page, but some are just commands with error in description and others are not anything critical or just warnings.[FONT=monospace][COLOR=#000000]
[/COLOR]



[/FONT]

---

### Post by tfr8 on 2024-01-25
I already found out what it was: WIFI network board: Asus PCE-N15. Since I took it off I have never had any problems again. I tried turning the pole back on, and the problem appeared again. When I tried another CPU, I removed the WiFi board because I wasn't using it, and I stopped having problems. I thought it was the processor. but then it wasn't making sense, without having changed anything it was good&#8230;. Then I remembered that I removed the wifi board

---

### Post by MAFoElffen on 2024-01-25
What you should do now, is to find out which module that board uses when it is there, then Report it to Launchpad, so that they can fix that module. The easiest way t do that is to put the board back in, and see what it uses.

Then if you blacklist that module from loading, see if it goes away. That way it confirms there is a problem with that module, and not just an interrupt problem with the board.

That is what I would do. Help to be part of the solution to get it working correctly. That is just the right thing to do.

---

