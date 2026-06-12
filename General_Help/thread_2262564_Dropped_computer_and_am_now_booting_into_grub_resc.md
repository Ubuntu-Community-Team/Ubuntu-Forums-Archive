---
title: "Dropped computer and am now booting into grub rescue. How screwed am I?"
date: 2015-01-25
forum: General Help
---

### Post by falsedichotomies on 2015-01-25
So... as the title says, my laptop was sitting on the table and I tripped over its cord, causing it come crashing down.

It immediately shut off and now when I tried to reboot it I hit the grub rescue> screen.

I've attached a picture of what happens when I use the ls command. Particularly noticeable is that a ls for (hd0,gpt2)/ yields a random string of characters.

What should I do? Am I screwed? Is there any way to recover at least the files that were on the hard-drive?

---

### Post by phidia on 2015-01-26
It depends if you can mount/access the partition(s) then you may recover your files. There are several tools to do that available: [systemrescue]("http://www.sysresccd.org/SystemRescueCd_Homepage") or select from one of the methods [here]("http://www.techrepublic.com/blog/10-things/10-linux-rescue-tools-for-recovering-linux-windows-or-mac-machines/").
Good luck

---

### Post by coldraven on 2015-01-26
> Is there any way to recover at least the files that were on the hard-drive?
To start with you could buy a new drive and install a working OS on it. (about £30 for a HDD or get a SSD for £50, the SSD will not get damaged if you drop your laptop again)
Also buy a cheap USB enclosure for your old drive so that you can try to extract your files from it. (about £5)
Something like this: 
[http://www.ebay.co.uk/itm/BLACK-2-5-SATA-to-USB-HARD-DRIVE-CADDY-HDD-CASE-ENCLOSURE-/310792272277?pt=UK_Collectables_HardDriveEnclosures_RL&hash=item485ca9b995](http://www.ebay.co.uk/itm/BLACK-2-5-SATA-to-USB-HARD-DRIVE-CADDY-HDD-CASE-ENCLOSURE-/310792272277?pt=UK_Collectables_HardDriveEnclosures_RL&hash=item485ca9b995)

---

