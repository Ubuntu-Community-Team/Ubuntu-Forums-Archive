---
title: "sudo password"
date: 2016-07-15
forum: General Help
---

### Post by viriatovigo on 2016-07-15
Has been long time that I didn't went into the terminal and I can't remember my sudo password.

How can I find?

Ta

---

### Post by slickymaster on 2016-07-15
The system does not store the password anywhere but a hash value is created from it; when you type a password a hash value is calculated and this is compared to the hash stored from the correct password.

You can reset it however, just follow this tutorial: [How to reset your password in Ubuntu]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by viriatovigo on 2016-07-15
Obrigado slickymaster.

Keep pressing "Shift" while rebooting does nothing at all. I need to put the Ubuntu 12.04 CD inside, then  reboot and it shows that window.

B ut in tht window says different things than in  yours. It shows: *Ubuntu and underneath of Ubunto "Advanced options for Ubuntu > Memory test (mentest86+) > Memory test (mentest86+, serial console 115200)".

I chose "Advanced options for Ubuntu" and shows "Ubuntu with Linux 3.13.0-77-generic > Ubunbtu, with Linux 3.13.0-77-generic (recovery mode) > Ubuntu, with Linux 3.2.0-23-generic-pae > Ubuntu, with Linux 3.2.0-3-generic-pae (recoivery mode)".

Now what?

---

### Post by slickymaster on 2016-07-15
> **viriatovigo said:**
> Obrigado slickymaster.De nada ;)

Keep pressing "Shift" while rebooting does nothing at all. I need to put the Ubuntu 12.04 CD inside, then  reboot and it shows that window.

B ut in tht window says different things than in  yours. It shows: *Ubuntu and underneath of Ubunto "Advanced options for Ubuntu > Memory test (mentest86+) > Memory test (mentest86+, serial console 115200)".

I chose "Advanced options for Ubuntu" and shows "Ubuntu with Linux 3.13.0-77-generic > Ubunbtu, with Linux 3.13.0-77-generic (recovery mode) > Ubuntu, with Linux 3.2.0-23-generic-pae > Ubuntu, with Linux 3.2.0-3-generic-pae (recoivery mode)".

Now what?[/QUOTE]
Just choose the Ubunbtu, with **Linux 3.13.0-77-generic (recovery mode)** option and follow the rest of the tutorial.

---

### Post by viriatovigo on 2016-07-15
No chance... After "Enter new UNIX password:" and "Retype new UNIX password:" (I did 3 times...) it says "passwd: Authentication token manipulation error","passwd: password unchanged".

Don't you tell me that I did wrong 3 times... Is my birthplace in Galicia and my birth year, so is very, very, very unlike that I did type it wrong 3 times...

---

### Post by slickymaster on 2016-07-15
That's, probably, because the file system isn't mounted read/write.

After selecting 'Drop into root shell prompt' run the following command```
mount -o remount,rw /
```and then repeat the steps to change the password.

---

### Post by viriatovigo on 2016-07-15
Nop... The same thing in the end: password unchanged

---

### Post by slickymaster on 2016-07-15
Ok, lets try one more thing.

Once again boot up your computer, chose "Advanced options for Ubuntu"choose Linux 3.13.0-77-generic (recovery mode), 'Drop into root shell prompt', run the following command```
mount -o remount,rw /
```Immediately after running that, run```
chmod 640 /etc/shadow
```Then do```
sudo passwd username
```It should work after that.

---

### Post by viriatovigo on 2016-07-17
"Sinto muito" the time to answer but I was out ot town.

After typing "chmod 640 /etc/shadow" it says: "Operation not permitted".

---

### Post by slickymaster on 2016-07-17
Can you please post the output you get from```
ls -l /etc/shadow
```

---

### Post by steeldriver on 2016-07-17
@slickymaster if the OP is only able to get to the grub menu by inserting a live DVD, doesn't that suggest they're actually seeing the grub of the **live** system? and hence is trying to change the password of the (ro) DVD...?

If it really is the case that they can't get to grub/recovery shell on the **installed** system, then a different approach will be required, I think e.g. mount the installed system from the live system and chroot into it to reset the password

---

