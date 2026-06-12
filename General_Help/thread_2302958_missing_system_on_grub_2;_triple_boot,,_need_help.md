---
title: "missing system on grub 2; triple boot,, need help"
date: 2015-11-15
forum: General Help
---

### Post by freddyfields on 2015-11-15
Hi all, I just put together a triple boot system with ubunut, windows and android. After install of course i had to use a live cd to run boot-repair. Afterwards, theres no Android OS on the grub menu. I used GRUB CUSTOMIZER to have a further look and its not there ither.  I can see the 8.6 gig file system on my desktop, but cant log into it. Anyone know how to fix?

---

### Post by benjaminsinger1974 on 2015-11-15
Honestly, I feel that you would do much better to install [Virtualbox]("https://www.virtualbox.org/wiki/Downloads") .  This would allow for so much more comfort and control. It's what I have been doing for about a year now.  I would recommend using Debian or anything off of the Debian fork as your primary OS. Then go ahead and install whatever OS's you would like within Virtualbox.  Just my two cents hope this helps.

---

### Post by oldfred on 2015-11-15
Grub2's os-prober is set up to look for other systems, but I do not know if that includes Android??

How does one boot Android. You may have to add your own boot stanza to 40_custom.

       gksudo gedit /etc/grub.d/40_custom

Someone posted this which I saved, but it says live version?


```
 menuentry 'Android-x86 4.4-r3 Live' --class android-x86 {
search --file --no-floppy --set=root /system.sfs
linuxefi /kernel root=/dev/ram0 androidboot.hardware=android_x86 quiet DATA=
initrdefi /initrd.img
}


```

After any changes to grub, you have to run this:

sudo update-grub

---

### Post by freddyfields on 2015-11-21
Yes i know, But i am also having trouble with that. Ive downloaded several android iso's and several versions of virtalbox and tried multiple times to install it and it wont install. Ither get an error message or system constantly reboots. its a headache. I dont understand what im doing different because ive gotten it to install before. Maybe its ubuntu, maybe its android, or maybe its virtualbox.. IDK. Just know the android iso's boot up from boot menu, but wont work in virtualbox. tried on both widows and Ubuntu. Ijust want an android already!

---

### Post by freddyfields on 2015-11-21
Thanks, i will give it a try

---

