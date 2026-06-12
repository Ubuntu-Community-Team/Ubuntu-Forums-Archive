---
title: "3 Linuxes...want to delete 2... How do I know which is which?"
date: 2016-09-14
forum: General Help
---

### Post by mdsmedia on 2016-09-14
I've been a beginner for 11 years.

I'm currently using Kubuntu 16.04 and have no problem with it, except that it seems to delay keyboard entry in Facebook, in that I enter a few characters and it takes a while to receive the entry.

I have Ultimate Edition 3.8 in a separate partition, long neglected because I couldn't get it to work, but now it does, but installed UE 5.0.

I want to delete the two Ultimate Editions. Is there any simple way of determining which of my partitions is UE and which is Kubuntu?

---

### Post by oldfred on 2016-09-14
May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

And you want to make sure the grub in the MBR (if BIOS) is the grub from Ubuntu.

---

### Post by DuckHook on 2016-09-14
Real gurus might have a more elegant way to tell, but here's how I would do it:
To see what devices are currently in use, do:```
df -h
```…this will give a result like the following:```
Filesystem            Size  Used Avail Use% Mounted on
udev                   32G     0   32G   0% /dev
tmpfs                 6.3G  9.8M  6.3G   1% /run
/dev/sda3              29G  7.4G   20G  28% /
tmpfs                  32G   11M   32G   1% /dev/shm
tmpfs                 5.0M  4.0K  5.0M   1% /run/lock
tmpfs                  32G     0   32G   0% /sys/fs/cgroup
tmpfs                  32G  4.0K   32G   1% /tmp
/dev/sda1             197M  3.6M  194M   2% /boot/efi
/dev/sdb1             918G  504G  367G  58% /mnt/duckhook
cgmfs                 100K     0  100K   0% /run/cgmanager/fs
tmpfs                 6.3G   52K  6.3G   1% /run/user/1000
/home/duckhook/.Private  918G  504G  367G  58% /home/duckhook/Private
```…ignore all lines except the /dev/sd?? ones. These show you what partitions are in use for your current session. *You must keep these partitions!* In my case, these critical partitions are: sda3 sda1 & sdb1. Now do:```
sudo blkid
```…which, in my case, yields something like:```
/dev/sda1: UUID="20C6-7C63" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="8a6b5b52-d62e-4616-8b38-62f3302012f5"
/dev/sda2: UUID="3008055e-bfa5-4166-8647-32c667554447" TYPE="ext4" PARTUUID="a8eca958-62fe-4f9a-a1c6-4b5750398c40"
/dev/sda3: UUID="88c3faab-55ed-4652-9f8f-2b32f61c782b" TYPE="ext4" PARTUUID="1a5d342f-3d3a-41af-bf2a-c0a28804a010"
/dev/sdb1: LABEL="home" UUID="8fd03e8a-28dd-4e31-9423-62ea729d1baf" TYPE="ext4" PARTUUID="98623751-141f-486a-9ba1-122c4d7c2350"
/dev/sdb2: UUID="EbDoDp-1fvD-OD11-hmqW-tI13-G1VC-r2owfg" TYPE="LVM2_member" PARTUUID="f89646ea-a516-4a72-9e24-1ad01588654c"
/dev/sdc1: UUID="10df1108-f241-49c1-84e6-ce43e7af9845" TYPE="ext4" PARTUUID="25b0298e-8f90-473d-a18b-4f3ddf80f6d3"
/dev/sdc2: UUID="53015697-4774-4fa6-83e7-47f876731999" TYPE="ext4" PARTUUID="805a8759-4181-4c5e-b181-36da829ee305"
/dev/sdd1: UUID="b0051304-b95b-44fd-9d74-678e79590e64" TYPE="swap" PARTUUID="7203dcc3-0749-41b4-99c1-beb2b4336ef3"
/dev/mapper/Xen-Root: UUID="196b4580-d93c-46fc-a3f0-eede64d277ec" TYPE="ext4"
```…any device that is not on your first list is not being used in the current session. Example: /dev/sda2 does not show up in the df -h command. It is a *candidate* for deletion. However whether you delete it or not depends on the next step. Also, If you have a partition that you mount only sporadically, but wish to keep for old data, then of course you mustn't delete it. Only you know the layout of your partitioning scheme.

****IMPORTANT STEP****

