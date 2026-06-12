---
title: "How to move around partitions"
date: 2014-02-15
forum: General Help
---

### Post by ThePie on 2014-02-15
I have this partition scheme set up below. I want to move the 300 MB partition to the second to last space so it's between the 50GB - and the the HP_TOOLS partition.

**Ignore the color scheme in the picture. Windows has it all screwed up.**

[IMG]http://s6.postimg.org/u9zeir6k1/Untitled.png[/IMG]

[COLOR=#0000cd]Primary[/COLOR], [COLOR=#006400]Logical[/COLOR][B]
[COLOR=#0000cd][FONT=Arial]/dev/sda1 * SYSTEM[/FONT][/COLOR]
[COLOR=#0000cd][FONT=Arial]/dev/sda2 C:[/FONT][/COLOR]
[COLOR=#006400][FONT=Arial]/dev/sda5 300 MB[/FONT]
[FONT=Arial]/dev/sda6 8GB[/FONT]
[FONT=Arial]/dev/sda7 T:[/FONT]
[FONT=Arial]/dev/sda8 50 GB NTFS[/FONT]
[FONT=Arial]/dev/sda9 50 GB RAW[/FONT]
[FONT=Arial]/dev/sda10 50 GB -[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#0000cd][FONT=Arial]/dev/sda4 HP_TOOLS[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][/B]
To This:[COLOR=#0000CD]

Primary[/COLOR], [COLOR=#006400]Logical[/COLOR][B]
[COLOR=#0000CD][FONT=Arial]/dev/sda1 * SYSTEM[/FONT][/COLOR]
[COLOR=#0000CD][FONT=Arial]/dev/sda2 C:[/FONT][/COLOR]
[COLOR=#006400][FONT=Arial]/dev/sda5 8GB[/FONT]
[FONT=Arial]/dev/sda6 T:[/FONT]
[FONT=Arial]/dev/sda7 50 GB NTFS[/FONT]
[FONT=Arial]/dev/sda8 50 GB RAW[/FONT]
[FONT=Arial]/dev/sda9 50 GB -[/FONT]
[FONT=Arial]/dev/sda10 300 MB[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#0000CD][FONT=Arial]/dev/sda4 HP_TOOLS


[/FONT][/COLOR][/B][FONT=Arial]How can I move the partition to the bottom of the extended partition? I have Windows 7 and Ubuntu 13.10 installed on the system to help achieve this.[/FONT]

---

### Post by oldfred on 2014-02-15
It is not exactly easy, as you have to move/copy everything in between. Anytime you start to move partitions around you need good backups as any interruption power failure or user error will corrupt data. It usually works but often then users take shortcuts and do not backup.

You also have to move space in and out of extended partition.
What data is in partitions, and why to move. Where a partition is on drive is not really critical in most cases.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by ThePie on 2014-02-15
I want to move sda5 down to where sda10 is but from looking at the guide I can't seem to get this to move. Is there something more detailed on moving partitions for gparted?

[IMG]http://s6.postimg.org/wxout3zld/gparted.png[/IMG]

---

### Post by oldfred on 2014-02-15
You have used all 4 primary partitions so any movement must be inside the extended partition.

But why move it?

It might be easier just to back it up, delete it and shrink sda10, to create a new partition and copy data into it. It only shows 21MB of data. 

But in moving partitions you have to make space by shrinking something and then slide it over, and continue to slide every partition in between. Then you can expand the last one if that is the goal??

---

### Post by fdrake on 2014-02-15
May I ask you why you want to move your partitions around? what are you trying to achive?

---

### Post by NM5TF on 2014-02-15
as old fred asked....***why*** do you want to move them ???

what do you expect to gain ???

tommy

---

### Post by ThePie on 2014-02-15
Fred: Yes that is what I'm assuming I'm going to have to do is slide everything over but being that everything is in the extended partition it's being annoying and when i shrink something I can't move the partitions around the swap partition.

Fdrake: I want to move the partitions because since I've already installed Ubuntu and another Linux os with another windows os all which are on their own 50 GB logical partition. When I made the 300 MB logical partition it placed it in front of the other logical partitions and now my ubunutu which was sda8 is now sda9 and I can't boot anything. i'm using a live Ubuntu usb boot to access gparted right now. So if I moved it to the bottom then the numbers would be correct again and 300 MB would be sda10. while my ubuntu would be sda8 again.

---

### Post by oldfred on 2014-02-15
Moving a partition does not fix a boot issue.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by ThePie on 2014-02-15
Well I tried this before, and because the location of the partition sdaX is different the OS (Ubuntu) isn't able to boot from the Windows boot manager when I turn PC on. 

(I have EasyBCD on Windows 7 and so the PC looks at the boot list that easy BCD created).

Is there a way to just like, run the boot-fix program and it will fix this? Not sure how to explain this really.

---

### Post by fdrake on 2014-02-15
follow the instruction on Boot-Info so that we can help you fix your booting problem.

---

### Post by oldfred on 2014-02-15
Boot-Repair will not fix EasyBCD as it has its own tools, and forum.
       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Some do use EasyBCD, but you have to force grub2 into a partition's boot sector. Grub2 does not fully fit, so it converts to blocklists or hard coded addresses. Updates to grub or kernel will often require grub to be reinstalled as the address may change. So if using EasyBCD you have to repair grub more often but that really is not grub but EasyBCD issue. EasyBCD uses an old version of grub that works inside a Windows partition to chain boot to the grub2 in the Linux partition.

We usually suggest just using grub2 to multi-boot. Windows is not designed to multi-boot and EasyBCD has a work around. But grub2 is designed to multi-boot systems.

---

### Post by ThePie on 2014-02-15
Alright so this is what I ended up doing.

I deleted that extra partition (300 MB) and then booted into live Ubuntu CD and ran the Boot-Fix -> "Quick Fix" and shutdown PC. Booted up and there was the GRUB loader with my 2 linux OS's and a line that has the Windows boot loader. So I got to Win boot loader, load win 7, run easyBCD, add items to boot list and fix mbr, and shutdown.

So what I have when I turn on is:

Windows Boot Loader
[TABLE="class: grid, width: 200"]
[TR]
[TD]Windows 7[/TD]
[/TR]
[TR]
[TD]Windows 8[/TD]
[/TR]
[TR]
[TD]Linux[/TD]
[/TR]
[/TABLE]

Click win 7 -> starts windows 7
Click win 8 -> starts windows 8
Click linux -> starts grub

GRUB
[TABLE="class: grid, width: 200"]
[TR]
[TD]Ubuntu[/TD]
[/TR]
[TR]
[TD]Mem Test[/TD]
[/TR]
[TR]
[TD]Windows BT[/TD]
[/TR]
[TR]
[TD]Debian[/TD]
[/TR]
[/TABLE]

Click Ubuntu -> starts Ubuntnu
Click Mem Test -> starts Mem Test (Comes with Linux)
Click Win BT -> Goes back to Win BT (Previuos menu)
Click Debian -> starts Debian

----------------------------------------------------------------------------------

Hopefully this helps someone in the future if they ever have problems like I did.
Also thank you guys for responding to this thread to help me.
That Boot-Fix program is a great tool to have also.

---

### Post by oldfred on 2014-02-16
If both Windows are in primary partitions, you can move boot flag to second install and run its repairs to add boot files. Then grub menu will show both Windows as boot options. Plus later if you delete the first install you do not delete the boot files from second install and have real Windows issues.

Windows only has boot files for all installs in the one partition with the boot flag or active partition on the drive set to boot from in BIOS.

Vista, but still same for how BIOS boot Windows systems work, not for UEFI.
 Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by ThePie on 2014-02-16
> **oldfred said:**
> If both Windows are in primary partitions, you can move boot flag to second install and run its repairs to add boot files. Then grub menu will show both Windows as boot options. Plus later if you delete the first install you do not delete the boot files from second install and have real Windows issues.

Windows only has boot files for all installs in the one partition with the boot flag or active partition on the drive set to boot from in BIOS.

Vista, but still same for how BIOS boot Windows systems work, not for UEFI.
 Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Ya I was thinking that but I like the way its set up with just the black screen and the 3 options for windows boot manager via easyBCD. I think it looks cooler that way. :)

---

