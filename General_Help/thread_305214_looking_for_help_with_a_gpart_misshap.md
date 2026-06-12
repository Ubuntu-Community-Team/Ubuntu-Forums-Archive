---
title: "looking for help with a gpart misshap"
date: 2006-11-23
forum: General Help
---

### Post by Efaustus9 on 2006-11-23
I recently installed Ubuntu on to a dell computer which has a 40GB HD. When I installed it I accidentally gave ubuntu more hard drive space then I was intending. so following the installation I went back into gpart off of the live CD deleted the linux partition and proceeded to extended the windows partition to an additional 10gb of free space from its previously allocated 1gb. Following this I saved the changes and shutdown. Now the computer will not boot from the harddrive so I figure the MBR is FUBAR. I use Ultimate Boot CD and manually boot the ntfs partition which starts to load windows and detours into disk checker. half way though checking the disk the motherboard beeps a few times and the system shuts down. So now im stuck any suggestions as to how to salvage both the MBR and my windows installation?

---

### Post by insub2 on 2006-11-23
windows might have not liked being resized...i hear that happens sometimes.
you may have to reinstall windows.  you can check (and save to another partition) your files from mounting the partition to a live cd.

but what are you trying to achieve?  do you want to ditch ubuntu and only run Windows?  (you said you deleted you linux partition and expanded windows to fill the freespace.)  if so, reinstalling windows is the easiest (note: i don't know if it is the best) way to get you MBR back.  and if your windows is fried, you may have to do this anyway.

---

### Post by Efaustus9 on 2006-11-23
thanks for the response. I was trying to reallocate the space given to the respective installs so instead of windows 20GB and Ubuntu 20GB I wanted to give windows 30GB and Ubuntu 10GB. I supposed the problem that windows disk checker was having was possibly due to the formating of the now additional space I had reallocated to it. I figured to get windows working again I would open up gpart and restore the original configuration of 20GB/20GB but unfortunately the program froze during this partitioning/reformatting process so I waited about 4hrs with no progress before doing a hard boot. Unfortunately in doing so I think I bricked the Harddrive for now not even UBCD can find it. I am very bummed for I do not have a copy windows xp so if the harddive is lost I need to get a new one and a copy of xp. :(

---

### Post by Ocxic on 2006-11-23
your resized your windows partition to 1 gig, that basically destoryed the windows install, your going to have to reinstall windows(you could try testdisk, a recovery program, but i dunno if it'll work). 
be carful when making changes to partitions, or thing like thins will happen.

---

### Post by ad2snake on 2006-11-25
Ok. I got this DELL Inspiron 6000.... and i put ubuntu on it... knowing zilch about all the other MBR and stuff. Anyways..., now, as you'll might know, dell comes with a partition that reinstates the comp back to factory settings.... apparently that was the original mbr (no wonder the freaking fdisk /mbr and **** didnt work ](*,) ).... anyway now its gone, cos i can no longer find the screen from where i do dell's restore. And my windows needs to be reinstalled...., and obvi i want the original thing. One thing i made sure.., while installing ubuntu.. I didnt touch the dell partition which contains all the thingies.... now i cant access that, my best guess is GRUB. Now I know a ton more about installing linux, but still dont know how to get my original windows install back. Now my dads also got a DEll inspiron 2200... now by mere observation, i can assume that his MBR is the same as mine was...(not sure if models should vary in MBR also - i dont think dell has the patience to do tht too). Anyways, i am guessing my best hope is, to make a copy of dads mbr and somehow rewrite my existing mbr. THe thing is, HOOOOW??? Can i get ANY HELP with this....:confused:

---

### Post by Efaustus9 on 2006-11-26
> **Ocxic said:**
> your resized your windows partition to 1 gig, that basically destoryed the windows install, your going to have to reinstall windows(you could try testdisk, a recovery program, but i dunno if it'll work). 
be carful when making changes to partitions, or thing like thins will happen.

for the record I did not resize the windows partition to 1gb, I extended the 20gb originally given to windows to 30gb. I would like to if at all possible revive the old hardive but that would likely require a flash of the firmware on the hd its self, if you know how to do this please share :). Things could be worse though because fortunately for a black friday sale I was able to pick up a Maxtor 200GB HD for 20 bucks, and although I wasn't able to get my hands on a copy of xp pro I was able to obtain an OEM copy of XP Home. 


ad2snake, if you still have your copy of the reddish xp restore cd that came with your computer you should be fine. just pop in that cd and hold down F12 as the computer boots, it will give you access to the recovery console and re instillation options.

---

### Post by Ocxic on 2006-11-26
there should be an option in your bios to boot from the recovery partition.

---

### Post by insub2 on 2006-11-26
> **Efaustus9 said:**
> Unfortunately in doing so I think I bricked the Harddrive for now not even UBCD can find it.

Aww bummer.  I'm curious what went wrong...?  IF it's the harddrive's fault, you may be able to put in the freezer for awhile and then plug it in real quick and possibly get some of your data back.  i've never done that, but i've heard it works depending on what is the matter.

200GB for $20 is a great deal. it sounds like you are gonna be ok.

---

### Post by ad2snake on 2006-11-26
No mate... the Dell notebooks dont come with a recovery disc anymore. They figured this shitty anti-piracy crap.... where, a portion of your HDD acts as a revocery. On the system boot screen, where it shows DELL..., you press Ctrl + F11, and it takes yuo to a screen where it asks you to confirm whether you want to restore factory settings. THis partition called "dell utilities"..., isnt recognizable in the windows or Linux partition managers... or explorers. You can see it only if you use something like "partition magic".., So anyways, I kinda resized my Drive.., and installed Ubuntu. Then things ran smoothly. But now, the Windows is corrupted.., and i found that GRUB screwed up the master boot record, which allows you to use the Ctrl + F11 option.., instead of that you directly have to choose which OS you wanna boot. Now to be able to access the recovery partition.., i think I need the MBR that came with the system..., now, my dads Dell notebook also has this same mbr.. i was thinking, if i backup my dads MBR, and restore it on mine..., i should get things back to working condition. The problem is, though both the notebooks are dell, the models are different. BUt i think only the contents of the recovery partition will differ, the main MBR should be the same.., even otherwise.., my dads notebook also uses the same key combo to access its dell utility partition.....](*,) ](*,) ](*,) :-#

