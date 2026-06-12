---
title: "desktop &quot;Files&quot; program cannot see all partitions"
date: 2022-05-05
forum: General Help
---

### Post by ed-crumbpacker on 2022-05-05
I have a hard disk sda broken into 4 partitions /dev/sda1 19 gig   /dev/sda2  214 gig extended of which is comprised of /dev/sda5  2g swap and /dev/sda6  212g
     (total of the /dev/sda2)
/dev/sda1 is bootable and type Linux
/dev/sda6 is also type Linux
Command "lsblk" says /home is located on /dev/sda6
Problem is:
When I use the "Files" program on the desktop, click on "Computer" then "Properties" it claims I only have the 19g of space and not the 212g on sda6
What is wrong and how can I fix it without destroying /home?  (I'm assuming I'm going to run out of space at 19g)

Thanks

---

### Post by Impavidus on 2022-05-05
If lsblk says that sda6 is mounted at /home, then it is mounted at /home. lsblk doesn't lie. I don't really know files a.k.a. nautilus.

Your sda2 and sda5 aren't available for storage as they have no filesystem, so I don't expect nautilus will show them. Nautilus doesn't show partitions mounted at boot time using /etc/fstab in the side panel, but should be aware of them.

A 19GB root partition is a bit small though. It's a bit hard to change without reinstalling, but it can be done with a live disk. Make sure you've got backups of all your important files.

---

### Post by tea for one on 2022-05-05
Files (nautilus) > Other Locations > Computer - This path is your system partition: 19GB in your case.
The terminology Computer is a bit misleading in this application.

Can you open a terminal and run this command:-
> lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint 

For legibility, please paste the output within code tags via the advanced reply/editor.

If you wish to see all the partitions via a GUI, have a look at Disks (gnome-disk-utility 42.0)

I notice that you mention extended partitions, which are more difficult to manage when compared to GPT.
Is your installation recent?

---

### Post by ed-crumbpacker on 2022-05-05
cfdisk
```
    Device      Boot    Start       End   Sectors   Size Id Type
>>  /dev/sda1   *        2048  39077887  39075840  18.6G 83 Linux               
    /dev/sda2        39079934 488396799 449316866 214.3G  5 Extended
    &#9500;&#9472;/dev/sda5      39079936  42991615   3911680   1.9G 82 Linux swap / Sol
    &#9492;&#9472;/dev/sda6      42993664 488396799 445403136 212.4G 83 Linux

```  