### Post by viriatovigo on 2016-07-17
It shows: "-rw-r----- 1 root shadow 975 Feb 16 23:00 /etc/shadow"

---

### Post by slickymaster on 2016-07-17
> **steeldriver said:**
> @slickymaster if the OP is only able to get to the grub menu by inserting a live DVD, doesn't that suggest they're actually seeing the grub of the **live** system? and hence is trying to change the password of the (ro) DVD...?

If it really is the case that they can't get to grub/recovery shell on the **installed** system, then a different approach will be required, I think e.g. mount the installed system from the live system and chroot into it to reset the password

You're absolutely right, steeldriver. With all that's been going on with the forums I forgot OP's third post. Thanks for the heads up on that.

@OP:
Like steeldriver points out the reason we're not being able to change the password is because we're doing  everything in the live DVD, not on your system. So what you're going to do is:
[LIST=1]
[*]Boot your live DVD
[*]Once it boots, press Ctrl+Alt+T to get into a terminal window
[*]At the terminal mount your root partition```
sudo mount /dev/sda1 /mnt
```If you have a custom partition layout, you'll need to replace sda1 with the partition where the root of your file system resides
[*]Issue the command```
sudo chroot /mnt
```
[*]Use the passwd command to reset the password
[/LIST]

---

### Post by viriatovigo on 2016-07-17
?????? The DVD is not in the drive since the beginning... I don't understand.

Do you want me to put the CD in the drive  and reboot?

I have not a custom partition layout or I don't know if there is one. The PC is a Shuttle X50V4 All-in-One Barebone, so I did install the HDD, the RAM and install the Ubuntu 12.04 from the disc and all this happen now. Of course, I have also an external DVD drive and USB keyboard and mouse because the Shuttle Barebone comes without them, that's why is "Barebone".

---

### Post by viriatovigo on 2016-07-17
Just let you know that this is not the 1[SUP]st[/SUP] Shuttle Barebone that I build. I did a X50V2, X50V3 and X50V4.
 
 
 In total 5, one with Microsoft Windows Vista, other with Microsoft Windows 7, other with AppleMac Snow Leopard, other with Linux Ubuntu and other with Linux Kubuntu and no problems. This is the first time that I have an issue with the installation.
 
 
 I have not the discs of the previous installations because gave them away with the PCs.

---

### Post by slickymaster on 2016-07-17
> **viriatovigo said:**
> ?????? The DVD is not in the drive since the beginning... I don't understand.

Do you want me to put the CD in the drive  and reboot?

I have not a custom partition layout or I don't know if there is one. The PC is a Shuttle X50V4 All-in-One Barebone, so I did install the HDD, the RAM and install the Ubuntu 12.04 from the disc and all this happen now. Of course, I have also an external DVD drive and USB keyboard and mouse because the Shuttle Barebone comes without them, that's why is "Barebone".

Now you lost me. In your post #3 you said:> Keep pressing "Shift" while rebooting does nothing at all. I need to put the Ubuntu 12.04 CD inside, then reboot and it shows that window.
That's what made us assume that you were booting from the DVD/CD from the start.

---

### Post by viriatovigo on 2016-07-18
Damn!! Spanish had to be... Sorry, I am not too clever. Yes, but after getting into Ubuntu I did take off the disc.

OK, to avoid being more stupid and wasting your time helping me, I am going to tell you the full events since I did try to install it, but -as I said before- this thing never did happen before so I am totally lost.

Now, when  I switch on the PC, the typical BIOS start up window shows up and then it asks me for my password. I didn't set up a password (I did chose no passsord) but it forces me to set one. This also didn't happen before. After inserting the password and pressing "Enter",  comes on for few seconds the BIOS window again and then a black screen with the following:

mount: mounting /sys on /root/sys failed: Input/output error
[        35.210871 hda-intel Error request power-well from i915

Then comes a pink Ubuntu screen that says:

Errors were found while checking the disk drive for /.
Press F to attempt to fix the errors, I to ignore, S to skip mounting, or M for manual recovery

Afer pressing F or M comes a long string of scripts that I have no a clue what they mean. I do press I and Ubuntu opens as normal but then I have all the problems that I am reporting.

I sould be stating this since the begining; please, acept my apologies.

---

