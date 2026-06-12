---
title: "Wubi uninstall not quite clean"
date: 2007-09-15
forum: General Help
---

### Post by Scotthchoc on 2007-09-15
So I just uninstalled Wubi from the computer, everything (/wubi folder) seems to be gone except for an entry left in the Add/Remove Programs menu.  Clicking 'Remove' again goes through the uninstall process again, except there's nothing to left to uninstall.  Could be a bug?  Would appreciate any help on removing the entry altogether!

[[IMG]http://img214.imageshack.us/img214/4782/wubiuninstzv3.th.png[/IMG]](http://img214.imageshack.us/my.php?image=wubiuninstzv3.png)

---

### Post by rivalarrival on 2007-09-15
It didn't remove itself from your registry - run regedit, find it by searching for wubi and CAREFULLY remove it

If you don't know what you're doing in the Windoze registry, don't mess with it.

---

### Post by itmozart on 2007-09-16
This is a bug.
The same thing happens to me.

System: Windows XP

---

### Post by Scotthchoc on 2007-09-16
Thx, rivalarrival for the advice!  I dreaded it to be a registry job, decided not to mess with it afterall...  Just gonna wait just a bit more till I reformat this sukah and install Ubuntu completely!  Can't wait..!

---

### Post by ago on 2007-09-17
Hmm, it should normally remove the registry key unless the uninstaller was interrpupted. We did not have issues with that in the past (unless you used an old version).

Anyway to undo things manually it is sufficient to remove the key: 

HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi

If others have the same issue, I'd like to hear from you (make sure you start with a clean sheet, install the latest version, then try to uninstall).

---

### Post by 71CH on 2007-09-19
> **ago said:**
> Hmm, it should normally remove the registry key unless the uninstaller was interrpupted. We did not have issues with that in the past (unless you used an old version).

Anyway to undo things manually it is sufficient to remove the key: 

HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi

If others have the same issue, I'd like to hear from you (make sure you start with a clean sheet, install the latest version, then try to uninstall).

I don't mean to resurrect such an old thread but I wanted to ask a question before using wubi.  How easy is it to uninstall wubi and get rid of ubuntu if I decide I don't need the dual boot?  Thanks.

---

### Post by ago on 2007-09-20
> **71CH said:**
> I don't mean to resurrect such an old thread but I wanted to ask a question before using wubi.  How easy is it to uninstall wubi and get rid of ubuntu if I decide I don't need the dual boot?  Thanks.

You should be able to simply uninstall as any other application, the above is not confirmed as a bug and probably due to some peculiar setup which should be irrelevant for the other users.

---

### Post by IssyBookWorm2 on 2007-09-24
Hi.

I've got that problem too. I uninstalled Wubi this morning, for one reason or another, and it uninstalled okay (apparently) but it is still listed in my Add/Remove Programs ! Any help, here ?

---

### Post by ago on 2007-09-24
Look under HKLM\Software\Microsoft\Windows\CurrentVersion\Uni nstall\ to see if there is any wubi related key (you can delete it). Also look if there are grldr/wubildr files in your partitions

---

### Post by EtniesBMX on 2008-03-18
I am also having the same uninstall problem. I don't think kubuntu finished downloading through the wubi installer because kubuntu didnt work when I chose it on the boot menu. 

Anyway, I'm having the same problem with the wubi entry on add/remove programs.

 I'm also running windows XP on a single HD with 2 NTFS partitions.

edit: in case anyone cares, the advice given by AGO worked well: remove wubi key at HKeyLocalMachine\Software\Microsoft\Windows\CurrentVersion\Uninstall\

(to get here go to start>run>and type "regedit")

---

### Post by ago on 2008-03-18
That should have been fixed in 8.04. If you experience that in 8.04 please let me know.

---

### Post by TheTrlak on 2008-07-02
Hi seems my 64 bit (vista) has driver issues so i wanted to start fresh and install everything properly. Well.... seems even after uninstalling from the programs manager it remains on dual boot and i can still boot to it in its last satte so its technically not gone? HAve any way for a complete true removal. It also was installed a second time so both appear on my menu.

---

### Post by AJCF on 2008-07-03
Yeah, I also had to use EasyBCD in order to remove Ubuntu completely from my laptop, I'm using Vista Home Premium 32-bit by the way :)

---

### Post by ago on 2008-07-03
I have vista and removal works for me. I will investigate further. Anyway here is the relevant link: [https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d](https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d)

---

### Post by TheTrlak on 2008-07-03
Thank you very much. Actually I eventually managed to get it off my system. It was very weird that after an install I could still boot to it until I removed it from my boot menu with the newest EasyBCD. Although my pc says I am using more hard drive space but que sera sera.

Now I have a nice working clean install going. The only issue remaining is getting the proper video drivers to work for my gf 9500m gs on my asus g1 64 -bit vista machine >.>;;

---

### Post by kcgirl on 2009-05-10
*deleted*

---

### Post by Nchalada on 2009-08-09
i tried Wubi on XP , didn't continue with it as it didn't / couldn't mount one of my hdds, unstalled it, and it left the startup entry in the main boot menu.

Edited the boot menu manually, seems to have worked..

---

### Post by triplesick on 2009-08-22
i had the same issue as the above user, but after uninstalling wubi i still can't hibernate.  anyone else?

---

### Post by Stoneface on 2009-08-27
I installed and uninstalled Wubi (Ubuntu 9.0.4) today on windows XP. I thought it was more like a Virtual PC Ubuntu I could run in Windows. But it just created Ubuntu as an alternative OS using Windows boot menu. At start-up I got my GRUB menu with Ubuntu options - Ubuntu was already installed as second OS by me :-) - and Windows XP. When I chose Windows XP I got the Windows boot menu with Windows XP and Ubuntu as a choice.. Anyway my mistake. I uninstalled Wubi using the .exe in C:/Ubuntu. It worked. But I still see Wubi as an option in the boot.ini:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

