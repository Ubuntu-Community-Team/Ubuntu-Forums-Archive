---
title: "looking for program to wipe my hard drive"
date: 2016-02-29
forum: General Help
---

### Post by ross4 on 2016-02-29
My old Toshiba has pretty well had it. I can still boot Xubuntu on it but I know it will probably fail completely very soon. I want to take it to a recycling depot but I also want to be sure everything on the hard drive is wiped clean. I know there are various programs out there but I am pretty sure I need to run whatever program I use from within Xubuntu because I have found the splash screens for various linux install screens completely unreadable because the text that is presented is some kind of weird characters. That's why I thought it would be more efficient for me to ask here rather than try out these other programs. Any suggestions for good clean wipe? I have used the machine for banking and financial work.
Ross

---

### Post by sudodus on 2016-02-29
Try ***DBAN***, which is a free system, that is a separate system.

If you want to do it from Xubuntu, you can use ***hdparm***, but it is more difficult.

An alternative is to destroy the hard disk drive ***mechanically***.

---

### Post by Cavsfan on 2016-02-29
> **ross4 said:**
> My old Toshiba has pretty well had it. I can still boot Xubuntu on it but I know it will probably fail completely very soon. I want to take it to a recycling depot but I also want to be sure everything on the hard drive is wiped clean. I know there are various programs out there but I am pretty sure I need to run whatever program I use from within Xubuntu because I have found the splash screens for various linux install screens completely unreadable because the text that is presented is some kind of weird characters. That's why I thought it would be more efficient for me to ask here rather than try out these other programs. Any suggestions for good clean wipe? I have used the machine for banking and financial work.
Ross

You *should* be able to format the entire hard drive from a live CD [http://askubuntu.com/questions/633351/cant-format-hard-drive](http://askubuntu.com/questions/633351/cant-format-hard-drive)

---

### Post by ajgreeny on 2016-02-29
> **Cavsfan said:**
> You *should* be able to format the entire hard drive from a live CD [http://askubuntu.com/questions/633351/cant-format-hard-drive](http://askubuntu.com/questions/633351/cant-format-hard-drive)

That does not totally wipe the drive, I'm afraid, and it is still quite easy to restore partitions and files.

DBAN is worth trying or you can boot to a live ubuntu disk and run one of many possible dd commands which I am.not able to remember at present and am.also unable to search sensibly on this android tablet but is something like 

sudo dd if=/dev/zero of=/dev/sda
or
sudo dd if=/dev/urandom of=/dev/sda


A search of this forum will soon find the correct syntax, but take care with the dd command; it is coloquially known as Disk Destroyer so be certain that your of= is the disk you really want tp

---

### Post by ross4 on 2016-02-29
Yes, I really want to wipe it clean not just format it. In fact, I have already installed Xubuntu 64 over the XP and the Xubuntu 32 that was on it and had whatever sensitive data. However, the problem is that I cannot be sure if I will be able to read any of the screens that might come up if/when I boot from a live CD or any other program booted directly. I was able to install the new Xubuntu because I could preview the Install Menu on another computer and figure out what selection to make. Once Xubuntu was being installed and afterwards, things were fine ... sort of. Lots of vertical lines but the screen was readable. I had hoped to play with various other linux distros but with the initial screens being unreadable it has just become a waste of time. Hence, I want to dispose of the whole machine. I suppose taking an axe to the machine or using it for target practice would work but I'm not sure if a recycling depot will take computer pieces:o.

I'll research DBAN and dd. Since the hard drive in the machine is the only drive in it, I suppose it is pretty had to make a mistake. I'll get back to here and report but if there are any other ideas, I'd welcome them too.
Ross

---

### Post by sammiev on 2016-02-29
Take the HDD out and put a nail threw it. Install back into the computer and take it to the dispose site.

---

### Post by HermanAB on 2016-03-01
A medium sledge will do it.

Otherwise, the only secure way to erase a disk is with the secure erase utility that is built into all disk drives since the late previous century.  It can be activated with hdparm.  This will erase the whole disk, including the space between tracks and bad sectors.  Any other method will not erase the whole disk, only the working tracks.

---

### Post by 1clue on 2016-03-01
I'm a bit less trusting than some so I would **dd if=/dev/urandom of=/dev/sdX bs=4096** and then try that hdparm secure erase mentioned above.

---

### Post by ross4 on 2016-03-02
Thanks for the various replies. I ended up using dd AND DBAN. In the case of DBAN, the menu was unreadable on the screen but I was able to enter "autonuke", which starts the process automatically. That took about five hours so I am hoping it did a complete job. Rather put a stake through it's heart, I think I will save the body for doing educational autopsies on file recovery. I figure if I, with my very limited Linux knowledge can actually recover something, then there was a problem with the wiping.
Thank you all again for your suggestions.

---

### Post by sudodus on 2016-03-02
I think wiping with dd is enough to prevent 'mortal people' like you and I to recover anything. I think DBAN can do a better job. Too bad it has problems with the graphics in your computer.

Thanks for sharing your solution :-)

---

