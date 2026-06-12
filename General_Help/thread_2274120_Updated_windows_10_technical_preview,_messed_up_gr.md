---
title: "Updated windows 10 technical preview, messed up grub. How can i fix without reinstall"
date: 2015-04-17
forum: General Help
---

### Post by dalvacoder on 2015-04-17
So i'm dual booting ubuntu and windows 10 technical preview. THe other day I guess microsoft pushed a new windows update so i decided to update my windows 10 which was running perfectly alongside my ubuntu 14.10 install. Well during the update, when windows restarted I got stuck in grub rescue screen and couldnt get past it. I tried downloading the ubuntu boot repair tool thing, started my computer from the usb with it, and ran the tool. It didn't give me an option to repair grub, it only gave me option to fix mbr, so i selected that. THen when I restarted I got a different error screen saying there was a problem with my windows bootloader and to insert windows install media and repair it. After trying to use the repair tool again several times to get grub to repair and it not working, i just used my windows install usb to repair the mbr error and now my windows 10 finished updating completely and it runs fine again. Problem is I can't get into ubuntu, and ubuntu is my shiz. Sooo, i tried booting from my ubuntu install usb, it says "no operating system detected" and gives me the option to wipe completely and install, obviously I don't wanna do this. THe other option is to partition the disk and when i select that I see all of my partitions, although I cant really tell which is my ubuntu one but I have an idea which one it might be. So since I don't want to reinstall ubuntu and wipe all the stuff I had in that partition I tried booting into the live ubuntu from usb, and running terminal and using the command "sudo grub-install /dev/sda" and i got an error saying "failed to get canonical path of cow". Idk what else to do to reinstall grub, when i researched online it said to just install grub again using that command but its not working. So now what? Any help would be much appreciated :)

---

### Post by yancek on 2015-04-17
To see which partition is Ubuntu, you would boot with a Live CD or flash, open a terminal and run the command:  sudo fdisk -l
 
Under the System column it will show the filesystem type which will probably be ext4.  Move to the left on that row to see which partition it is.  This should also show you what your primary internal drive is shown as since it apparently is not sda.  It should also show you whether you have an Ubuntu partitions still on the drive.  It's always a high risk to volunteer to test software as you did with the Windows Tech preview.

---

### Post by dalvacoder on 2015-04-18
Hey thanks for the response, I did fdisk before posting this and also before attempting to install grub, it is sda according to gparted and fdisk. I've included a screenshot.
Also, I'm pretty sure the Linux partition still exists because I didn't reinstall anything all windows did was update. I just need to figure out how to reinstall grub since its not working using the comman i tried. Anyone have any ideas?[ATTACH=CONFIG]261391[/ATTACH]

---

### Post by Impavidus on 2015-04-18
Your Ubuntu is gone. I assume the Ubuntu ext4 partition used to be in the extended partition, just before the swap partition. Maybe Windows decided to shrink the extended partition and not knowing what to do with the ext4 partition just deleted it? Just a wild guess.

As (most of) the Ubuntu partition is now unallocated space, you may be able to recover (most of) your files. Using your backups will be easier. But it seems you'll have to reinstall Ubuntu.

---

### Post by dalvacoder on 2015-04-18
Ugh that sucks. Oh well I guess thats what I chose when I decided to try out Windows 10. I didn't store many things to be honest I'm just upset because I had it set up just the way I wanted. Question, so now when i reinstall linux, and I select the manual option to decide on my partitions, do I install it on the extended space? I think the way I had it before was a seperate root portion and then some space for storage but I'm not quite sure. Also, what is on sda 3? Hidden ntfs winre ? Is that just some sort of windows recovery partition?

---

### Post by yancek on 2015-04-18
I expect sda3 is the standard windows recovery partition.  When you boot the Ubuntu installaton medium, use gparted on the disk to create another logical partition inside sda4, the Extended partition.  All you have inside that now is the swap so there seems to be a lot room.  You can create a root partition for the filesystem there (25-40GB) and use the rest of the space for a data partition.

---

