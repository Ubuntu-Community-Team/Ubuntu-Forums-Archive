---
title: "Gutsy Boot Blank Screen (different than the documented bug)"
date: 2007-11-14
forum: General Help
---

### Post by SagaLhan on 2007-11-14
Hey guys, I have upgraded Feisty to Gutsy a few weeks ago without any major problems and everything works fine.

So I decided I kind of wanted to stop using Windows XP on my pc at work (a Dell Optiplex 320 with I believe an ATI Radeon X1300 videocard). I had issues when booting the Live CD, something about an allocation problem. After some searching I was able to bypass this by adding "hpet=disable" to my Live CD bootoptions. I then proceeded to install Gutsy on a 70GB partition.

Well now, installation went fine and I rebooted into Grub. Grub looked fine as well. I boot Ubuntu and wham, blank screen. Nothing.

So I searched around again and noticed this was a well documented problem. There is however one problem: Ubuntu does not load with my pc **at all**. The documentation about this bug mentions that it's possible to wait 3-10 minutes for Ubuntu to boot (not displaying the splash screen). I have waited over 10-15 minutes without any sign of life from my pc.

I cannot get into Ubuntu at all to do the required upgrade and fix this problem. So basically, the reason this case is different from the documented one is because Ubuntu doesn't boot at all instead of booting after a few minutes.

Any help please? I hate using Windows for my programming work and was kind of excited about working on Gutsy.

---

### Post by SagaLhan on 2007-11-14
Tiny bump while the other side of the globe is still awake. :)

---

### Post by kylecchh on 2007-11-14
Man, I have the same black screen, except I didn't upgrade, and no Live CD issues, but a simular graphics card - Radeon X1600 512 Mb... I left my PC on over night to see if it would boot ubuntu, no life - just like you mentioned, mabye its something with the ATI Video Cards?

---

### Post by SagaLhan on 2007-11-15
I think it does yes, loads of problems with ATI cards. But every forumpost I could find mentioned Ubuntu did actually boot, but it just doesn't over here. :(

---

### Post by SagaLhan on 2007-11-20
Bump.

---

### Post by SagaLhan on 2007-11-21
And another bump.

---

### Post by SagaLhan on 2007-11-27
Anyone?

---

### Post by Ciansy on 2007-11-27
I have exactly the same problem, and I also have a Radeon X1300 card. I had Vista and Feisty on a dual boot, then upgraded to Gutsy and was about to get rid of Vista altogether but on rebooting the machine found that Ubuntu would not boot at all. I was all up for getting into Gutsy properly, but this is a complete killer.

---

### Post by SagaLhan on 2007-11-28
Yeah it is sadly. I could really do without Windows on my work and Gutsy seemed like the perfect OS to work on. Was really disappointed to find out it is so horribly bugged.

---

### Post by lokojones on 2007-11-28
Hi! Its strange that no one answered you..
Ok, the fact that your system doesnt boot at all, doesnt mean its not the same bug. Your system could be having any problem to boot or to start X server, and you wouldnt be able to see it. What I suggest is trying to boot from a live cd, and mounting the Hard Disk to see whats up. Check the X server error log, and if necessary, disable usplash, and set vga=791 at boot command line (/boot/grub/menu.lst, and add vga=791 to the end of the boot line) 791 is for 1024x768 at 16 bpp if i'm not wrong.

Good luck!

---

### Post by SagaLhan on 2007-11-29
Thanks for the reply! I'll just test it now.

[add] I added the vga option to the boot options and removed splash from it, but it doesn't change a thing. I also looked around in /var/log for an xserver error log, but I couldn't find any log of X. Does dat mean there is no log?

[add] I'm online on the Live CD right now and have just added fbcon to /etc/initramfs-tools/modules (a possible fix I found somewhere on Launchpad), then updated /boot/initrd.img-2.6.22-14-generic and copied it over the one that I have installed on the harddisk. Let's hope this does at least something, because it gets really frustrating to try so much and not really seeing any improvement at all. :p

I really can't find out what's wrong, if the Live CD boots fine (although with hpet=disable option), then why won't an installed Gutsy do the same? Anyway... I'll just try the above now.

[add] Again no luck, back on Windows now.

---

### Post by SagaLhan on 2007-12-04
Anyone got any ideas? I just installed Gutsy on my home PC as well without a single problem (Nvidia card), so it's obviously a horrible problem with ATI cards.

---

### Post by SagaLhan on 2007-12-06
I'm getting desperate.

---

### Post by Ciansy on 2008-01-08
I'm hoping this bug is fixed very soon. I've had to give up on ubuntu for the time being, and I'm (very unsatisfactorarily) back at windows. Also, it'd be nice if someone could try to help us out here in the meantime.

---

### Post by halln on 2008-01-09
I encountered that problem as well, this is what I did to fix it. I installed feisty 7.04 first then update it after that upgrade it to 7.10 using 7.10 alternate cd and presto!!  I get tru the black screen.

---

### Post by SagaLhan on 2008-01-09
Thank you for the suggestion! I'll try it out soon. =)

---

### Post by SagaLhan on 2008-01-10
I've downloaded 7.04, burned it, formatted my Ubuntu partition and installed Feisty. But I didn't get past the black screen sadly.

---

