---
title: "(Stupid?) Question re. Ubuntu security"
date: 2007-01-10
forum: General Help
---

### Post by sarc on 2007-01-10
After all this is the beginner forum.

If I can start a PC with the LiveCD and mount didks, what's stopping anyone with a LiveCD from mounting and accessing my drives?

p.s. I am considering truecrypt to protect my shared drives Ubuntu/Win XP.  Do you think it's a good choice?

Thanks

---

### Post by scrooge_74 on 2007-01-10
Live CDs are in my opinion for "show and thell" and for emergeny repairs not to be your everyday work force.

And then you could set your bios not to boot from the CDROM, and put a password for the bios.

---

### Post by stalker145 on 2007-01-10
> **sarc said:**
> If I can start a PC with the LiveCD and mount didks, what's stopping anyone with a LiveCD from mounting and accessing my drives?

p.s. I am considering truecrypt to protect my shared drives Ubuntu/Win XP.  Do you think it's a good choice?

Physical access is the bane of security's existence. If someone can actually sit at your box, there is next to nothing that you can do about it. I have no experience with encryption on Linux, but that is probably the best step to move on to if you are worried about someone that has physical access to your box getting your information.

As previously mentioned, set a BIOS password and remove the CD-ROM from the startup list in your BIOS... it will help.

---

### Post by liljoe76 on 2007-01-10
encryption is your only real option (though i know nothing bout it) to lock down the box. if someone is intelligent enough to use a live cd and mount your disk, then they probably also know how to google bios crackin... thats not hard ;)
f*ed if you do... f*ed if you dont.
-joe

---

### Post by az on 2007-01-10
You don't even need a live cd, just a screwdriver....

---

### Post by scrooge_74 on 2007-01-10
> **azz said:**
> You don't even need a live cd, just a screwdriver....

Right on the mark as always :D

---

### Post by rioghal on 2007-01-10
Physical access to your computer is something that is hard to secure. However, I have taken the following steps to make this job more difficult to anyone trying to physically access my hard drives.

1) Set BIOS to boot from the hard drive and set a BIOS password so that BIOS changes can only be done by someone with the password.

2) Remove all recover mode boot options from /boot/grub/menu.lst so that no one can simply boot into recovery mode (root). The downside to this is you won't be able to boot into recovery mode either.

3) I keep all usernames and passwords for websites/credit cards/PINS/etc encrypted on the hard drive. I use Revelation (it's in the repos) to manage and save all of these items.

The hardest thing to prevent is someone simply taking a screw driver and removing the hard drive so they can browse it at their leisure. Using encryption will prevent them from gaining vital information if they do that.

---

### Post by smoker on 2007-01-10
bios passwords can be overcome in minutes, and you can get bootable usb-drives now, encryption, or get a removable drive and take your data with you:-)

---

### Post by sarc on 2007-01-10
AAAARGH this confirms my worst fears...

If I set the BIOS to HD boot only then something happens to my system I'm F**KED!  No way to alternate boot.

I&#314;l have to look at encryption to slow the b*stards down.

Thanks guys (and girls).

---

### Post by Ocxic on 2007-01-10
actually your not f**ked, the bios will always be accesable, so you don't have to worry about not being able to change anything there if you system crashes.

---

### Post by rioghal on 2007-01-10
> **smoker said:**
> bios passwords can be overcome in minutes, and you can get bootable usb-drives now, encryption, or get a removable drive and take your data with you:-)

Actually, I recently forgot my BIOS password. So, I hopped on the internet and searched google, yahoo, and a few others, for default passwords to my BIOS chip. I found dozens.. but, guess what, none of them worked. I spent an entire day searching and trying everything I found and I was not able to get into my BIOS via a default password or anything. I am thinking that manufacturers have changed things in the recent BIOS chips or I just totally missed the one I needed. I must have tried a hundred passwords before giving up.

Taking you data with you is an excellent idea, though.

---

### Post by scrooge_74 on 2007-01-10
reset the bios, you need to change a jumper in your motherboard and it goes back to default settings :D

---

### Post by rioghal on 2007-01-10
> **scrooge_74 said:**
> reset the bios, you need to change a jumper in your motherboard and it goes back to default settings :D

Well, I'll just keep important data encrypted with Blowfish or IDEA.. let's see them break into that ;)

---

### Post by esaym on 2007-01-10
> **sarc said:**
> After all this is the beginner forum.

If I can start a PC with the LiveCD and mount didks, what's stopping anyone with a LiveCD from mounting and accessing my drives?

p.s. I am considering truecrypt to protect my shared drives Ubuntu/Win XP.  Do you think it's a good choice?

Thanks

Linux is secure 

This has been discussed before and if some kind of "hacker" type guy has access to your physical hardware then you are just screwed either way.  

Get some better locks on your doors;)

---

### Post by sarc on 2007-01-12
Duh.. yer right!  Thanks.  Off I go.

---

### Post by laidback on 2007-01-12
I'm not concerned re this issue in particular but I do use removable hard drives which are fitted into caddys, this means that you can easily take the HD away with you, no more difficult than removing a CD. If you were to use these then you wouldn't need to leave your HD in the PC at all, instead take it with you and lock it away! 

It's an idea for those who are as concerned as Sarc.

Laidback

---

### Post by gkasinath on 2007-01-15
quoting B. Schneier, "Security is a chain only as strong as its weakest link". 
If you are looking for security and computers (especially networked), forget it. No matter how much of the *security* magic dust you sprinkle on your box, it aint 100% secure. 
The best way is, use your computer only for stuff that you can live with, if compromised. Saving credit card numbers, pin numbers, account information etc, if you are looking for security, you will remember them by heart (in your head) and not trust a device to store it for you.

---

### Post by Sef on 2007-01-15
> The best way is, use your computer only for stuff that you can live with, if compromised. Saving credit card numbers, pin numbers, account information etc, if you are looking for security, you will remember them by heart (in your head) and not trust a device to store it for you.

Agreed.

> (Stupid?) Question re. Ubuntu security

Not a stupid question.  A rather intelligent one.

---

