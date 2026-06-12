---
title: "Wubi Grub load problem"
date: 2012-11-22
forum: General Help
---

### Post by tttz on 2012-11-22
Hi guys,

I have Ubuntu installed thru Wubi. Few days ago I had to shut down my laptop with button, because it didn't want to shut down normally. On next boot I started laptop I chose "ubuntu" (the other option is win). Then I should get a menu with kernels, but I got such screen [http://cdn.ttgtmedia.com/digitalguide/images/Misc/figuur1.gif]("http://cdn.ttgtmedia.com/digitalguide/images/Misc/figuur1.gif") instead.

I got a copy of root.disk by using LiveDVD, luckily.

I read a lot of forums, blogs and other stuff about this, but nothing works for me, so that's why I'm writing on here now. Hoping someone knows how to fix my problem.

When I was in liveDVD, firstly I couldn't mount the root.disk. Then tried fsck.ext4 and I could mount it. Thought this might also fix the booting problem, but it didn't.

I found that procedure like described here  [http://calamari.wordpress.com/2009/12/01/fixing-a-broken-wubi-grub-after-ubuntu-updates/]("http://calamari.wordpress.com/2009/12/01/fixing-a-broken-wubi-grub-after-ubuntu-updates/") helped many users. Of course it was not my case. Got problem on this command:
*linux /boot/vmlinuz-(Your version of the kernel)*. No disk found or no file found.

If this info is important - I'm using Ubuntu 10.04.

What I would like to reach is:
1) not lose my data - DONE
2) preferably fix grub or wubildr or where the problem might be
3) I don't wanna lose all my settings and install programs again, so is it possible to? :

Install Wubi again, and rewrite fstab's root (/) to the old root.disk file? (I'm not sure if it'd work with wubildr. Won't there be problem with different kernels?)

Or is it possible to install Wubi again, and replace it's new root.disk with the old one? Again, not sure if kernels are not problem while booting.

Or last idea - move /home, and hopefully /opt, /usr or other dirs to get my installed programs, gnome settings (as set emblems) to fresh new installation? (maybe even not thru Wubi).

Thank you

p.s.: I'm sorry if I wrote something wrongly, tagged wrongly or similar - I'm totally new here. :-)

---

### Post by Karlchen on 2012-11-22
Hello, tttz.

You have not told us which operating system refused to shutdown properly when you pressed the power button for 5 seconds thus performing a hard shutdown.
I assume it was Ubuntu. Right?
In this case, you should start troubleshooting by following this official howto: [**How can I access my Wubi install and repair my install if it won't boot?**]("https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F")
HTH,
Karl

---

### Post by tttz on 2012-11-23
Hi, thank you for reply.

Right, sorry, of course I was using Ubuntu :-)

I have seen that site, but it actually does what I did for backing up my root.disk. I was able to mount the disk with LiveDVD like this:

sudo mkdir /mnt/ubuntu
sudo mount -o ro,loop /media/SOME_WINDOWS_THING/ubuntu/disks/root.disk /mnt/ubuntu

But this helped only to backup, I'm not able to fix GRUB this way :-(
One little difference was, I used fsck.ext4.

---

### Post by Karlchen on 2012-11-23
Hello, tttz.

Assuming that your root.disk holds an ext4 filesystem, launching fsck will invoke fsck.ext4, too.

As you keep getting a Grub error, the following things come to my mind:

On the Windows partition, drive C: in most cases, there will be the files wubildr, wubildr.mbr and wubildr.cfg. Maybe one of them is damaged.
In the folder \ubuntu\winboot, there should be the same three files.
Maybe it is worth a try to copy these 3 files to the root folder of the Windows partition thus overwriting the existing files.

Next idea:
Lucid Lynx installed via Wubi will only startup correctly provided the underlying Windows NTFS partition is clean. So it may be worth a try to run chkdsk on all NTFS partitions at Windows boot time.

Final question for the moment:
Prior to seeing the Grub prompt as illustrated in [this screenshot]("http://cdn.ttgtmedia.com/digitalguide/images/Misc/figuur1.gif"), is there an error message which gives a hint as to why Grub does not feel like booting Lucid Lynx?

Kind regards,
Karl

---

### Post by Karlchen on 2012-11-23
Hello, tttz.

About your question on re-installing via Wubi and restoring the current root.disk file:
> Install Wubi again, and rewrite fstab's root (/) to the old root.disk  file? (I'm not sure if it'd work with wubildr. Won't there be problem  with different kernels?)Yes. It can be done. (Assuming that your current root.disk file is not damaged.)
In this case you must be absolutely sure about which Wubi version matches your current Lucid Lynx version. (You must not use any Wubi that comes with a different Ubuntu version.)

E.g. my current Lucid Lynx is Ubuntu 10.04.4, i.e. 10.04 with SP4 installed. You can find out by mounting your current root.disk again and going to the folder /mountpoint/etc and doing a ```
cat lsb-release
```The matching wubi.exe for Ubuntu 10.04.4 e.g. would be this one: [wubi.exe 2012-Feb-07 21:16:55 1.4M]("http://swtsrv.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu-release/10.04.4/wubi.exe")

Steps to follow: 
[LIST]
[*]Boot Windows. Move the current root.disk file to a different folder outside of \ubuntu, e.g. to \temp\root.disk.
[*]Uninstall Ubuntu (Wubi) from "Programs and Features"
[*]Perform a Wubi installation of the same Lucid Lynx edition which you are using currently and install to the same folder and drive whee the current Ubuntu lives.
[*]Once the installation has completed (Windows part and Linux part) reboot into Windows.
[*]Replace the new root.disk by the root.disk inside \temp
[*]Reboot into Linux
[*]I admit I am not quite sure whether you will have to change any blkids inside the Grub commands when invoking the Grub menu during this reboot. - Never had to revive a Wubi installation this way. So I am just repeating the steps which I remember having read somewhere in this forum.
Hm, the Wubi Guide suggests there may be no need to worry about blkids at all: [How can I make a backup of my Wubi install?](https://wiki.ubuntu.com/WubiGuide#How_can_I_make_a_backup_of_my_Wubi_install.3F)
[/LIST]
Hope this helps nevertheless.

Karl

---

### Post by tttz on 2013-02-05
Thank you for your replies.

I have one bad and one good news.

The good one: I made it work :)
The bad one: for those who will solve such problem - I solved it a different way than I wanted to. Gonna write down.

I tried to get new installation of Wubi. But since it was 10.04, it was not yet possible to download such. So I didn't do anything with wubildr files.

I checked windows' disk with some ntfs Linux CLI program (I'm sorry, I don't remember the name). It said the disk needs to be repaired or something like this. I read (online) that this program only checks the basics, but if you want to repair it, you have to run windows' checkdisk. Since I didn't have access to win, I couldn't.

I backed up everything from win with Linux Live DVD. Downloaded Wubi migrate program ([https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)).

I deleted everything from hard drive. Installed new Linux (partition must be larger than the Wubi root.disk). Downloaded my old root.disk to this new partition and ran Wubi Migrate program. My whole Wubi installation became normal install in a new partition. :)

I recommend to try the whole process in Virtual box, so you are familiar with what you are going to do.

---

