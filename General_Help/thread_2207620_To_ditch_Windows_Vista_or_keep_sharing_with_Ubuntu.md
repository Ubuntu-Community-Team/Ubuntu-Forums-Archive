---
title: "To ditch Windows Vista or keep sharing with Ubuntu?"
date: 2014-02-24
forum: General Help
---

### Post by spenbeck on 2014-02-24
Hi everyone, I have 2 compaq presario cq50 laptops installed with vista and ubuntu 12.04. I use one regularly and recently it has run out of space on the hard disk it shares with windows.

I think I have 2 options: 1 to re-install ubuntu 12.04 and select more space away from vista, or 2 install ubuntu 12.04 on it's own and ditch vista (which I would prefer).

The problem is at the moment I have to have vista installed as 12.04 uses the driver in vista to make the wireless card work. I can not find any driver to work with the original wireless card and ubuntu.

Another option would be to install a new wireless card which ubuntu could use with out vista.

I mentioned that I have 2 identical laptops, so I could experiment on 1 without too much worry. The exact models are cq50-110em and the wireless card is an Atheros.

Your views and information is welcome.

best regards, Ian

---

### Post by sudodus on 2014-02-24
> **spenbeck said:**
> Hi everyone, I have 2 compaq presario cq50 laptops installed with vista and ubuntu 12.04. I use one regularly and recently it has run out of space on the hard disk it shares with windows.

I think I have 2 options: 1 to re-install ubuntu 12.04 and select more space away from vista, or 2 install ubuntu 12.04 on it's own and ditch vista (which I would prefer).

Backup first because editing partitions is risky!

You can use ***gparted*** to shrink the vista partition, and then grow the ubuntu partition into the unallocated space created (if the partitions are adjacent). But you need to repair the bootloader, if you move the head end of the ubuntu partition ([described here]("https://help.ubuntu.com/community/Grub2/Installing")).
> 
The problem is at the moment I have to have vista installed as 12.04 uses the driver in vista to make the wireless card work. I can not find any driver to work with the original wireless card and ubuntu.

Another option would be to install a new wireless card which ubuntu could use with out vista.

I mentioned that I have 2 identical laptops, so I could experiment on 1 without too much worry. The exact models are cq50-110em and the wireless card is an Atheros.

Your views and information is welcome.

best regards, Ian

It could be a good idea to get a wireless card or USB stick that works out of the box with Ubuntu. Don't spend too much time to trying to get the existing wifi card work with linux.

---

### Post by Impavidus on 2014-02-24
People say using gparted to resize Windows partitions doesn't always work. I would use the Windows tools for that part, and only use gparted for expanding the Ubuntu partition. And make sure to have backups, of course.

> The problem is at the moment I have to have vista installed as 12.04 uses the driver in vista to make the wireless card work.I didn't know that was actually possible, using a Windows driver to get your hardware working under Linux. I have an Atheros myself (lspci gives me *24:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)*), which worked out of the box. They usually work fine, but maybe not always.

---

### Post by wildmanne39 on 2014-02-24
Atheros cards work about 98 percent of the time, I help people with wireless issues and it usually takes a little tweaking that is all.

Your ubuntu install does not use your windows wireless driver unless you installed ubuntu using wubi.

---

### Post by spenbeck on 2014-02-24
> **Impavidus said:**
> People say using gparted to resize Windows partitions doesn't always work. I would use the Windows tools for that part, and only use gparted for expanding the Ubuntu partition. And make sure to have backups, of course.

I didn't know that was actually possible, using a Windows driver to get your hardware working under Linux. I have an Atheros myself (lspci gives me *24:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)*), which worked out of the box. They usually work fine, but maybe not always.

Could you recommend a tool/software for me to reduce the size of windows, then I will have a go with gparted to increase the size of the ubuntu partition.

best regards, Ian

---

### Post by Impavidus on 2014-02-24
I think there must be a tool build into Windows. I don't know what it's called. I haven't really used Windows the past 7 years.

---

### Post by sudodus on 2014-02-24
I think it helps to ***defragment*** the Windows partition before shrinking it (but some people say it is waste of time). If you don't find a Windows tool, you can use ***gparted***. I have used it successfully several times to shrink Windows partitions.

Anyway, avoid creating dynamic partitions, because they cannot be managed by linux.

---

