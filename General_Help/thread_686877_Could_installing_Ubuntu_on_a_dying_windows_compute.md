---
title: "Could installing Ubuntu on a dying windows computer save the files?"
date: 2008-02-03
forum: General Help
---

### Post by TJF on 2008-02-03
I have a computer with windows XP installed on it that just suddenly got thousands(Ok, I don't know the exact number) of viruses. I was wondering if, if I installed Ubuntu on a separate partitions, could I extend the partition over all of my family's files? We have some really important pictures and documents that need saving. And If that was possible, could these files still be readable on another windows XP/Vista computer, and the ubutnu computer? Also, is there* any* chance of losing **any** of the files?

---

### Post by HermanAB on 2008-02-03
Use BartPE or a live Linux CD to copy the data off the machine:
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

Cheers,

Herman

---

### Post by TJF on 2008-02-03
What exactly does it do? Looks like you could just boot windows/linux off of a live cd...  
How would that save the files?

Also, I have a ubuntu live cd.

---

### Post by The B'man on 2008-02-03
If your Windows installation is dying, then you should reinstall the OS on the partition after backing up your important files and formatting the partition.

It's not possible to set up another partition that encompasses all or part of the existing one - the table of contents (TOC) for the existing partition wouldn't be there even if it was possible. The solutions I can see:

* Using a LiveCD, you can boot Ubuntu and access the files on the Windows partition. This will allow you to copy them to another partition, back them up on DVD or move them to another computer on the network.

* Again with the LiveCD, you can install Ubuntu in its own partition, either by using unpartitioned space or by resizing the Windows partition to give you the space you need. Then you can access the Windows files from Ubuntu and move them to the Ubuntu partition. From there you'd typically scan them with antivirus software like ClamAV, format the Windows partition and reinstall, before moving the files back.

On Kubuntu, you can access the Windows drive by opening Konqueror and going to Go > Storage Media. I forget how it works in Ubuntu, but I *think* it'll be available off the bat in the Places menu. If not, it may be in [/media](file:///media)

---

### Post by gpilkay on 2008-02-03
I agree that you can use the Ubuntu Live-CD, but you may have trouble burning a DVD if Ubuntu is running off that drive.  Another alternative is, once Ubuntu has started, go to places> Computer and you should see your Hard Drive with Windows (it will be the NFTS one).

From there, a USB key makes copying the files easy.  You can then disinfect them on a separate machine while you re-install Windows.  This tactic was one I just used a few weeks ago, in a very similar situation to yours.

From there, I recommend, if you don't have paid subscriptions, to go to free.grisoft.com and try their free anti-virus and anti-spyware.  I use both in XP and they work very well (have both removed active infections for me many times).  

I myself have two hard drives, one with XP and one with Ubuntu (Ubuntu is the Master drive so no partitioning is required), so I can do redundant backups on each, just in case.  Though i must admit, XP has had all the troubles thus far...

---

### Post by TJF on 2008-02-03
Genius!.. I'll try to convince my parents to let me do that.. oh, and do you know of any internet services that would allow us to up-load a 15 gig file, possibly full of viruses?... ._.

---

### Post by manimal347 on 2008-02-03
> **TJF said:**
> Genius!.. I'll try to convince my parents to let me do that.. oh, and do you know of any internet services that would allow us to up-load a 15 gig file, possibly full of viruses?... ._.

You can just run the antivirus program under Linux for the scan. F-Prot for Linux is free, as is the open Source ClamAV.

[http://www.f-prot.com/download/home_user/download_fplinux.html](http://www.f-prot.com/download/home_user/download_fplinux.html)

---

### Post by gpilkay on 2008-02-04
Also, keep in mind that AVG does not come with its own firewall.  I use comodo and it seems to work fine, and also combines in some system-wide HIPS functions, though they are kind of annoying and not recommended for machines without a lot of memory.  [www.comodo.com](www.comodo.com)

Don't forget to un-install your old anti-virus before adding in a new one in XP!  Norton's in particular is a pain, I had to go through shutting down processes and deleting files manually to get rid of Norton 2005's trial...

---

