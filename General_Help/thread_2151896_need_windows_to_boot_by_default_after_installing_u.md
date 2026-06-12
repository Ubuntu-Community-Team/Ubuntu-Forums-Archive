---
title: "need windows to boot by default after installing ubuntu"
date: 2013-06-06
forum: General Help
---

### Post by fowzan on 2013-06-06
i was running win server 2008 on my primary hdd. i later installed ubuntu 12.04 on another hdd leaving the windows untouched. ubuntu installed grub and made a boot menu. this boot menu lets me boot to windows (last option in the list). but that only happens if i use my secondary hdd to boot.
and if i use my primary hdd to boot i just get a blank screen. is it possible that that i boot to windows if i use my primary hdd and i get the grub menu if i use the secondary hdd?

---

### Post by Shrek01 on 2013-06-06
How about selecting to boot first on your 2nd HDD in your BIOS, which has your boot manager Grub, and then configuring Grub to boot by default on Windows?  IMHO this is the simplest solution.

You could install grub on the primary HDD instead.

---

### Post by fowzan on 2013-06-06
i plan to remove linux for now and reinstall at a later time. thats the reason i want my os to boot with primary hdd without grub

---

### Post by Shrek01 on 2013-06-06
So you want to reinstall the Windows' boot loader/MBR.  Boot using your server's CD and look for the repair option.

---

### Post by Mark Phelps on 2013-06-06
You said your Windows drive was removed when you installed Ubuntu on the other drive.  This has the following results:
1) GRUB would ONLY be written to the Ubuntu drive (since the other drive did not exist at the time)
2) Ubuntu would not know about any other OS, so there would be no entries in the GRUB menu for any other OSs
3) You should still be able to boot OK by having only the Windows drive connected

If there is a problem with 3), then you've done something since installing Ubuntu to mess up the boot loader on the Windows drive.

---

### Post by Shrek01 on 2013-06-06
If I deduced correctly from the original post, Fowzan is using the boot menu on startup (F12?) to select the hdd, which would explain why he does have a Grub entry for Windows.

@Fowzan can you confirm how you go from booting into one HDD to the other?

---

### Post by fowzan on 2013-06-06
windows hdd was intact when i installed linux. i just installed linux on the other hdd without touching the primary hdd. thats the reason the grub was installed on the secondary hdd and there is an option to boot to windows from that.
the problem i am facing now is that if i press f11 boot key and boot from my primary hdd the windows os is not able to boot (i guess grub removed the windows boot files). i can use the secondary hdd and select the windows option form the grub which works fine though.
what i am trying to do now is that if i boot with my primary hdd i want it to directly start the windows.

---

### Post by Shrek01 on 2013-06-06
Then windows repair should fix it.

---

### Post by greatsirkain on 2013-06-06
yup windows repair will fix it when he logs into windows. I had a similar problem when installing Ubuntu, it gave me the option when installing to have dual boot but it replaced the mbr with grub so even though I had the option for windows it wouldn't boot.
Make a boot USB with super grub2 on it and select 'detect any operating system' at start up when you see windows select it. This should boot windows and give you all the windows repair options if you've already removed ubuntu without fixing the MBR.
Optionally there are tons of boot disks/USB's you can make to fix the MBR.
Remove the drive with Ubuntu on when you do this otherwise it wont boot afterwards.
When windows is fixed re-connect the ubuntu drive and press f12 or whatever at start up to get the option of both drives with the correct boot loaders.
To get windows to boot automatically just go into BIOS and select the drive with it on as the primary boot device.

---

### Post by Mark Phelps on 2013-06-06
> **fowzan said:**
> windows hdd was intact when i installed linux. i just installed linux on the other hdd without touching the primary hdd. thats the reason the grub was installed on the secondary hdd and there is an option to boot to windows from that.
the problem i am facing now is that if i press f11 boot key and boot from my primary hdd the windows os is not able to boot (i guess grub removed the windows boot files). i can use the secondary hdd and select the windows option form the grub which works fine though.
what i am trying to do now is that if i boot with my primary hdd i want it to directly start the windows.

I thought you said that the Windows drive was NOT connected when you installed Ubuntu?  What you're saying here contradicts that and, since GRUB always installs to the first drive it sees (by default), that explains how the MBR on your Windows drive got overwritten when you installed Ubuntu.

You will need to repair the MBR on the Windows drive to get it booting again.

---

### Post by Rebelli0us on 2013-06-06
Just install "Grub Customizer", it will set up grub to do what you want.

---

