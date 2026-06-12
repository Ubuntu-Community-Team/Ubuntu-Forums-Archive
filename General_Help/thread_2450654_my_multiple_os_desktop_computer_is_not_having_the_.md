---
title: "my multiple os desktop computer is not having the option to load fedora at startup"
date: 2020-09-18
forum: General Help
---

### Post by ronjjjg8885 on 2020-09-18
i've applied the latest updates and since then i don't see fedora on grub
i've windows, ubuntu, and the fedora which is now missing from that list...

i need to study with fedora and i want to know if you could tell me how to make the fedora back on that list and what might have happened

thanks ! :P

---

### Post by guiverc on 2020-09-18
I would firstly `sudo update-grub` & hope it detects it.  (*I think I mostly do this so I can watch it detect OSes and look for anything wrong, or different to the norm [eg. speed of detection]*)

I would then load KDE Partition Manager or `gparted` & check your partitions for issues (are file-systems clean etc).  I would then likely `sudo update-grub` again in hopes it'd detect Fedora system.

If not fixed, next I'd `mount` the Fedora partition, and `update-grub` again with it mounted. In my experience this detects systems that for an unknown reason aren't picked up at other times. I don't know why, but I've had this work well before a couple of times I've not an another GNU/Linux detected. I can't give reason as to problem, the few times I've had to use this, the system has returned to detecting it quickly, or I never found the cause.   

My 2c suggestions anyway

---

### Post by ronjjjg8885 on 2020-09-18
TNX :) that was fast
this is the output of `sudo update-grub`
[https://pastebin.com/bGa1pRdk](https://pastebin.com/bGa1pRdk)
i don't see fedora on the list.
do i need to install KDE for the `gparted`?
how do i `mount` fedora like you have said after checking the partition?

---

### Post by ajgreeny on 2020-09-18
If your file manager shows the fedora partition in the left hand pane click on it and it may mount.

Is your fedora install using lvm which many years ago was the default at installation or is it encrypted?

---

### Post by guiverc on 2020-09-18
FYI: 

`gparted` is the GNOME version of KDE Partition Manager. I was using that as a means to `fsck` or *file-system check* your Fedora partition(s). You could use either, or other tools too including commands) to check your file-system (ie. `fsck`).  If errors are detected & fixed, you'll likely find the next `update-grub` works. 

For mounting, refer @ajgreeny's post.

---

### Post by ronjjjg8885 on 2020-09-18
i didn't encrypt it. i think it is lvm
how can i determine which one is fedora's partition?
[ATTACH=CONFIG]286978[/ATTACH]

---

### Post by ronjjjg8885 on 2020-09-18
guiverc
these are my disks details from the "disks tool"
[https://ibb.co/zRxQCNB](https://ibb.co/zRxQCNB)
[https://ibb.co/yqCfzyh](https://ibb.co/yqCfzyh)

i'm a bit confused because i'm still not sure how to know which partition is fedora's.
after i know, do i probably just need to update grub again?

---

### Post by oldfred on 2020-09-18
If sda8 is LVM as shown that probably is your Fedora.

In Ubuntu you also need the LVM tools to be able to mount it.
sudo apt-get install lvm2
Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)

Post this in code tags ( Go Advanced editor in Forum and # icon)
lsblk -o NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE,MODEL, uuid | egrep -v "^loop"

There was a recent grub update in Ubuntu which would have reset Ubuntu as default or to first in boot order in UEFI, if UEFI or installed Ubuntu's grub to MBR if BIOS. If mostly using Fedora, you may want its grub to be default.

---

### Post by ronjjjg8885 on 2020-09-18
i performed the command 'sudo apt-get install lvm2'
this is the results:
```
https://pastebin.com/yZmhzQeR
```
but i still can't monut sda8.
do i need to rebbot first?

do you need me to enter all the commands of:
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)
?
and then copy the output here in tags?

or perhaps you have meant to type:
```
lsblk -o NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE,MODEL, uuid | egrep -v "^loop"
```
?

do you mean that perhaps i don't have to do a thing and just restore the fedora's grub to its default?

thank you

---

### Post by oldfred on 2020-09-18
You need to mount it, so it is seen.
You can run the lslbk command so we can see it mounted & which partition is which.
And then sudo update-grub should work.

Then you can boot into Fedora and install its grub as default. Do not know Fedora nor command to install grub, but expect similar to Ubuntu's commands.

---

### Post by Dennis N on 2020-09-18
> but i still can't monut sda8.

You can't mount sda8 since it's an LVM physical volume. You would need to know the **LV path** for Fedora's root logical volume to mount it. You can use **sudo lvdisplay** to find the LV Path.

Then you can mount it using this construct:
```
sudo mount LV-path mount-point
```

---

### Post by ronjjjg8885 on 2020-09-19
ok
but do you think that i need to follow:
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)
for mounting it? because with the sudo apt-get install lvm2 i could not mount it in the file manager as it is not seen there.

i also not sure how to use the 'sudo mount /dev/YourVolGroup00/YourLogVol00 /YourMountPoint' command. what should i fill in "YourVolGroup00/YourLogVol00 /YourMountPoint"
i'm attaching the results of all the commands except for the last one:
[https://pastebin.com/9k17zn7w](https://pastebin.com/9k17zn7w)


edit:
i've now rebooted and it's working. fedora is shown and i i'm using it now.
i'm wondering how exactly can i use the fedora's grub so it doesn't happens again.
thanks

you really helped me and saved me from installing fedora again.

---

### Post by Dennis N on 2020-09-19
> i'm wondering how exactly can i use the fedora's grub so it doesn't happens again.
You don't need to do anything with Fedora's grub, such as reinstall it.

With UEFI, the listing order in the UEFI boot manager determines which OS boots at startup. You can change that in the UEFI firmware (sometimes called 'UEFI BIOS') and put Fedora first. Look in the boot settings in the UEFI.

When Ubuntu upgrades or reinstalls grub, it changes that boot order to put Ubuntu first. That's what happened here. BTW, Fedora doesn't change this order when it upgrades its grub.

---

### Post by oldfred on 2020-09-19
Most systems will let you change boot order with efibootmgr.
A few only seem to work if you change in UEFI as Dennis N has explained.

Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
 sudo efibootmgr -o 0,1,2
see also 
man efibootmgr

---

### Post by ronjjjg8885 on 2020-09-22
Tnx !

---

