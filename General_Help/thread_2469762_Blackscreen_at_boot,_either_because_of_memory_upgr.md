---
title: "Blackscreen at boot, either because of memory upgrade OR full disk ?"
date: 2021-12-08
forum: General Help
---

### Post by frederic-c on 2021-12-08
Hi everyone, I've been having trouble with booting on Ubuntu ever since I upgraded my memory ram stick, for roughly a month.

Machine : ASUS K501UB
CPU : Intel 17-6500U, dual core
GPU Nvidia GeFroce 940M
OSs : dual boot Win10/Ubuntu20.04
Memory : migrated from 4Gb+4Gb   to 4Gb+8Gb
BIOS : UEFI


I have been **booting on Windows without any problem so far**, the memory working well for what it looks. However I am **having black screen with blinking underscore right after the GRUB screen** ever since when trying to boot on Ubuntu.

My guesses :
As I digged on forums, I suspected something had to do with the graphic drivers or memory compatibility.
To be noted, a disk occupancy might be responsible of the bug as far as I understand it. Indeed, the disk partition was quite full the days around the memory upgrade. The fact that the black screen happened right after the ram stick change could be a coincidence. Does it make sense to anybody ?

--DEBUG ATTEMPTS--

***RECOVERY BOOT**[INDENT]Booting on recovery, I receive the following message at the end of the process:

[IMG]https://ubuntuforums.org/images/attach/png.gif[/IMG] Attach1.PNG (488.4 KB)
[/INDENT]
 
