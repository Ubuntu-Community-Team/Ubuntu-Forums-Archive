---
title: "can I use Ubuntu to fix Windows?"
date: 2008-04-26
forum: General Help
---

### Post by metalf8801 on 2008-04-26
Is there anyway for me to scan my Windows partition for viruses from my Ubuntu partition? 

Thank you 
Dan

---

### Post by _sAm_ on 2008-04-26
> **metalf8801 said:**
> Is there anyway for me to scan my Windows partition for viruses from my Ubuntu partition? 

Thank you 
Dan

I guess you could install ClamAV on Ubuntu([http://www.clamav.net/](http://www.clamav.net/)), then mount the windows drives and scan them. You would need to activate the ntfs drive.

---

### Post by grannyw on 2008-04-26
> **metalf8801 said:**
> Is there anyway for me to scan my Windows partition for viruses from my Ubuntu partition? 

Thank you 
Dan

ofcause just install antivirus(i use avast!),mount the partition you want to scan and scan

---

### Post by MobiusNZ on 2008-04-26
You'll need to do two things:

1st) make sure you can access your windows file system from linux in read/write mode. It's fairly easy - google has millions of pages on it, or I can spell it out to you if you like.

2nd) Install clamav. It's used for scanning mail that gets delivered to all operating systems, so it should have all the mojo for doing a local scan of your windows folders. I haven't actually tried doing that yet though.

---

### Post by metalf8801 on 2008-04-27
> **MobiusNZ said:**
> You'll need to do two things:

1st) make sure you can access your windows file system from linux in read/write mode. It's fairly easy - google has millions of pages on it, or I can spell it out to you if you like.

2nd) Install clamav. It's used for scanning mail that gets delivered to all operating systems, so it should have all the mojo for doing a local scan of your windows folders. I haven't actually tried doing that yet though.

Can't I just do number one with a swap partition?

---

### Post by MobiusNZ on 2008-04-27
> **metalf8801 said:**
> Can't I just do number one with a swap partition?

Ah, no. I think you're missunderstanding what a swap partition is (or I'm missunderstanding your question). A swap partition is a partition reserved for *nix virtual memory (in contrast, windows uses a swap file)

---

### Post by ubockto on 2008-04-27
> **metalf8801 said:**
> Is there anyway for me to scan my Windows partition for viruses from my Ubuntu partition? 

Thank you 
Dan

Depends, if its windows vista, I would doubt it, since it uses a bit more secure way of locking up the files so noone apart from the user can use them, but dont quote me on that, I maybe wrong of course....btw, dont you trust any virus scanner on your windows installation? Or dont you have one?

---

### Post by ubockto on 2008-04-27
> **metalf8801 said:**
> Is there anyway for me to scan my Windows partition for viruses from my Ubuntu partition? 

Thank you 
Dan

Depends, if its windows vista, I would doubt it, since it uses a bit more secure way of locking up the files so noone apart from the user can use them, but dont quote me on that, I maybe wrong of course....btw, dont you trust any virus scanner on your windows installation? Or dont you have one?

---

### Post by metalf8801 on 2008-04-28
sorry somehow posted the same thing twice see below

---

### Post by metalf8801 on 2008-04-28
> **MobiusNZ said:**
> Ah, no. I think you're missunderstanding what a swap partition is (or I'm missunderstanding your question). A swap partition is a partition reserved for *nix virtual memory (in contrast, windows uses a swap file)

I guess I thought a swap partition was something else.  Thanks for you telling me what a swap partition is.  

Could you please spell it out how to access your windows file system from Linux?  

Thank you 
Dan

---

### Post by MobiusNZ on 2008-04-30
First up, figure out which device(s) your windows partitions are on. Usually it will be along the lines of /dev/sda1, if your windows drive is the first partition. If not, or if you're not sure, open up a terminal and run

```
sudo fdisk -l /dev/sda
```

If you have more than one harddrive, you might need to also run sudo fdisk -l /dev/sdb, etc (just change the last letter to the next one in the alphabet).

You should get output that is similar to mine:
```

al@tucker:~$ sudo fdisk -l /dev/sda
[sudo] password for al:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8a87ed5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7724    62042998+   7 HPFS/NTFS
/dev/sda2           13840       14593     6056505    7 HPFS/NTFS
/dev/sda3            7725       13583    47062417+  83  Linux
/dev/sda4           13584       13839     2056320    5  Extended
/dev/sda5           13584       13839     2056288+  82  Linux swap / Solaris
```

Here I have two windows partitions, and 2 linux partitions - one of which is in an extended partition. (If you don't know what these terms mean, google a basic partitions guide)

On my laptop, only the first partition is useful - the second is the factory recovery drive. You should get the idea of what to do though.

In your terminal create a folder or folder system to mount your windows drives in. Usually if I have only one drive I want, I just create /windows, for more I'd create /windows/c, /windows/d etc. In your terminal, do

```
sudo mkdir -p /windows/c
```
(feel free to layout as you like, just adjust the rest of the instructions to suit).

Once you've got your folders ready, run

```
sudo mount -t ntfs /dev/sda1 /windows/c
```

(adjust the /dev/sdxx and /windows/xx to suit. You will need to run it once for each partition you want to add)

Now you can open up your normal file browser and browse to your windows directories.

To make this permanent (ie so it's there next time you reboot), open up your terminal again.

Take a backup of your fstab file just in case you bugger up (your fstab file is really REALLY important to have right).

```
sudo cp /etc/fstab /etc/fstab.backup
```

Now edit your fstab file

```
sudo nano -w /etc/fstab
```

Move your cursor down to the bottom, and add a line that looks similar to this (adjust it to suit your needs of course). It should be all on one line. Again, repeat and adjust the lines for each partition you're adding.

```
/dev/sda1    /windows/c     ntfs   defaults,auto  0  0
```

Double-check it to make sure it is correct, then type CTRL-X to save and exit (say yes to saving and press enter to overwrite the file).

Check that everything is ok with your fstab by running

```
sudo mount -a
```

If it gives you no errors you should be fine.

---

