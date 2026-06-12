---
title: "No sound - dummy output"
date: 2020-04-23
forum: General Help
---

### Post by bendanna93 on 2020-04-23
Hi guys, I'm new here, and new to Ubuntu in general. I have just installed the OS (18.04) to dual-boot with Windows 10, and it's given me plenty of trouble, but that's beside the point. My main issue right now is that my TV speaker is not recognized and all that is shown in the sound settings is dummy output. Now, I've been searching online for answers left and right for a couple hours, trying every terminal command I could dare to look at, but nothing has worked. Could anyone assist me?

For extra info, I have an old Element TV (ELEFT281 I believe), and my computer is an iBuyPower desktop. Sound card is NVIDIA High-Definition Audio.

---

### Post by CelticWarrior on 2020-04-24
Welcome.

First of all, "iBuyPower desktop" says nothing about the actual hardware. And "given me plenty of trouble" when it really shouldn't as long as users know the basics of installing OSes, suggests something wrong happened. Supposedly the motherboard itself has its own audio chipset so at least that one should have been recognized, i.e., not "dummy". The HDMI audio is on the graphics card and probably requires proprietary drivers.

---

### Post by bendanna93 on 2020-04-24
I bought it at Best Buy, I believe it's mass-manufactured, I'm not sure how to find the specs you'd be looking for.

Looking up proprietary drivers, it seems none are recognized even though they work on Windows just fine.

---

### Post by SeijiSensei on 2020-04-24
You probably need to install the proprietary NVIDIA driver to activate its sound system.  Go to System Settings > Driver Manager and let the application search your machine. It should offer to install the NVIDIA driver. Let it do so.

---

### Post by bendanna93 on 2020-04-24
I searched for Driver Manager and nothing came up. Is it called something different in 18.04?

---

### Post by CelticWarrior on 2020-04-24
Actually is Additional Drivers (as it always has been) and also a tab in Sofware & Updates (as it always has been).

---

### Post by bendanna93 on 2020-04-24
Ok, yeah I did find that already. I was doing some more online recommendations in the terminal however, and now it shows no output options at all.

I know I'm not being very specific, maybe I'm just gonna have to be on my own. Sorry guys!

---

### Post by SeijiSensei on 2020-04-24
> **CelticWarrior said:**
> Actually is Additional Drivers (as it always has been) and also a tab in Sofware & Updates (as it always has been).

On recent versions of Kubuntu it's now called Driver Manager.  It used to be called Additional Drivers, but that changed around the time Kubuntu moved from KDE4 to KDE5. Did the name not change in recent versions of other Ubuntu flavors?

---

### Post by bendanna93 on 2020-04-24
I'm currently going to install 20.0 and see if anything will be different.

---

### Post by CelticWarrior on 2020-04-24
> **bendanna93 said:**
> I'm currently going to install 20.0 and see if anything will be different.

Yes, please. I was about to suggest that.

Now:
[LIST]
[*]Make sure you're booting (and consequently installing) in UEFI mode. For better results when using the automatic installer first open Gparted in the live session and remove the single Ubuntu partition, do NOT touch anything else. 
[*]In UEFI disable Secure Boot and, optionally, Fast Boot 
[*]In Windows disabled the Fast Startup feature.
[*]In the Ubuntu installation make sure to select the option to install third-party drivers, codecs, software, etc. (this should automatically install the recommended Nvidia drivers for you graphics card). 
[/LIST]

---

### Post by bendanna93 on 2020-04-24
I'm not sure what Gparted is, I understand just about everything else though.

---

### Post by CelticWarrior on 2020-04-24
Gparted is a software for managing partitions, just search it and you'll find it. It's available on all live ISOs but not installed by default so if you want it later you'd need to install it. Alternatively you can use Disks, available in the live session and this is installed by default.

---

### Post by bendanna93 on 2020-04-24
Looks like the sound works now! Thanks guys!

---