---

### Post by Efaustus9 on 2006-11-26
> **insub2 said:**
> Aww bummer.  I'm curious what went wrong...?  IF it's the harddrive's fault, you may be able to put in the freezer for awhile and then plug it in real quick and possibly get some of your data back.  i've never done that, but i've heard it works depending on what is the matter.

200GB for $20 is a great deal. it sounds like you are gonna be ok.

thanks, I may try that freezer fix. The hard dive deal was quite fortuitous and although cracked oem copy of xp home is no where near as good as a legit copy of xp pro sp2 things could be worse. Now I have a new 200gb harddrive to install I was wondering which order of installation would be ideal (1 XP Home then Ubuntu 6.06 or (2 Ubuntu 6.06 then XP Home.

ad2snake, sorry to hear that but there are alternatives available that will work as well if not better then that dell recovery partition. You can try out [Ultimate Boot CD]("http://www.ultimatebootcd.com/download.html") or this [Recovery Console]("http://www.geocities.com/xfaustus9/xprc.zip") cleaved from an xp install cd, just download and burn the isos to a couple of bootable cds.

---

### Post by ad2snake on 2006-11-26
*Reffering to the above post:-*ALso I dont quite know how to make a backup of the MBR :(

---

### Post by ad2snake on 2006-11-26
Hey yea... will try that..., thanks.... but what exactly does it do......, also I have an issue with my DVD drive. Sick thing stopped reading discs...now me have no alternative other than to look for a new drive.... or borrow an external USB drive or buy that instead.......

---

### Post by insub2 on 2006-11-27
> **Efaustus9 said:**
> Now I have a new 200gb harddrive to install I was wondering which order of installation would be ideal (1 XP Home then Ubuntu 6.06 or (2 Ubuntu 6.06 then XP Home.

Do windows first.  then when you install ubuntu, grub will set up the dual boot automatically.  if you do ubuntu first, then windows will (most likely) eat it.

---

### Post by Efaustus9 on 2006-12-02
I have installed the new drive and put Windows Xp home on it. I am trying to avoid another mishap. So when using the live CD installer and it asks to allocate some space for a partition is the percent its listing (identified w orange bar)intended for windows, with the remaining space (gray area ahead of bar) intended for the Linux install. I postulate this is the case for it will not let me make the partition less then 3gb. I have a 200gb drive I would like to give ubuntu about 10-15gb of it.

---