### Post by dragonfly41 on 2014-02-24
Read recent tips here ...  [http://ubuntuforums.org/showthread.php?t=2205653](http://ubuntuforums.org/showthread.php?t=2205653)

[www.partition-tool.com](www.partition-tool.com) is a windows tool.

and don't shrink partition too much so that Window doesn't work.

---

### Post by Xanthius on 2014-02-24
If you do this, it can go both ways. 

The software found in windows to shrink your HDD is available from Vista and above and found in: start -> control panel -> System -> Administrative Tools -> Computer Management and finally the tab "Disk Management".
Right click the partition and select properties from there you would be able to shrink your volume down to size.

But as stated above, it is **very dangerous**. Many times it works like a charm but it's that *one* time that matters.
From my perspective it is **not wise** to use **external tools** and better to use the *build-in one in Windows*.
Some might argue its doesn't matter to defrag your drive before hand, but even if it would slim down the chance by 1% I'd still do it.

Now here comes the tricky part, if you did use external tools and it did go wrong you might find yourself in a lot of trouble.
The symptoms are simple, you want to re-install Windows for whatever reason and it does not find your drive.
The -only- solution I came across was this:
[http://www.fdisk.com/fdisk/HardDrive.htm](http://www.fdisk.com/fdisk/HardDrive.htm)

Yes, I've worked for Dell and I've had quite a few "IT specialists" who thought they could just "shrink" it.
The script basically clears the MBR record of the HDD, while Linux could do the same it did not have the same effect as this script.

I personally didn't experience this issue by using the Disk management, the worst was that Windows couldnt boot up anymore.
This does however happens allot with 3th party software, like partition magic.

Trade carefully.

---

### Post by Mark Phelps on 2014-02-24
Having shrunk Windows many times myself, I would STRONGLY suggest you use ONLY the Vista Disk Management tool to do the shrinkage.  Yes, it's primitive and won't let you shrink much,  but in return, it will not damage the Windows filesystem.  Other tools provide a LOT more flexibility, but they do so at the risk of corrupting the Windows filesystem.  And once that happens, you can't boot back into Windows to fix it.

A second choice, which is also free, is to download the Minitool Partition Wizard Boot CD, burn that to a CD, and use that.  This is a Windows partitioning tool strongly recommended by the Windows 7 forums and the Windows 8 forums.

---

### Post by spenbeck on 2014-02-25
> **Xanthius said:**
> If you do this, it can go both ways. 

The software found in windows to shrink your HDD is available from Vista and above and found in: start -> control panel -> System -> Administrative Tools -> Computer Management and finally the tab "Disk Management".
Right click the partition and select properties from there you would be able to shrink your volume down to size.

But as stated above, it is **very dangerous**. Many times it works like a charm but it's that *one* time that matters.
From my perspective it is **not wise** to use **external tools** and better to use the *build-in one in Windows*.
Some might argue its doesn't matter to defrag your drive before hand, but even if it would slim down the chance by 1% I'd still do it.

Now here comes the tricky part, if you did use external tools and it did go wrong you might find yourself in a lot of trouble.
The symptoms are simple, you want to re-install Windows for whatever reason and it does not find your drive.
The -only- solution I came across was this:
[http://www.fdisk.com/fdisk/HardDrive.htm](http://www.fdisk.com/fdisk/HardDrive.htm)

Yes, I've worked for Dell and I've had quite a few "IT specialists" who thought they could just "shrink" it.
The script basically clears the MBR record of the HDD, while Linux could do the same it did not have the same effect as this script.

I personally didn't experience this issue by using the Disk management, the worst was that Windows couldnt boot up anymore.
This does however happens allot with 3th party software, like partition magic.

Trade carefully.

As a test I have just tried to shrink the windows partition using the windows disk management shrink tool on my spare machine and it came back 'zero'. It wouldn't let me.

The laptop has a 250 gb hard disk - 177 gb for windows (c drive) and 9.32 gb for presario_rp. The rest is taken up by ubuntu 12.04. Stumpted at the first go!

The alternative would be to install a new wireless pci card which is known to work and install 12.04 from scratch again. If installing ubuntu only, what happens to the presario_rp partition - does the laptop need it to run? I seem to remember having install problems when I originally tried to install 12.04 only.

Is there a later wireless card which will reliably work with 12.04. I think the my card is a full length PCI card. Could I fit a half length card such as the Atheros AR9285 AR5B95 802.11BGN PCI Express Half Mini WLAN card?

P.S. I mentioned previously that I thought that ubuntu was using the windows driver to operate the wireless card. All I is know that if wireless is switched off in ubuntu I have to boot vista and turn it back on in there.

---

