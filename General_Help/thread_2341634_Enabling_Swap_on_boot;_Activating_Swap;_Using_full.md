---
title: "Enabling Swap on boot; Activating Swap; Using full Swap of 7.5GB; Used Swap FAQ"
date: 2016-10-30
forum: General Help
---

### Post by SciGuy1872 on 2016-10-30
Hi, all.  Like the title says, I read the Swap FAQ [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) but still had some questions.  The swap is listed as:

```

anthony@anthony-Aspire-X1200:~$ sudo fdisk -l

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 286722047 286720000 136.7G 83 Linux
/dev/sda2       286724096 302350335  15626240   7.5G 82 Linux swap / Solaris

```

```

anthony@anthony-Aspire-X1200:~$ cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=a6a40043-b414-4fd0-bd4b-20b77ac7a730 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ff80f47a-6621-4287-9f7d-fb2c9509d48c none            swap    sw  


```

> **Enabling a swap partition**

[COLOR=#333333][FONT=Ubuntu]In case you do have a swap partition, there are several ways of enabling it.[/FONT][/COLOR]

[LIST]
[*=left]Use the following commandcat /etc/fstab
[*=left]Ensure that there is a line link below. This enables swap on boot./dev/hda8       none            swap    sw              0       0
[*=left]Then disable all swap, recreate it, then re-enable it with the following commands.sudo swapoff -a
sudo /sbin/mkswap /dev/hda8
sudo swapon -a
[/LIST]


For "Enabling The Swap" section, the document says there are several methods and then lists three of those--are they listing three different ways, or are they meant to be used together?  
In the FAQ, the result of fdisk -l is used for step two, which I have done:

```

anthony@anthony-Aspire-X1200:~$ /dev/sda2       none            swap    sw              0       0bash: /dev/sda2: Permission denied

anthony@anthony-Aspire-X1200:~$ sudo /dev/sda2       none            swap    sw              0       0
sudo: /dev/sda2: command not found

anthony@anthony-Aspire-X1200:~$ su
Password: 
su: Authentication failure

```

Thus, I don't know the su password (I only have one password, but I enter it, and the system tells me that there is an Authentication failure).  Shouldn't the sudo password allow me the same privilege as the su password?  The FAQ says that this step enables the swap on boot, which I need.

For step three--I have already created a partition (I used the Live DVD, then GParted, then rebooted)--would these effectively delete the partition I have created?

Also, I ran a lot of memory-taxing programs and the Swap that I turned on in the Disks application (The Swap was reported as inactive before I activated the Swap in Disks by clicking the swap partition, then clicking the triangle, or play button) only used 5MiB--how do I get the full 7.5GiB used?  I did this to make mainly Chromium open faster than the 15 seconds it required.

Thanks for your help,
                      Anthony

---

### Post by Bucky Ball on 2016-10-30
You need to open this file

```
sudo nano /etc/fstab
```

Then do your thing. Add your line. You don't enter those lines at a command line. They are not commands.

I strongly advise to make a back up of that file before you do it as you don't seem too familiar with this. If you screw up you have a copy of the original and can start again. :)

```
sudo cp /etc/fstab /etc/fstab.bak
```

---

### Post by Bucky Ball on 2016-10-30
Sorry, edited my post, but just to clarify, that's

```
sudo nano /etc/fstab
```

I left out the 'nano' originally. :| ;)

---

### Post by ajgreeny on 2016-10-30
Just as a tip for checking the fstab file, after editing and saving /etc/fstab file you can, and I recommend you to do so, run command ```
sudo mount -a
```
If any errors are shown there is something wrong in the file which you need to correct, but if that command goes straight back to the prompt, everything is OK.

Incidentally, you should always use UUIDs in the fstab file, as yours already seems to do, and not use /dev/sdx# nomenclature which can change if more disks are attached; UUIDs are immutable unless you change them manually (not normally necessary) or format a partition which gives it a new UUID.

You can find the UUIDs of all partitions with command ```
sudo blkid -c /dev/null
```

---

### Post by SciGuy1872 on 2016-10-30
Thanks for all the info.  I see that there are two UUID's and two drive locations reported for the swap:

```
anthony@anthony-Aspire-X1200:~$ cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=a6a40043-b414-4fd0-bd4b-20b77ac7a730 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ff80f47a-6621-4287-9f7d-fb2c9509d48c none            swap    sw              0       0

```

```
anthony@anthony-Aspire-X1200:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="a6a40043-b414-4fd0-bd4b-20b77ac7a730" TYPE="ext4" PARTUUID="28fb42dc-01"
/dev/sda2: LABEL="swap" UUID="4b59264b-2cc4-4205-8366-20f727e70689" TYPE="swap" PARTUUID="28fb42dc-02"

```


I'm pretty sure I should go with the blkid entry.  When editing the fstab what should I replace with at the third hash?  
Thanks for all the help again,
                                           Anthony

---

### Post by SciGuy1872 on 2016-10-30
I figure I just need to replace /dev/sda5 with /dev/sda2 and also replace the UUID with 4b592* in the fstab file--just wanted to make sure, though.
Thanks,
        Anthony

---

### Post by Bucky Ball on 2016-10-30
```
# swap was on /dev/sda5 during installation
UUID=4b59264b-2cc4-4205-8366-20f727e70689 none            swap    sw              0       0
```

That's all you need. You could have this if you want.

```
# My uncle is an elephant.
UUID=4b59264b-2cc4-4205-8366-20f727e70689 none            swap    sw              0       0
```

In other words, anything that comes after '#' is a comment only, not read, so you can change that if you want. Best to keep it uniform, though, so you do know what's where, so if your swap is sda2, change to that. :)

---

