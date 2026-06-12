---
title: "External Hard Drive Ubuntu"
date: 2007-11-12
forum: General Help
---

### Post by pingue110489 on 2007-11-12
Hi. 
Having just installed Ubuntu on my External HDD, (with Vista as default on the internal HDD), I was very pleased, while it was sitting at home, with the external drive plugged in. I managed to change GRUB to have Vista load by default, which was fine. 
However, I took my laptop out earlier, and didn't have space to carry the external drive. When I came to boot up, I expected to see GRUB as normal, and there just be an error if I selected ubuntu, and be able to boot to vista as norm. Instead, I get a GRUB error message 20 (21?), and cannot even boot to Vista, as the list doesn't appear. Is this possibly something to do with where GRUB was installed, and is there a way around it? 
Apologies if this is a stupid question: I'm relatively new to (and impressed by) Linux, and have never had much need to play around with bootloaders before! 
Thanks muchly

---

### Post by -=Ghostlike=- on 2007-11-13
probably the fastest way: insert your Vista disk -> recovery mode -> mbrfix (that resets your Vista bootloader) then reboot with your Ubuntu CD and USB drive connected

let the live-cd startup -> run gnome-terminal -> 'fdisk -l' in terminal to check your USB drive letter (probably /dev/sdb) -> 'grub' in terminal (that gives you a menu) -> type 'find /boot/grub/stage1' -> type 'root hd(X,Y)' (where X and Y are the output from the find command, it will probably be 'hd(1,0)' -> type 'setup hd(X)' -> type 'quit' -> reboot your system.

You should now have the Vista bootloader when you don't have your USB drive connected and grub when your drive is connected.

---

### Post by Fire_Chief on 2007-11-13
> **pingue110489 said:**
> Hi. 
Having just installed Ubuntu on my External HDD... I expected to see GRUB as normal, and there just be an error if I selected ubuntu, and be able to boot to vista as norm. Instead, I get a GRUB error message 20 (21?), and cannot even boot to Vista, as the list doesn't appear
The reason you are seeing this problem is because GRUB uses files located in /boot on the Ubuntu filesystem to hold its configuration and boot menu. The MBR that is written to the Internal HDD has just enough information to load GRUB and the point to the GRUB configuration files in /boot. Since you did not take the External HDD with you, the MBR section could not find /boot and therefore could not find it's configuration or show you the boot menu.

Follow Ghostlike's suggestion to fix your MBR to boot Vista > probably the fastest way: insert your Vista disk -> recovery mode -> mbrfix (that resets your Vista bootloader)and then have a look here to get Vista to also boot Ubuntu for you.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by pingue110489 on 2007-11-13
Thanks muchly for the promt replies. I had already managed to recover using a Vista CD, as I needed it urgently, and Vista was OK. I wil try the Ubuntu steps as soon as I have a chance, and will let y'all know. Again, thanks, ghostlike amd fire_chief: you have saved me from endless hours of struggling, as i would otherwise have been lost!!!

---

### Post by soman on 2007-12-31
i ran into this same problem with xp. will the same procedure work?

thanks in advance.

---

### Post by pingue110489 on 2008-01-01
I can't imagine it wouldn't: the process can't be much different, though vista and xp boot slightly differently. I may be able to give you more insight next week: I'm planning on trying something similar (again). Will get back to you if I find any problems.

---

### Post by soman on 2008-01-02
hmm. i used the super grub disk to fix my xp mbr, then followed ghostlike's procedure. the result:

xp boots up when the external drve isn't connected,and while GRUB *does* show up when i start up the external drive, i can get into neither xp nor ubuntu. 

should i not have used the sgd?

or does the problem lie in the fact that im using a dell?  i heard linux doesn't work too well on those.

any help would me much appreciated, thanks.

---

### Post by soman on 2008-01-03
whoops, should have been more specific.

when i have connected the external drive and i try to boot into ubuntu, i get GRUB error # 17: Cannot mount selected partition, and when i try to get into xp, i get error #13: Invalid or unsupported executable format.

i am so confused...

---

### Post by pingue110489 on 2008-01-03
I had a similar sort of problem soon after I installed linux, and found it extremely frustrating. 
What I did was when Grub shows the list, press `e` to edit the selected entry (forgive me if it's not e), change the (0,1) or whichever numbers to something else, <ENTER>, then `b` to boot it. Try plenty of combinations; (0,0) ; (0,1) ; (0,2) ; (0,3) ; (1,0) ; (1,1) ; (1,2) etc etc. This is because grub seems to load disks in a strange order, so windows (at least for me) showed up in a partition number I didn't expect. I have no idea if this'll work, but it did for me, so hopefully you'll have some luck. 
Mike

---

### Post by soman on 2008-01-03
hey, thanks. it boots now. 

i was wondering if you could explain the 'theory' behind this 'technique'; what exactly did i change in my computer to make it work?

---

### Post by geirha on 2008-01-03
You didn't change anything, you just altered the boot entry to point to a different partition from the grub menu itself, it doesn't save anything, so you'll have the same problem next time you boot. Write down the correct partition numbers (X,Y) and edit your /boot/grub/menu.lst accordingly, changing the line ```
# groot=(hdX,Y)
``` for the ubuntu entries, and the windows entry you change directly.
Run ```
sudo update-grub
``` after you've edited menu.lst (update-grub will change the root entry on each ubuntu entry with the one you specified on the groot-line)

---

### Post by pingue110489 on 2008-01-05
Keeping in mind that I'm no expert, this is roughly what I think happens. 
When GRUB loads, it reads that list of OSs from wherever it is you installed Linux. The list contains references to the partition the OS is installed on, and GRUB boots from wherever the list tells it to look, be it the Linux or XP partition.
However, for some reason, the list doesn't seem to be in a sensible order, so it's trial and error till you find the right partition. 
Eg (0,1) - This would presumably be the 2nd partition on the first hard disk, though this varies depending on the disks, and where things are installed etc etc. My tactic has been not to think about it, and just hope it stays working.
Glad it works for you now, though
Mike

---

