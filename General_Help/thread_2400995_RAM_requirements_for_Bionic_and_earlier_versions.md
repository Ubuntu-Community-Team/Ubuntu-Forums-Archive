---
title: "RAM requirements for Bionic and earlier versions"
date: 2018-09-12
forum: General Help
---

### Post by JamButty on 2018-09-12
I have an old laptop intended as an emergency backup if my newer desktop goes down or on the rare occasions I need a laptop while traveling. 
In trying to get a new external wireless adapter to work on it, it became clear I needed either to upgrade or at least reinstall the same operating system (password problem). The Bionic requirements include 2.0 GB RAM. It has 1.9 Gb (free -m = 1994, free -g = 1) which technically puts in just below the Bionic requirements. It currently has 16.04 on it. I checked the requirements for 16.04 and it also required 2 Gb officially, though it works with 1.9
Since I have to reload the system anyway, I would rather install 18.04 to have the best chance of getting the wireless adapter working. Is that likely to work or would I have fewer issues with reloading 16.04?

---

### Post by Impavidus on 2018-09-12
Minimum ram isn't a very hard requirement. If ram is too low, the system may still work, but very slowly. How slow is still usable is your decision.

Instead of an old version, I would use a lighter flavour. You could try Xubuntu or Lubuntu 18.04.

---

### Post by JamButty on 2018-09-12
thanks Impavidus! I have never tried other types of Ubuntu. My main concern would be getting this wireless adapter (Archer T2UH) working on it asap. In other posts concerning driver problems with that hardware, someone suggested that the user (then on 17.10) upgrade to Bionic to minimize such problems. Is there any reason to think that Xubuntu or Lubuntu 18.04 would be less flexible in accommodating less common drivers and/or self-compiled drivers?

---

### Post by oldfred on 2018-09-12
It does not look like 18.04 is a requirement, unless driver now included.

[https://askubuntu.com/questions/674116/how-to-install-tp-link-t2uh-wireless-adapter-driver-ralink-mt7610u](https://askubuntu.com/questions/674116/how-to-install-tp-link-t2uh-wireless-adapter-driver-ralink-mt7610u)

But see chili555's post, or better to check that device works with Linux first:
[https://ubuntuforums.org/showthread.php?t=2367163&p=13670888#post13670888](https://ubuntuforums.org/showthread.php?t=2367163&p=13670888#post13670888)

---

### Post by JamButty on 2018-09-12
hmmmm. The askubuntu link refers to the V1 earlier version of this hardware and, as it is EXTREMELY specific in it's commands, I am leery of that route.
The forums discussion with Chilli555 does not look very promising. If developers with years of experience specifically on that chipset cannot make it work, then I, who could not even follow the discussion, have zero chance. Preliminary checks before ordering it seemed to indicate that device could work and its features and price made it look ideal. Now I am stuck with it.
I am thinking I need to downgrade to 14.04. I still have an install CD for that and, theoretically, the drivers the hardware company supply are compatible with that. 
I am up against a hard deadline as I go on the road with that laptop in a week so the severe downgrade may be the only timely route. 
thanks!

---

### Post by oldfred on 2018-09-12
I still have my 14.04 install on my SSD, but all data is on HDD.
So you can multiple boot if you desire.

```
sda                                                          
&#9500;&#9472;sda1  vfat   EFI      FD76-E33D                            /boot/efi
&#9500;&#9472;sda2                                                       
&#9500;&#9472;sda3  ext4   trusty   45de38c8-6748-4634-b207-628d9aa8b42b 
&#9500;&#9472;sda4  swap            3af6a910-59f8-4719-b58c-2e7484d435f0 
&#9500;&#9472;sda5  ext4   iso_ssd  695d18b5-16f8-4e9c-bf66-675a12da5a26 
&#9500;&#9472;sda6  ext4   xenial   255a2800-b871-4fdf-a809-16987e64b8b3 
&#9492;&#9472;sda7  ext4   bionic   8c92557f-cc60-438b-b1ea-ffea0adf0a1a /
```

---

### Post by JamButty on 2018-09-12
This is just a backup laptop for emergencies and road trips - otherwise I am on a desktop with Bionic and working onboard wireless. To use basically as a netbook, 14.04 should be ok for  now on the laptop. Going dark now for a few hours as the process for installing on that crappy old laptop with no working onboard wireless, no working internal CD drive and a locked bios takes hours.

---

### Post by Impavidus on 2018-09-13
> **JamButty said:**
> Is there any reason to think that Xubuntu or Lubuntu 18.04 would be less flexible in accommodating less common drivers and/or self-compiled drivers?

Under the hood (which is where we are when dealing with drivers, kernels, repositories and that kind of things) all flavours of Ubuntu are the same.

---

### Post by JamButty on 2018-09-14
Thanks Impavidus and oldfred. I will close this for now. I would like to try a "lighter flavor" at some point but things are too chaotic right now. When I downgraded to 14.04 I got bad news and good news. Bad news, 14.04 is supposed to be kernel 3.13, which that external wireless theoretically supports. Once I finished the install though, I had 4.2, which should be 15.10??? Even in the older kernels available under "special" option of boot menu, there was no 3.xx kernel.
The good news, the onboard wireless that had remained dead though multiple reinstalls, came back to life. Don't understand it, but don't care for right now.

---

### Post by oldfred on 2018-09-14
You have to install 14.04 or more likely 14.04.1 to get original kernel. Those do not upgrade.
But then newer kernels are in the enablement stack upgrades. That is so a LTS can support newer systems that need new kernel & support software.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr)

---

### Post by Impavidus on 2018-09-15
You probably installed using the 14.04.4 live disk. That would give you the same kernel as Ubuntu 15.10. It's no longer supported, but should offer an upgrade to the 4.4 kernel of Ubuntu 16.04.

---

