---
title: "Mixup with openSUSE 10.2 &amp; Edgy &amp; Winxp"
date: 2007-01-11
forum: General Help
---

### Post by garbage_ on 2007-01-11
Ok the story is like this:
I got a new comp 2 months ago (hp dv2000 series) with pre-installed winxp on it.
I have shrinked the partition, and created 3 partitions - 1 for ubuntu, 1 for opensuse and one for the /home.
I have installed edgy - worked fine dual-booting.
when openSUSE 10.2 was released I have installed it in parallel - worked like a charm !

(now the grub menu is openSUSE's)

after playing with the openSUSE I tried to boot to the ubuntu - but there during the boot process I was told it cannot ID something called UUID (???) and opened a recovery console.
when I enter "exit" it continues the boot process and logs in - everything works fine, odd...

anyway, after several weeks openSUSE crashed on me without any reason and booted - now everytime I try to log it, it tells me that the session crashed after 10 secs and that I need login using the failsafe, but it crashes also.

to make a long story short ( ;) ) I want to restore my ubuntu and get rid of the openSUSE.
I thought of using Win XP recovery console with fixmbr but they don't give install CDs anymore with new computers and my WinXP SP1 doesn't recognize the harddrive.

does installing one more from ubuntu's live-cd will resolve this issue and won't try to load suse's dead corpse?

---

### Post by maxamillion on 2007-01-11
Installing from the ubuntu liveCD and just reclaiming hard drive space from the old OpenSuSE partition should fix your problems because the ubuntu installer will write a new grub config to the mbr when it is finished.

---

### Post by garbage_ on 2007-01-11
so just remove the openSUSE partition and install from the live-cd, nothing more?

---

### Post by hal10000 on 2007-01-11
You don't have to reinstall ubuntu you just have to reinstall grub

Assuming that your ubuntu root partition (i mean where your /boot directory is located) is  /dev/hda2, just do from your ubuntu live cd:
[COLOR="Red"]grub[/COLOR]
[COLOR="Red"]root (hd0,1)
setup (hd0)
exit[/COLOR]
This should reinstall grub to the mbr to the master disk of your primary (ide) disk.
You may use the free space from your SuSE installation as a partition for your data (documents, music etc.)

---

### Post by garbage_ on 2007-01-11
1st - can I do the grub install from my ubuntu install itself? (after all, it is working ...)
2nd - if my ubuntu install is in /dev/hda6, it means that the line should be this:
root (hd0,5)
?

thank you

---

### Post by hal10000 on 2007-01-11
Yes you can do it from the ubuntu install.
If /dev/hda6 is your ubuntu installthen:
[COLOR="Red"]
grub
root (hd0,5)
setup (hd0)
exit
[/COLOR]

The setup (hd0) means that grub has to be installed in the master boot record (mbr) of your harddisk.
You could even get grub to be installed to the boot record e.g. of your ubuntu install, then the line woud be setup (hd0,5), but in this case you would also need a boot manager to be installed into the master boot record (hd0). You could then call the second grub from within the one thas installed in your mbr.

But I think for your suits it's the best to install it to hd0.

---

