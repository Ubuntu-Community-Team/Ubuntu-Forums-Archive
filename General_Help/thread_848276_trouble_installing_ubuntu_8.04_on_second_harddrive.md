---
title: "trouble installing ubuntu 8.04 on second harddrive"
date: 2008-07-03
forum: General Help
---

### Post by restore on 2008-07-03
i am having trouble installing ubuntu on my second harddrive.

i downloaded ubuntu 8.04 (the latest, from the homepage) and after i was done downloading. i burned it to a disk. unfortunately it didnt boot up. after looking further into why it wouldent boot up. i realized that theres no BOOT.INI file in there. instead...there was wubi?

many people that i have asked in chat rooms say they dont mess with wubi so idk what i should do right now. if anyone could help me please reply to this thread.

o the error i get when i install is "BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (Ash"

bassicly i get what this guy gets

[http://ubuntuforums.org/showthread.php?p=4964737](http://ubuntuforums.org/showthread.php?p=4964737)

---

### Post by avtolle on 2008-07-03
At first blush, sounds like a bad iso or a bad burn. Did you do a md5um check on the iso after downloading and before burning? Did you burn as an image at a slow speed, and then when booting the Live CD did you do a disk check (option 4 from the menu)?

---

### Post by restore on 2008-07-03
bump.

---

### Post by avtolle on 2008-07-03
[https://help.ubuntu.com/community/Installation/](https://help.ubuntu.com/community/Installation/) is something you should look at, too.

BTW, you shouldn't bump until your initial post has been up 24 hrs.

---

### Post by restore on 2008-07-03
sorry, idk what a md5um check is, sorry.

erm. when i tried burining it. if i double clicked the rar file. it wouldent finish it (this is in nero 6) i would have to extract the rar. and select all files + folders.

and i cant boot from the CD. i told you. it doesent have a boot.ini file so its not bootable

---

### Post by avtolle on 2008-07-03
Read this: [http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso) and follow it.

---

### Post by restore on 2008-07-03
alright, and i live in new jersey. which server should i choose for a redownload?

and ty

---

### Post by avtolle on 2008-07-03
Which one do you have selected in your software sources? I'd try the Main server for the U.S. myself. HTH.

---

### Post by restore on 2008-07-03
well the download was NOT corrupted. i just ran that MD5UM hash thing. and now i am reburning the ubuntu.

so ill give details when its done burning!

---

### Post by avtolle on 2008-07-03
OK, once you have it burned as an image, try it again. If you still get the Busy Box shell, there are some other things to explore. If you want, you could (while the new CD is burning) put a list together of your system specs; most importantly, your graphics card, and whether your two HDDs are SATA drives, and if you have a RAID setup; if RAID, is it hardware or software. But that is getting the cart before the horse a bit, let's see if you can boot.

---

### Post by restore on 2008-07-03
ALRIGHT WELL I get where im supposed to get to. the menu. then i clicked f4 to boot with the other video option. because i remember it going out on me when i used to run ubuntu. then it just started goin on and on and on about how io have to go to this link

[http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

idk why. plz reply back.

i am currently trying ubuntu out without changing anything with my computer. 

so ill reply when i get results.

---

### Post by restore on 2008-07-03
ok well it gave me that error again. then my screen started flickering. now i see the cursor. and a black screen behind the cursor.

im running an ati radeon 9550

---

### Post by avtolle on 2008-07-03
From looking at the link in your post, it appears that the system is detecting a Broadcom wireless NIC. Do you have such on your system? If so, you may need to disable it to get booted.

---

### Post by restore on 2008-07-03
i have a wireless card yeah. and wtf. why is this being such a bitch to me? lol.

---

### Post by avtolle on 2008-07-03
Well, you have two things that cause problems; an ATI Radeon card and apparently a Broadcom wireless card. Hang in there, I'm going to take a look around.

---

### Post by restore on 2008-07-03
alright thanks.

and ati has drivers out for my card. i looked like a week ago.

and if i use wubi. and i tell it to install to my D Drive (2nd hd) well for 1. it trys downloading ubuntu? even though i have it on my harddrive. so idk.

---

### Post by avtolle on 2008-07-03
You may well need to add boot options to get going. [https://help.ubuntu.com/community/BootOptions#When%20installing](https://help.ubuntu.com/community/BootOptions#When%20installing) gives a few examples; scroll around the page to read more.

---

### Post by avtolle on 2008-07-03
> **restore said:**
> alright thanks.

and ati has drivers out for my card. i looked like a week ago.

and if i use wubi. and i tell it to install to my D Drive (2nd hd) well for 1. it trys downloading ubuntu? even though i have it on my harddrive. so idk.

Well, using Wubi (if you are using the latest 8.04.1 release) does d/l, as it is looking for the latest "daily build" iso. Otherwise, both wubi.exe and the iso need to be in the same folder so the iso is found, otherwise it will download the iso and ignore the one on the HDD.

EDIT: Reference Wubi and trying to install on the D drive. How is the D: drive formatted? It is my understanding that the drive needs to be in "native" NFTS format for Wubi to install correctly.

---

### Post by restore on 2008-07-03
hmmm i just formatted it to be NTFS.

idk how to put it as native ntfs. could you grab me a tut?

---

### Post by avtolle on 2008-07-03
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) for more help with Wubi.

On formatting, if you formatted it to NFTS (and didn't change formats from FAT 32, e.g.), that should be OK. I know little about Windows, so that's the best I can tell you.

---

### Post by restore on 2008-07-03
alright, hey well i have a live stream where you can hear me and see me. i think that would be more convienent for errors and communication

[http://www.ustream.tv/channel/grizzlytv](http://www.ustream.tv/channel/grizzlytv)

well there it is. if you want to talk over the forums i understand =].

---

### Post by avtolle on 2008-07-03
Thanks for the offer, but I'm at work (and need to get back to finishing some things up) so no can do. I'm not abandoning you, but I'll be away for a while.

---

### Post by restore on 2008-07-03
np, well im going to try wubi again. my d drive is ntfs so so ill try again.

im rebooting right now for wubi, it recognized all the files and crap

so its going to restart.

when i choose to boot from my D drive. it says

NTDLR is missing
press ctrl+alt+del to restart

thaaaats not good.

edit: i pressed F4 when i booted from the CD, and i chose use safe graphics mode. then  i chose the first one. where i dont change anything.

now im getting buffer errors? and squashfs errors. wtf?

edit 2 :::it just went through a big list of errors. then it loaded crap and it said [ok]

now the list of errors is going rapidfast. and its repeating that same 2 errors.


edit3::: wtf did they do to make this **** so confusing?   man its worse then before.

---

### Post by avtolle on 2008-07-03
Just grabbed a moment, and saw what problems you are having now. I'm about out of suggestions other than the following: scrub the D: drive again, then try getting the latest Wubi installer from the wubi site, download it and put it on the D: drive. Then, let it download the latest Ubuntu iso and see if that will install on the D: drive. Best thought I've got right now.

EDIT: As you have Windows on that computer, look at [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows). Back to work <sigh>.

---