```
 Not in the add/remove program list though so no problem there. Do I need to edit boot.ini or will a reboot do? If I need to edit the boot.ini please tell me how..

---

### Post by Stoneface on 2009-08-27
If I am not mistaken I just need to remove this line:

```

C:\wubildr.mbr = "Ubuntu"

```

See also: [http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

But when I just remove the line and try to save it Windows says Nooo. I am admin...

---

### Post by Stoneface on 2009-08-27
Had to uncheck "Read only" by right clicking the file and selecting properties > check box Read only. Then I adjusted the file and made it rad only again.

boot.ini now has:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

---

### Post by SIStem_shock on 2009-09-09
Looks like this is still not fixed, as I installed Wubi 9.04 (xubuntu) about 2 weeks ago on a brand new netbook running Xp and had the same problem when I tried to uninstall it earlier today. It did remove it from add/remove programs, but it still showed up as a choice in the boot menu each time I booted. I had to manually remove it.

---

### Post by wilee-nilee on 2009-09-13
So you can delete all of the wubi files by searching in c in xp then follow the edit bootloader information in these 2 links. The 2nd link shows you what the bootloader looks like with a single OS or multi-booting.

Edit: I noticed in deleting wubi in c that temp files still had info, but the boot was set back to just windows. The temp files can be deleted, except for WebClient/Publisher Temporary Files. This function can be turned off though if needed, be very careful deleting anything though make sure you are confident in what your doing.

[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

[http://vlaurie.com/computers2/Articles/bootini.htm](http://vlaurie.com/computers2/Articles/bootini.htm)

---

### Post by ColJep on 2009-11-03
I would like to add my experience with Wubi. I installed 9.04 on my XP machine as an experiment before installing it for a friend on his machine. He is Spanish so I wanted to be clear of all the steps.

I used the live 9.04 to do a bit of partitioning with no problems then installed 9.04 with Wubi. Again no problems. I even changed the language to Spanish.

I then uninstalled 9.04 from Add Remove programs and that was OK except that on the next boot I was given the choice of Windows XP Professional or Ubuntu. During my attempts to resolve this I tried the live version of 9.10. This installed but the chosen screen resolution brought up an "out of range" message on my monitor so I could go no further.

This screen resolution problem happens with annoying regularity with 9.10. I have reported this on another thread. I have also had a successful install on another computer (with Nvidia graphics) that had no trouble with 9.04 suddenly revert to 640 x 480!

I used the XP recovery console to restore the MBR then edited boot.ini to remove the Ubuntu option on booting.

This does not seem to be an isolated case so maybe wubi needs some more work. 9.10 certainly has a few wrinkles in the video department.

---

