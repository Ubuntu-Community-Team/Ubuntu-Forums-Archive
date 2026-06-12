---
title: "Urgent problem... GRUB error 22"
date: 2007-11-26
forum: General Help
---

### Post by TV-VCR on 2007-11-26
Well, I completely deleted all the partitions from my ubuntu drive. Note that ubuntu and my windows Vista were on separate HDDs. I deleted all the partitions on the Ubuntu HDD from the ubuntu live CD.

So, I thought I had successfully removed ubuntu... I restart, and the grub starts to load and tells me GRUB error 22. I cannot boot into windows vista. How do I boot into Vista?

This is the only computer I have and the ubuntu liveCD is the only other "OS" I can "use"

Someone also told me about trying "sudo dd if=/dev/zero of=/dev/hda bs=512 count=1" but it seemed a little suspicious, and also he told me it would clear the whole MBR. if it did that I would not be able to boot into Vista. :(

How can I resolve this without damaging my data?

---

### Post by TV-VCR on 2007-11-26
I should also mention, I cannot use the vista DVD to repair my install currently.


Oh... question... does the Gentoo Linux install CD have GRUB on it? If I installed it to the same drive as ubuntu was on, might that fix the problem?

---

### Post by meierfra on 2007-11-26
Check out the link:

[http://ubuntuforums.org/showthread.php?t=616540&highlight=fixmbr]("http://ubuntuforums.org/showthread.php?t=616540&highlight=fixmbr")

---

### Post by TV-VCR on 2007-11-26
> **meierfra said:**
> Check out the link:

[http://ubuntuforums.org/showthread.php?t=616540&highlight=fixmbr]("http://ubuntuforums.org/showthread.php?t=616540&highlight=fixmbr")

Which should I download? The LiveCD ubuntu OS is my only available OS right now.
[http://sgd.howto-linux.de/download/binaries/sgd/cdrom/](http://sgd.howto-linux.de/download/binaries/sgd/cdrom/)

---

### Post by meierfra on 2007-11-26
Actually you can also fix your problem   from the Ubuntu LiveCD:

Open a terminal (Applications->Accessories->Terminal)

```

sudo apt-get install ms-sys
sudo ms-sys -m /dev/sda
```

This assumes that the  Windows drive is /dev/sda. If you don't know the Windows drive name,  you can find out by typing "sudo fdisk -l"

If this didn't  not work pick  sgd_0.9670.iso
 (if you have a slow internet connection you might  choose sgd_0.9670.iso.gz. Butyou will have to extract it before you burn it)

---

### Post by TV-VCR on 2007-11-26
meierfra, what does that command do specifically (the first one)?

Thanks.

---

### Post by meierfra on 2007-11-26
The first one installs the program "ms-sys". The second one uses "ms-sys" to rewrite your MBR. After you install "ms-sys" you can type "man ms-sys" to get some information about it)

---

### Post by meierfra on 2007-11-26
Opps:  The second command also need "sudo"

---

### Post by TV-VCR on 2007-11-26
So basically what it does is, remove the GRUB entry in MBR and replace it with** Vista's** NTLDR?

---

### Post by TV-VCR on 2007-11-26
Just read that doing that command can destroy vista!! Is this true? :(

---

### Post by meierfra on 2007-11-26
> So basically what it does is, remove the GRUB entry in MBR and replace it with** Vista's** NTLDR?

Not with the NTLDR. (The NTDLR sits in the Vistas partition.)  It just replaces it with a Windows type   MBR.   (A windows MBR is very simple, it justs hands  control to the  boot sector of the active  partition, that is the one with the boot flag)

---

### Post by meierfra on 2007-11-26
> Just read that doing that command can destroy vista!!

Where did you read that? It only rewrites the MBR.  It won't even touch the vista partition and so cannot distroy vista. (But I have to admit that I only tested it with Windows XP)

---

### Post by TV-VCR on 2007-11-26
Well thanks for your help meierfra...

But it can't find the package!! "E: Couldn't find package ms-sys"

:(

---

### Post by meierfra on 2007-11-26
Open synaptics and enable all the repositories.

---

### Post by TV-VCR on 2007-11-26
> **meierfra said:**
> Open synaptics and enable all the repositories.

Where is that and how do I do that?

---

### Post by meierfra on 2007-11-26
Just hang on for a minute. I just started the Live CD on my other computer to check out things. Why don't you download Super Grub in the mean time. Even if your don't use Super Grub now, it might come in handy later.

---

### Post by meierfra on 2007-11-26
To enable the "universe" repositories:

Go to Systems-> Adminstration->Software Sources

Click on the Box next to "Community-maintained Open Source Software (universe)"

Click on Close (twice)


Next open a terminal and  type
```
sudo apt-get update
sudo apt-get install ms-sys
sudo ms-sys -m /dev/sda
```

---

### Post by TV-VCR on 2007-11-27
> **meierfra said:**
> To enable the "universe" repositories:

Go to Systems-> Adminstration->Software Sources

Click on the Box next to "Community-maintained Open Source Software (universe)"

Click on Close (twice)


Next open a terminal and  type
```
sudo apt-get update
sudo apt-get install ms-sys
sudo ms-sys -m /dev/sda
```

It worked, I'm back in windows.

Thanks. :popcorn:

---