lsblk
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sr0     11:0    1  1024M  0 rom  
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0   1.9G  0 part [SWAP]
&#9500;&#9472;sda1   8:1    0  18.6G  0 part /
&#9492;&#9472;sda6   8:6    0 212.4G  0 part /home
```

I should have mentioned ubuntu 16 on old computer

I should also mention I am reading "man" on lsblk because the "tea for one" info request is throwing an error, mostly because I'm an "lsblk" moron

---

### Post by GhX6GZMB on 2022-05-05
There's nothing at all wrong with your system.
But I think you're stuck in M$ C:\, D:\, E:\ etc. thinking and looking at the partitions like that.
UNIX/Linux doesn't operate that way: there's one directory tree, and storage (in this case, partitions) are mounted under the different directories as needed.
In this case, / has 19 GB to work with, and /home 212 GB.

BTW: Ubuntu 16 is ancient. And if it's an old computer, a lighter version might bring more happiness (Lubuntu, Xubuntu). I recommend 20.04 LTS at this point, later this year 22.04 is an option.

---

### Post by tea for one on 2022-05-05
> **ed-crumbpacker said:**
> I should have mentioned ubuntu 16 on old computer

As mentioned by [COLOR="#0000FF"]ml9104[/COLOR], Ubuntu 16.04 is now unsupported unless you have subscribed to Extended Security Maintenance (which is generally for business/enterprise users).
Your priority is to ignore your local difficulty with Files(nautilus) and back up your personal data.

I would suggest that you download Ubuntu 22.04 (or your preferred flavour), create a bootable USB and try it out.
If all goes well, install a supported OS (in UEFI mode with GPT) and restore your data.

Please post back if you have any questions about UEFI and GPT.

---

### Post by Impavidus on 2022-05-06
Ubuntu 16.04 is indeed old. You no longer get any upgrades on that, except if you signed up for extended security maintenance, but that isn't ideal either. {X,L,K}ubuntu 20.04 still have one year of support left, or you can install 22.04 right away. 22.04 isn't entirely stable yet, but installing that saves you an upgrade in the coming 11 months. On an older computer, Xubuntu or Lubuntu may be better than Ubuntu, as they require less resources.

If you try a fresh install of 22.04, make the root partition a bit larger. 19GB is tight. Around 30GB will do.

---

### Post by TheFu on 2022-05-06
Excellent answers above by everyone.
```
$ lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint 
lsblk: unknown column: fsuse%,fsavail,mountpoint
```
I'm seeing an error too.  I use:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
and
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
to gather disk overview information.  fsuse%,fsavail, aren't working for me.

---

### Post by tea for one on 2022-05-06
> **TheFu said:**
>  fsuse%,fsavail, aren't working for me.

I ran [COLOR="#0000FF"]lsblk --help[/COLOR] in a terminal and both FSUSE% and FSAVAIL were listed in the Available Output Columns.
```
edited@edited-22-04:~$ lsblk -V
lsblk from util-linux 2.37.2
edited@edited-22-04:~$ 
```
```
edited@edited-22-04:~$ lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint 
NAME          SIZE TYPE FSTYPE FSUSE% FSAVAIL MOUNTPOINT
sda         111.8G disk                       
&#9500;&#9472;sda1        487M part vfat                  
&#9500;&#9472;sda2       25.7G part ext4                  
&#9500;&#9472;sda3       27.7G part ext4                  
&#9500;&#9472;sda4         16M part                       
&#9492;&#9472;sda5       57.9G part ntfs                  
nvme0n1     232.9G disk                       
&#9500;&#9472;nvme0n1p1   512M part vfat       1%  505.7M /boot/efi
&#9500;&#9472;nvme0n1p2    30G part ext4      47%   14.2G /
&#9500;&#9472;nvme0n1p3    31G part ext4      37%   17.7G /home
&#9492;&#9472;nvme0n1p4   100G part ext4      34%   60.1G /mnt/381ee381-e1af-4ca4-9a8d-fcccf8987669
edited@edited-22-04:~$ 

```
Is your version number of [COLOR="#0000FF"]util-linux[/COLOR] different?

---

### Post by TheFu on 2022-05-06
> **tea for one said:**
> I ran [COLOR="#0000FF"]lsblk --help[/COLOR] in a terminal and both FSUSE% and FSAVAIL were listed in the Available Output Columns.

I didn't see the OP say 22.04. Must have missed that.  Thought he was running 16.04 as we try to push for a supported release.  Plus, the error was reported by the OP.

Neither 20.04 nor 18.04 support those options.  One more thing to look forward to in a new LTS, but many people don't jump to newest release ASAP.

---

### Post by tea for one on 2022-05-06
> **TheFu said:**
> I didn't see the OP say 22.04. Must have missed that.  Thought he was running 16.04 as we try to push for a supported release.  Plus, the error was reported by the OP..

You did not miss anything, the OP did not mention 22.04 at all. 
16.xx was mentioned in post 4 after I had posted the command in post 3.
Unbeknown to me, I had no idea that my suggestion would not yield a successful terminal output.

Anyway, the interesting outcome for me is that there is great variation in the output of terminal commands depending on the version used.
The OP has not reported back after all these comments/suggestions so I hope that a supported OS installation is being considered.

---

### Post by TheFu on 2022-05-06
> **tea for one said:**
>  Anyway, the interesting outcome for me is that there is great variation in the output of terminal commands depending on the version used.

Ah ... this is why I strongly suggest that people read the manpages ON-THEIR-SYSTEM and not by web searches.  The options are different for different versions of many programs. They change all the time. Use the local manpages.

Almost always, using older versions of programs will retain the same options for the same purposes in newer versions, but not always.  I've been burned by systemd stuff a few times.  Their manpages don't always describe the code delivered, but the code in a soon-to-be available release.  On an LTS, that's a problem, since only security and bugfixes should get updates.

---

