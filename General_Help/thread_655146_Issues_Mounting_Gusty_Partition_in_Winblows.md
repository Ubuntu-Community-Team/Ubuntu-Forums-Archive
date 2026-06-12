---
title: "Issues Mounting Gusty Partition in Winblows"
date: 2008-01-01
forum: General Help
---

### Post by Hachi-Roku on 2008-01-01
Hey all.

 Ive done some forum searching and not turned up an answer yet...

I hate to say... but i need to run windows sometimes. So i like to mount my Linux partition in windows  ...Ive been using this ;

[http://www.fs-driver.org/extendeddl.html](http://www.fs-driver.org/extendeddl.html) 

This has worked for all previous ubuntu versions but has ceased working since upgrading to gusty.

Ive re ran it since, giving the linux partition a drive letter in windows without success.
The linux partition is Ext2 orExt3, can't remember. But both should be fine, and have been fine in the past.

When i try and open the 'drive' in windows i get a message "drive 'x' is not formatted".

Am i missing a permission in gusty or something???

cheers.

---

### Post by xyphur on 2008-01-01
I went to the fs-driver.org site, and looked for something that might have answers to common issues... and what do you know, I found a Troubleshooting section!

[http://www.fs-driver.org/troubleshoot.html](http://www.fs-driver.org/troubleshoot.html)

The problem you're having is the first one on the page. Download the diagnostic tool using the link, and point it at the drive letter in question. It should help you figure out why this is happening.

---

### Post by MrFSL on 2008-01-01
Interesting... you would think that this tool would be part of their distribution. Odd. - "We have this diagnostic tool that can give you ideas of what is going on if you are unsuccessful using out tool. - Of course it would probably be easier just to include this functionality in our driver but we decided that this would just be too easy ;)" WOW!

---

### Post by dlegend on 2008-01-01
Seems like you've got your answer --- I can confirm that fsdriver does pick up Gutsy as I use it under Windows XP.

---

### Post by Hachi-Roku on 2008-01-03
hahaha. theres a good example of how you can overlook things. I didnt even think of that!!!

so i ran the diag as specified and the out put said that the drive is mounted and working fine.

then i tried to open the drive and wow, it worked. I didnt touch it since it hadn't worked. Im putting this down to the fact windows is severly f'd up in general.

Thanks for the replies! appreciated.

J

---

### Post by ~LoKe on 2008-01-03
I've been using explore2fs, should I be using this one instead?

---

### Post by Hachi-Roku on 2008-01-03
couldn't tell you the difference. If the one your using works... go with it!

This one has always worked  for me...until that strange problem. But all is well now so woo hoo!

---

### Post by ~LoKe on 2008-01-03
> **Hachi-Roku said:**
> couldn't tell you the difference. If the one your using works... go with it!

This one has always worked  for me...until that strange problem. But all is well now so woo hoo!

Explore2fs doesn't allow me to write to the partition, AFAIK.  Does this one?  Or is it read only?  I'll give it a shot the next time I'm in Windows.  I should at least try it out.

---

### Post by MrFSL on 2008-01-03
As compared to explore2fs, this driver actually lets you assign a drive letter and mount the partition/drive in Windows. Yes - you can write!

---

### Post by ~LoKe on 2008-01-03
> **MrFSL said:**
> As compared to explore2fs, this driver actually lets you assign a drive letter and mount the partition/drive in Windows. Yes - you can write!

O_O

Definitely got to remember to install it.  Are there any risks to damaging anything?

---

### Post by MrFSL on 2008-01-03
There's always a risk in everything we do - thats why all software seems to be beta these days and even a free notepad will come with a disclaimer.

Odd. ;)

---

### Post by ~LoKe on 2008-01-03
> **MrFSL said:**
> There's always a risk in everything we do - thats why all software seems to be beta these days and even a free notepad will come with a disclaimer.

Odd. ;)

Good enough for me. :)

---

### Post by Hachi-Roku on 2008-01-25
The probelm happened again....

this time when i ran the diagnostics it gave me a bit more to go on. 

It seems its not mounting it due to linux not unmounting the drive properly.... which comes from the shutdown hang problem i have in gusty.

the plot thickens!

---

