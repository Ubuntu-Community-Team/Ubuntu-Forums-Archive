---
title: "Cant reboot to Ubuntu!"
date: 2013-05-04
forum: General Help
---

### Post by Ashfaqur Rahman on 2013-05-04
I am using Windows 7 side by side Ubuntu(Dual Boot).
And Using EasyBCD to boot from start up.
It was OK. I have reboot to Windows and Ubuntu several times.faced no problem.
Recently when I tried to boot to Ubuntu a black screen came and showed following lines:

```

Try (hd0, 0) : NTFS5 : No Ang0
Try (hd0, 1) : NTFS5 : No Ang0
Try (hd0, 2) : Extended :
Try (hd0, 3) : NTFS5 : No Ang0
Try (hd0, 4) : EXT2 : _(blink)

```

Then nothing happens. Just blinking.
I cant boot to Ubuntu.
Whats wrong?

---

### Post by 2F4U on 2013-05-04
From the list of partitions it looks as if Ubuntu isn't installed. There are 3 NTFS partitions, which most likely belong to Windows. Then there is a EXT2 partition. In a default install Ubuntu would use EXT4. Since you provide not much information it is impossible to judge what happened. I would boot into a liveCD and use Gparted to look at the partitions.

---

### Post by Ashfaqur Rahman on 2013-05-04
I dont know why its showing EXT2.
when I install ubuntu I created 4 Logical partition breaking a primary partition /dev/sda2(which was actually local disk d: in windows) .
1.Boot partition(I mean mount point /boot) which was created as EXT4 Journal file system
2.Root partition(I mean mount point /) which was created as EXT4 Journal file system
3.Home partition(I mean mount point /home) which was created as EXT4 Journal file system
4.for swap created as swap area.
Then I install Ubuntu.

Ok I am giving you a screenshot of Gparted.

---

### Post by Ashfaqur Rahman on 2013-05-04
I have just checked my partitions from Live Mode with Gparted.
I think theres no problem with my partitions.

I should have three NTFS partition
I have three NTFS partition /dev/sda1 (100MB system reserved in windows), /dev/sda2 (my 50GB C drive in windows or partition C), /dev/sda4 (my 420GB E drive in windows or partition E)

I should have 1 extended partition.
I have 1 extended partition /dev/sda3 (which was my 30GB D drive or partition D in windows which I deleted to create that 4 logical partition to install ubuntu)

I should have 4 logical partition(1 swap area, 3 EXT4)
I have 1 linux-swap(1GB /dev/sda7), 3 EXT4 (500MB /boot partition /dev/sda5, 20GB / partition /dev/sda6, 8GB /home partition /dev/sda8)

Sorry I cant give you screenshot as when I take screenshot from Live Mode(PrntScrn button) and save it.When I try open it from windows (as cant access ubuntu) it says " cant open either this picture is deleted or its in a location that isn't available " though I saved it in my E partition!!

---

### Post by Ashfaqur Rahman on 2013-05-04
At Last found a solution here : [https://neosmart.net/wiki/display/EBCD/Ubuntu](https://neosmart.net/wiki/display/EBCD/Ubuntu)

Following the steps after [COLOR=#003366][FONT=Arial]Adding Ubuntu to the Windows Bootloader headline.
[/FONT][/COLOR]

---

### Post by Ashfaqur Rahman on 2013-05-05
It seems that somehow my GRUB or MBR got affected and after recreating GRUB or MBR this problem solved.

---

