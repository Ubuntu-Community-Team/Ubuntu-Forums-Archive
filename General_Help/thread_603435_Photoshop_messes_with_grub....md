---
title: "Photoshop messes with grub..."
date: 2007-11-05
forum: General Help
---

### Post by mrphd on 2007-11-05
I have a very wierd problem. I am running a dual boot with Vista and Ubuntu on an ASUS VX2 laptop.

I have installed Adobe Photoshop CS3 on Windows. Everytime that I use photoshop I am unable to boot my computer.

Specifically, after running Photoshop, once the computer has been restarted I get the grub loading message, but it then restarts the computer before the grub menu appears. I then have to use the supergrub disk to restore grub to be able to boot again.

This happens *every* time I use Photoshop, and I have not had this problem using any other program at all.

What is going on and how can I stop it? How and why  is Photoshop messing with my computer?

---

### Post by danielronin on 2007-11-05
> **mrphd said:**
> I have a very wierd problem. I am running a dual boot with Vista and Ubuntu on an ASUS VX2 laptop.

I have installed Adobe Photoshop CS3 on Windows. Everytime that I use photoshop I am unable to boot my computer.

Specifically, after running Photoshop, once the computer has been restarted I get the grub loading message, but it then restarts the computer before the grub menu appears. I then have to use the supergrub disk to restore grub to be able to boot again.

This happens *every* time I use Photoshop, and I have not had this problem using any other program at all.

What is going on and how can I stop it? How and why  is Photoshop messing with my computer?

I thought it was just me! 

I'm having the EXACT same problem on my new Asus F3t laptop (and I have to fix it the EXACT same way)!

Also: due to a recent careless partitioning while changing distros (which resulted in a complete wipe and reinstall for both OS), I've now recreated the problem with two different distros (Kubuntu Fiesty and Mandriva 08, both using GRUB) *and* three different CS3 products (once with Photoshop CS3 extended only, once with CS3 Master Suite, and once on an unregistered 30-day demo, d/l'd straight from Adobe, specifically to test this problem )

I can't find anything online from Adobe, and the gent in tech support I chatted with with didn't seem to think there was a problem, since nothing is preventing the app from running properly in Vista. :(

Is there anyone out there that can anyone confirm whether or not this also happens with LILO (or on a different laptop or desktop)?

I'd volunteer mine, but it's running beautifully with a Kub Fiesty/XP dual-boot, and I can't see myself shelling out for another Vista license, plus the hardware upgrade I'd need just to make it run as well as it does on XP now, when I didn't really want it on my laptop in the first place (and I'm hesitant to play around with where the bulk of my media is stored).

But it's driving me nuts, and it's definitely CS3 doing it. To Kubuntu and Mandriva. Possibly any distro using GRUB.

Which really sucks, because that's mainly what I use Vista on my laptop for in the first place...arrrrgh!:mad:

---

### Post by #Reistlehr- on 2007-11-05
Hmm, i think it might be a coincidence. Photoshop has no need to write to the MBR. I have Dreamweaver CS3 and Photoshop CS3 installed, on XP, and no problems reported. Perhaps if you are both using vista, it's a coincidence with vista?

---

### Post by mrphd on 2007-11-05
> **danielronin said:**
> 
I can't find anything online from Adobe, and the gent in tech support I chatted with with didn't seem to think there was a problem, since nothing is preventing the app from running properly in Vista. :(

I will contact Adobe as well and see what they say. If they get more people reporting this, then I guess it is more likely to be resolved. I would be very interested to know whether this is affecting other vista users. But in anycase, I can't think of any reason *why* the program would be messing with the boot in the first place...

---

### Post by AJB2K3 on 2007-11-05
That is why I never use photoflop.
Your lucky when i had it photoflop killed my registry.

---

### Post by danielronin on 2007-11-05
> **mrphd said:**
> I will contact Adobe as well and see what they say. If they get more people reporting this, then I guess it is more likely to be resolved. I would be very interested to know whether this is affecting other vista users. But in anycase, I can't think of any reason *why* the program would be messing with the boot in the first place...

I'm going to see if I can install the CS3 Master Suite on my XP desktop just to double check, but I'm pretty sure it's the combination of Vista and CS3 (although there is a chance it's ASUS related). 

And I agree, there's no reason any of that stuff should be mucking around with the MBR on their own. What's weird is after repairing the Vista bootloader with UBCD4Win, it runs fine, makes no changes, and boots perfectly after numerous reboots and combinations of CS3 apps used in between them. Maybe the apps are making Vista do some kind of DRM check that makes the OS realize the MBR's been altered? Because no matter which CS3 app is used, even if only for a second, it buggers up a GRUB MBR (nothing I've ever done in Vista has before).

I only wonder about it being something ASUS specific because of the amount of crapware they have (not as bad as many, but still...), and because of other little "hiccups" my ASUS laptop has, like NTVDM errors, etc.

 cI guess I could use EasyBCD to make Vista load my Linux, but that just feels..so....wrong. 

I'd much rather find a way to make GRUB work (it actually worked beautifully until this)

---

### Post by danielronin on 2007-11-05
Also: **mrphd** - did you load Linux over Vista or vice versa, and was it before or after you had CS3 installed?

---

### Post by mrphd on 2007-11-05
> **danielronin said:**
> Also: **mrphd** - did you load Linux over Vista or vice versa, and was it before or after you had CS3 installed?

Vista Ultimate was factory installed, so Linux was installed after that and Linux was also installed before I tried CS3.

I'm only using a trial at the moment, so I can't open a support issue on their website, although I did send in a bug report. Not sure if I'll get any response from them...

---

### Post by danielronin on 2007-11-06
> **#Reistlehr- said:**
> Hmm, i think it might be a coincidence. Photoshop has no need to write to the MBR. I have Dreamweaver CS3 and Photoshop CS3 installed, on XP, and no problems reported. Perhaps if you are both using vista, it's a coincidence with vista?
Pretty sure it is Vista related, and I've been able to replicate it with 2 different OS and 3 flavors of CS3. I agree it had no business in the MBR> 

Are there any 'nix utilities that log MBR activity that I can use while I run a CS3 app?

---