Fire up your other OSes and do:```
cat /etc/fstab
```All of the partitions that those OSes use will be listed in the fstab file. If these correspond to your detective work from earlier, then you will have double confirmation and you can go ahead and delete them. It is very important to do this double check. Once deleted, consider a partition toast and unrecoverable. You only get one chance to do it right, so make sure that you double check and are absolutely sure.

Make a note of the actual UUIDs that you wish to delete (*not* the /dev/sd?? because these may change in the next step).

Boot into a LiveDVD/USB and use *gparted* to delete the partitions that you no longer want.

*****WARNING*****

If you fail to back up your data before performing the above, then you must consider yourself the author of your own misery should everything go south. When goofing around with partitions in this way, proven restorable backups are the only thing standing between you and the outer darkness.

---

### Post by Habitual on 2016-09-15
boot into your preferred OS.
Open a terminal and issue:
```
sudo parted -l | grep Disk
```

First disk in the system is usually designated sd**a**
First partition on sd**a** would be sd**a**1
Second disk would be sd**b**
First partition on sd**b** would be sd**b**1

First non-native Drives including my storage 
I get sd**c**
It looks like this:
```
sudo parted -l | grep Disk
Disk /dev/sda: 1000GB
Disk /dev/sdb: 1000GB
Disk /dev/sdc: 3001GB
```
in terminal of your preferred booted OS, issue:
```
df -hT /
``` and this likely is going resemble this
```
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda1      ext4   23G  7.5G   15G  35% /

```

If yours comes back as sda - That's the one you want to keep.
Reason we don't assume sda?
You could have booted a custom menu entry to get KDE. And this booted KDE does not have to be on sda[123]
So we're gonna look.

Let us know, so we can independently verify the results using other c-line utilities.
(I might have forgot "something")

---

### Post by DuckHook on 2016-09-15
> **Habitual said:**
> &#8230;```
df -hT /
```&#8230;I believe that this will only return root. If OP's, say, /home is on a separate partition, this won't be shown and s/he could inadvertently delete it.

@mdsmedia

It's best to look at your whole directory structure using the plain command:```
df -h
```&#8230;then double-check by comparing those entries with your fstab file. They should match entry for entry. And as both Habitual and I have stated, do not rely on the sda&#8230;sdx designations. They can change when you run a LiveUSB session. Always look at the UUIDs because each is unique.

---

### Post by mdsmedia on 2016-09-16
Thanks for all the responses.

I did the silly thing, went to Gparted?, in Kubuntu, looked at what I thought was probably Kubuntu, deleted the rest (except Win7) and rebooted, to find that Grub wasn't working, because Ultimate Edition was the last Linux installed and it held Grub definitions. so reinstalled UE, which restored Grub.

It worked, but WASN'T the recommended route! I knew the risks, but having installed and resinstalled and mucked up many times, I was able to get myself out of it pretty well. All is OK. I had wanted to remove an OLD UE edition and the more current one I'd installed recently. Neither of them held any data that I wanted to keep. The only real risk was that I'd delete the wrong partition. Thankfully my "guesses" were correct :).

df -h gives:

```
mdsmedia@mdsmedia-H81M-DS2:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            2.0G     0  2.0G   0% /dev
tmpfs           394M  6.4M  387M   2% /run
/dev/sda8        92G  5.9G   81G   7% /
tmpfs           2.0G   20M  2.0G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           2.0G     0  2.0G   0% /sys/fs/cgroup
/dev/sda6       9.1G  197M  8.4G   3% /boot
/dev/sda7       184G  6.0G  168G   4% /home
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           394M   12K  394M   1% /run/user/1000
```

...which was exactly what I "guessed" was Kubuntu :)

---

### Post by Habitual on 2016-09-16
@DuckHook
Thanks. :)

@mdsmedia
beginner's luck !?

---

### Post by DuckHook on 2016-09-16
> **Habitual said:**
> &#8230;beginner's luck !?&#8230;sometimes, luck is even better than knowledge. \\:D/

@ mdsmedia:

*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

### Post by ltrtiger2 on 2016-09-16
> **DuckHook said:**
> _***]I believe that this will only return root. If OP's, say, /home is on a separate partition, this won't be shown and s/he could inadvertently delete it.***_.

I can emphatically attest to this! Painful lesson.

---