***MEMTESTER**[INDENT]On a Deepin live usb, I ran memtest as followed:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install memtester
sudo memtester 1024 5
```

[IMG]https://ubuntuforums.org/images/attach/jpg.gif[/IMG] Attach2.jpg (50.7 KB)
It returned screens apparently stating evertyhing was great. Is it right ?  (sorry for the poor quality of photos)
[/INDENT]
 
***RECOVERY TOOLS**[INDENT]On the recovery screen, the analyzer tools give the following messages: (those screens are in French in my machine. I hope it is understandable still)

-disk space-
[IMG]https://ubuntuforums.org/images/attach/png.gif[/IMG] Attach3.PNG (503.9 KB)


-memory-
[IMG]https://ubuntuforums.org/images/attach/jpg.gif[/IMG] Attach4.jpg (31.3 KB)
[/INDENT]
 [B]
*NVIDIA DRIVERS[/B][INDENT]On a forum, I got the hint to reinstall nvidia drivers.
On recovery command line, I entered :

```
sudo apt-get update && sudo apt-get upgrade
sudo apt install nvidia-drivers-390
```

It returned the following messages :

[IMG]https://ubuntuforums.org/images/attach/jpg.gif[/IMG] Attach5.jpg (117.5 KB)

[/INDENT]
[INDENT]As a result, I now** no longer boot on a blinking underscore, but a pitch black screen.**
[/INDENT]
 



UPDATE:
Following the last struggle, I performed on recovery CLI a dist upgrade and installed a more recent nvidia driver:[INDENT]```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install nvidia-driver-455
```
[/INDENT]
 
I now can see the Ubuntu load screen! So there is that. Pressing F7, I see the boot process. With the same error message seen back in the Attach1.
I now end up in a black screen with a not-blinking underscore..



 
I am opening this thread as I really dont see where to look now as I cant grasp the problem. I am sorry if it is somehow redundant with other posts.

---

### Post by frederic-c on 2021-12-11
UPDATE : I, so far, troubleshooted several things.. SPOILER.. without having solved the bigger problem : I still dont boot to Ubuntu.  


[B]*DEPENDENCY FAILED*

[/B]The dependency error seen in Attach1 was resolved as followed:
- boot on a live USB session. In command line, enter:[INDENT]```
sudo blkid
#write down the UUID corresponding to the failed disks in the error message from the boot screen
```[/INDENT]

- then, opening /etc/fstab I see differences between UUID entered and the ones from the blkid. Namely, with the /boot/EFI partition.
- I substitute the IDs with  blkid output. 5I make sure to write down the previous IDs before making any change).

*This solved the problem*.


[B]*UPDATE & UPGRADE failures*
[/B]After paying more attention, I realized update and upgrade commands werent as effective as intended.
[INDENT]-UPGRADE
The upgrade was having Signatures problems for 3 different repositories. I followed this Tutorial and it got solved.
[https://stackoverflow.com/questions/33598679/how-to-fix-invalid-signature-when-apt-get-update-error](https://stackoverflow.com/questions/33598679/how-to-fix-invalid-signature-when-apt-get-update-error)

-UPDATE
[/INDENT]
[INDENT]The update was was still encountering problem with a Gamemode ppa I had added a while back. 
My first tries were to remove the PPA with add-apt-repository command. However, I was failing to enter the exact name of the ppa required. Following this : [https://askubuntu.com/questions/307/how-can-ppas-be-removed](https://askubuntu.com/questions/307/how-can-ppas-be-removed) I deleted the .list file in /etc/apt/sources.list.d corresponding to the PPA. It is not properly removed removed then, but the apt update can go on however.

 [/INDENT]
*****[B]FSCK*

[/B]Fsck either in CLI or with the recovery mode couldnt analyze /dev/sda3 where my Ubuntu partition is, as it returned it was mounted. Using a live USB session, I could bypass this problem. It stated that my Ubunutu partition sda3 was clean.

[B]*BOOT REPAIR*
[/B]Out of ideas, Iperformed still on the live USB session a (Recommended) Boot Repair fix. It did not solve the error I am encountering.



Folowing these fixes, I still cant boot. The process goes further as I can now see the "ASUS-Ubuntu" loading screen (just before the normally Ubuntu purple loading screen.

Booting in nomodeset doesnt change anything..
I keep digging and will update it here in case it is useful to anyone else.

---

### Post by dragonfly41 on 2021-12-11
[COLOR=#000000]> [/COLOR][COLOR=#000000]Memory : migrated from 4Gb+4Gb to 4Gb+8Gb[/COLOR][COLOR=#000000]
The fact that the black screen happened right after the ram stick change could be a coincidence. Does it make sense to anybody ?
[/COLOR][COLOR=#000000]

I have been running with 8GB and recently purchased an additional 8GB .. still waiting to be added.

I read that you have upgraded to 4+8GB.
I'm sure that in my reading about memory upgrades there was mention about matching the sticks.
You could try uninstalling the old 4GB and try using only 8GB stick.
It *may* be that you need to match your 8GB sticks and buy another 8GB.   8+8 GB.
But that is my best guess.[/COLOR]

---

### Post by frederic-c on 2021-12-11
Thank you for your reply dragonfly !
Im having this problem ever since I changed my ram set indeed, I am still not finding anything on this.
The other 4Gb are welded to the board unfortunately :/ Is there a way to disable this stick by in the software level ? 
The fact that I am booting without trouble on Windows10 or several different distros live USB sessions is worth noting also. I dont have much knowkledge about it, I imagine it to be relevant.

---

### Post by dragonfly41 on 2021-12-11
[COLOR=#000000]> The fact that I am booting without trouble on Windows10 or several different distros live USB sessions is worth noting also.
That added fact seems to rule out my theory.
Can you reverse your tracks and now remove the added 8GB to get back to original working state?[/COLOR]

---

### Post by oldfred on 2021-12-11
You cannot install a different nVidia driver without totally purging any old drivers.
You get conflicts and typically the black screen. 

If you can boot recovery mode, purge all nVidia & install default.

If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

#What is installed
dkms status
lsmod | grep nvidia

sudo apt-get remove --purge nvidia-*

sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you can manually choose any in list.
sudo apt-get install nvidia-XXX 

Some after a purge need this:
sudo apt update
sudo apt install linux-generic
sudo apt full-upgrade

---

### Post by frederic-c on 2021-12-12
Thank you very much oldfred for correcting my installation process of nvidia drivers. I performed a much proper install following your advice and saved the commands in a txt file. The result however wasnt successful, still the exact same boot problem.
Also, worth-noting that my "nomodeset" boot attempts were as unsuccessful.
We might safely agree Nvidia drivers should be out of suspicion for now ?

Thank you dragonfly, it makes sense to try back with the 8Gb settings, and keep or discard the memory cause hypothesis. I will give updates as soon as I put my hands on the old memory stick.
I keep in mind the memtester report (see first post) that should set out any memory problem, but I dont have much perspective on which conclusions to draw from this report.

---

### Post by frederic-c on 2021-12-24
UPDATE:
I finally could switch back to my 4Gb stick... and nothing at all changed.

The ram problem can be erased from the list of suspects.. and I am definitely puzzled now

---

