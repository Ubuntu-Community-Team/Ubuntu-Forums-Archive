---
title: "The side keys of the mouse do not work."
date: 2024-05-05
forum: General Help
---

### Post by rarog-17 on 2024-05-05
Hello.
I don’t know if I’m writing in the right topic, but I didn’t find the right one.
Anyway. As the title of the post suggests, there is a problem with the mouse. Namely with Defender Commander GM-511. Bluetooth mouse. It connects correctly, everything works well, except for the side buttons (standard buttons 8 and 9). In xev they are not defined at all. I couldn't find any drivers for Linux. But on an Android home TV set-top box, these buttons work.
Together with Chatbots (Copilot, Gimini, GPT) we did not find a solution. We tried a lot: piper, xinput, keymapper, input remapper. Next, I was advised to create an undev rule, but I don’t understand anything about this at all.
Just in case, I’ll write here the models of Bluetooth adapters: Buro bu-bt40a (CSR8510 chipset); hama D1900380. Suddenly it's up to them.
I hope you can help.
With respect to the community,
Lex.

---

### Post by karyk on 2024-05-05
Mouse controls in Ubuntu are very limited.  I'm hoping they improve in the next version, but I haven't read anything to indicate that's the case.

---

### Post by dragonfly41 on 2024-05-05
I have problems in Ubuntu 22.04 working with Logitech Bluetooth mouse (with side buttons) and keys.  They did work in an earlier version but not today.  They work in Windows. One day I'll find out why. At the moment I'm using wired mouse abd keys.

Here are some notes from my own research including trying remapper.

[https://knowledgebase.frame.work/ubuntu-bluetooth-S1PGxfho](https://knowledgebase.frame.work/ubuntu-bluetooth-S1PGxfho)

[https://ubuntuforums.org/showthread.php?t=2492760](https://ubuntuforums.org/showthread.php?t=2492760)

---

### Post by rarog-17 on 2024-05-05
It's clear. So at the moment there is no solution. It's a pity there is no list that shows all supported devices. And it turns out that under Ubuntu, most purchases are made for luck - it will work/not/look for crutches.

---

### Post by dragonfly41 on 2024-05-05
The finger should point to the manufacturer, not Ubuntu, in my opinion. The question is does the manufacturer support Ubuntu?

---

### Post by #&amp;thj^% on 2024-05-05
> **dragonfly41 said:**
> The finger should point to the manufacturer, not Ubuntu, in my opinion. The question is does the manufacturer support Ubuntu?

+100
you need to get in this habit, when buying newish hardware to be sure if Linux is fully supported.

---

### Post by ajgreeny on 2024-05-05
I did have a Trust mouse many years ago, probably 15yrs or thereabouts with two side buttons which did nothing when I first plugged it in.

However, back then I somehow managed to get them both working as Backwards and Forwards in the file manager and those older versions of web browsers. To do so I had to get the code from using the buttons using **xev** in terminal and then adding those codes to a system file somewhere.  I thought I still gad a copy of the text file I created as an aide-memoire to myself but now I can't find that information.

I will look again to see if I can find more detail but in any case this may give you a clue as to where to search for more details.

---

### Post by rarog-17 on 2024-05-06
> **ajgreeny said:**
> I did have a Trust mouse many years ago, probably 15yrs or thereabouts with two side buttons which did nothing when I first plugged it in.

However, back then I somehow managed to get them both working as Backwards and Forwards in the file manager and those older versions of web browsers. To do so I had to get the code from using the buttons using **xev** in terminal and then adding those codes to a system file somewhere.  I thought I still gad a copy of the text file I created as an aide-memoire to myself but now I can't find that information.

I will look again to see if I can find more detail but in any case this may give you a clue as to where to search for more details.

Yes, I also tried to determine the buttons through xev. But as it is written in the first post “In xev they are not defined at all.”.

---

### Post by rarog-17 on 2024-05-06
> **1fallen said:**
> +100
you need to get in this habit, when buying newish hardware to be sure if Linux is fully supported.

I completely agree that the manufacturer should support Ubuntu. This is in an ideal world, of course. But at the moment, we have what we have. Most manufacturers support Windows, with support for MacOS sometimes added. And everyone else is already adjusting. As an example: this mouse in question officially supports Win and Mac, but also works on Android (and the same thing is different, on the TV set-top box all the buttons work (a10), but on the Google Pixel 6 the side buttons also don’t work ( a14)), and perhaps in some build of Linux the side keys will work. And it’s possible that the manufacturer will write that Linux is supported, but in reality, you’ll need crutches to make it work. Everything is complicated, and there is no single solution.

---

### Post by MAFoElffen on 2024-05-06
Years ago, I had a lot of Razer Keyboards, Mice and GamePads. They did nothing special in Linux, until some people got together and wrote drivers for them under OpenRazer. That is an exception.

Even Microsoft (with Windows) feels that drivers for peripherals are the responsibility of the Vendor. If they want to sell there product, they need to make it work with things. (Not the other way around.)

---

