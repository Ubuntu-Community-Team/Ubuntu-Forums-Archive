---
title: "Updated to Ubuntu 14.04 - now my system is broken - please help me!"
date: 2016-05-09
forum: General Help
---

### Post by mr.green2 on 2016-05-09
Hi everyone!

At first let me say: I am not very tech-savvy and English isn't my mother tongue - so this could become quite a challenge :/

Today I updated my Asus X54C to Ubuntu 14.04 in order to be able to install "Foxit Reader" (need a tool to highlight text in pdfs).
I updated the Laptop through the automatic-updating-application. After ~2 hours the process seemed to have finished and I was informed to restart the laptop. Then the problems started:

While booting, I saw the following message (translated): "The drive for /dev/mapper/cryptswap1 is not yet ready or does not exist" (see attachment)

If I dont do anything, I get to the normal set-up where I can log in via password - which works just fine.

But then the system more or less breaks down, reports system errors and the whole display is blurred (see attachment). Due to the blurring I can't tell you what the system error-messages say.

It might be significant: I have 2 "partitions"(?) -> but I only use the one called "Ubuntu 11.10" -> that's the one I updated (see attachment)

What did I do wrong and how can I solve this? 

Thanks for your help!

Ps: I use Ubuntu because a former friend recommended it to me and promised to help me out if I have problems. Well, he ditched me ice cold and vanished off the face of the earth :/

---

### Post by mr.green2 on 2016-05-09
by the way: before I updated, I made a backup of all my files. So if it would be the easiest way to just download ubuntu to a USB-stick and completely install everything new (and erase all the faulty ubuntu-versions) - i would very much appreciate a beginner friendly link to the instructions for that! I just want to highlight text in pdf files and get my work done ://

---

### Post by grahammechanical on 2016-05-09
You have me confused.

If the Grub boot menu is showing an option to load Ubuntu (14.04) and an option to load Ubuntu 11.10 then you have 2 installations on that machine. That of 14.04 & 11.10. If we have only one installation on the machine and we use Update Manager to upgrade it to the next version, then the original version is replaced by the new version and we still have only one installation of Ubuntu on the machine.

Your post gives the impression that you updated 11.10 to 14.04 when it seems that you did a new install of 14.04. Or you had Ubuntu 12.04 (as well as 11.10) on that machine & upgraded it to 14.04. 

If you are willing to loose all data on that hard disk, then simply run the Ubuntu (14.04 or 16.04) live session, select Install Ubuntu and then choose the option to Erase disk & install Ubuntu and the installer will take care of everything.

See image #3 Allocate drive space

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

As you have existing installations on that machine you may be offered the Install Alongside option. That is if the partitioning layout allows it. 

Regards.

---

### Post by mr.green2 on 2016-05-10
Hi!

Thank you for your reply!
Before the last update, I already had 2 installations -> one listed as "ubuntu" in the starting menu, and one "11.10". The 11.10 is the one I always use and the one I tried to update. The screenshot was made after the update - but for whatever reason, it did not change the description of "11.10". 

I will try to erase everything and have a fresh start! Again, thanks for your help - wish me luck :)
[COLOR=#000000]**_grahammechanical_**[/COLOR][COLOR=#000000]**grahammechanical**[/COLOR][COLOR=#000000]**grahammechanical**[/COLOR][COLOR=#000000]**grahammechanical**[/COLOR][COLOR=#000000]**grahammechanical**[/COLOR][COLOR=#000000]**grahammechanical**[/COLOR]

---

