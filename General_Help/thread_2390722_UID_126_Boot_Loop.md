---
title: "UID 126 Boot Loop"
date: 2018-05-01
forum: General Help
---

### Post by daylediamond on 2018-05-01
[LEFT][COLOR=#333333][FONT=&amp]Hi everybody, first time poster here.

I've got a boot loop on my work computer while upgrading from 17.10 to 18.04.[/FONT][/COLOR][COLOR=#333333][FONT=&amp]It's been in a boot loop ever since I rebooted after I updated/upgraded/dist-upgraded . What's odd is that going back one version via the advanced startup option isn't helping, it's giving me the same error message now in both versions of the OS. [/FONT][/COLOR][COLOR=#333333][FONT=&amp]It's a flashing screen, about how it's starting and stopping the user manager for UID 126.[/FONT][/COLOR][COLOR=#333333][FONT=&amp]I've had the problem once before, logged into an archived version of the OS and removed Nvidia drivers. That seemed to help, but I'm pretty sure this isn't happening to all Nvidia users, so I don't know if it was correlation or causation.[/FONT][/COLOR][COLOR=#333333][FONT=&amp]Hit a brick wall trying to go into repair. It's happy to repair files, but it can't contact the network.I've got an Asus PCE AC55BT, a PCI-e wireless card, which connects automatically once I'm logged in, but networking is disabled until then.[/FONT][/COLOR][COLOR=#333333][FONT=&amp]Manually turning on networking in the command prompt or drop down repair menu gets even weirder results : once I try, the prompt will just print out whatever I've typed with no reaction. From commands to gibberish, it just moves the cursor down a line.[/FONT][/COLOR][COLOR=#333333][FONT=&amp]I'm the only tech support at the office and don't have formal training. &#128530;[/FONT][/COLOR][COLOR=#333333][FONT=&amp]Hopefully all this information was helpful. Thanks in advance! [/FONT][/COLOR][/LEFT]

---

### Post by Claus7 on 2018-05-03
Hello,

there are many cases why you have such a boot loop. Some ideas:

1) even though is not exactly a loop changing display manager might solve the issue:
[https://ubuntuforums.org/showthread.php?t=2390052&p=13760162#post13760162](https://ubuntuforums.org/showthread.php?t=2390052&p=13760162#post13760162)

2) users who are cinnamon ones facing the same problem as yours (they had  to use purge):
[https://ubuntuforums.org/showthread.php?t=2390186&p=13760157#post13760157](https://ubuntuforums.org/showthread.php?t=2390186&p=13760157#post13760157)

3) flashback case where there was a loop as in your case (purge helped once again even a different one)
[https://ubuntuforums.org/showthread.php?t=2384556&page=2&p=13743098#post13743098](https://ubuntuforums.org/showthread.php?t=2384556&page=2&p=13743098#post13743098)

All solutions mentioned here they had to do with upgrading to 18.04 as in your case.

Ah! And welcome to the forums!

Regards!

---

