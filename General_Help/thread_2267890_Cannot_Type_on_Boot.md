---
title: "Cannot Type on Boot"
date: 2015-03-04
forum: General Help
---

### Post by Justin_Yarrington on 2015-03-04
Hello everyone, I am very new to the forums. 

I have already searched on topics relating to my topic but I have not been able to find anything relating to my certain issue. 

Recently I installed Ubuntu on my laptop, I am currently running version 14.10 and had very few issues when I first installed it via CD-ROM. 
However, recently whenever I boot up my laptop ( I currently have encryption enabled so it requires me to type in my password on boot) I get to the purple screen asking me for my password but am unable to type. My only work around is to go into the boot options and boot in recovery mode everytime I need to use my laptop now. I am unsure of what specefic details would be appropriate for this matter. If anyone can maybe guide me in a helpful direction, or even help me with my problem it would be greatly appreciated. 

I would be willing to do a fresh install of Ubuntu off the CD-ROM I just did not want to resort to that because I already have a lot of files and programs for my classes installed and don't want to deal with the hassle.

EDIT***: I would like to add additional information:
When I get to the Unlock screen for the encryption, when I start typing, the text appears in the top left corner of the purple screen. It overwrites the purple screen with black and the white text will appear. It should be appearing in the black field where I enter in my password. This happens instead. Thought this was relevant information. 

Thanks again in advance
-Justin

---

### Post by grahammechanical on 2015-03-04
So, the keyboard is active at the boot menu but not active at the login screen? Is it a USB keyboard? Try inserting it into another USB port.

EDIT: Forget what I just wrote. It a laptop.

Well, the only other idea I have is to check the BIOS/UEFI set up utility. In my BIOS settings there is an option that allows for having a plug and play OS. Having it set to No puts the responsibility on the BIOS to configure plug and play devices such as USB keyboards. If it is set to Yes then the responsibility falls on the OS and that could be where the problem lies.

Regards.

---

### Post by sandyd on 2015-03-04
> **Justin_Yarrington said:**
> Hello everyone, I am very new to the forums. 

I have already searched on topics relating to my topic but I have not been able to find anything relating to my certain issue. 

Recently I installed Ubuntu on my laptop, I am currently running version 14.10 and had very few issues when I first installed it via CD-ROM. 
However, recently whenever I boot up my laptop ( I currently have encryption enabled so it requires me to type in my password on boot) I get to the purple screen asking me for my password but am unable to type. My only work around is to go into the boot options and boot in recovery mode everytime I need to use my laptop now. I am unsure of what specefic details would be appropriate for this matter. If anyone can maybe guide me in a helpful direction, or even help me with my problem it would be greatly appreciated. 

I would be willing to do a fresh install of Ubuntu off the CD-ROM I just did not want to resort to that because I already have a lot of files and programs for my classes installed and don't want to deal weith the hassle.

Thanks again in advance
-Justin

Do you get the unlock request in recovery mode?
At which point do you get the unlock request - before the text menu or after? (Sorry, I don't use encryption anymore due to SSD)

---

### Post by Justin_Yarrington on 2015-03-05
> **sandyd said:**
> Do you get the unlock request in recovery mode?
At which point do you get the unlock request - before the text menu or after? (Sorry, I don't use encryption anymore due to SSD)
To clarify, when I get stuck on the purple Ubuntu unlock screen, I hit Ctrl+alt+Delete to reboot and choose the recovery mode from the boot options. 
In recovery mode, it goes into a black screen and a bunch of white text flies across the screen as it boots. I am then prompted while in the black screen with white text to enter in my password. I believe this is the unlock request you are referring to. And yes I can type then. The only time I cannot type is when I boot my laptop from off and I get the purple screen that says "Ubuntu" and the black bar where I am suppose to type in my password, but am unable to type anything.

---

### Post by sandyd on 2015-03-05
> **Justin_Yarrington said:**
> To clarify, when I get stuck on the purple Ubuntu unlock screen, I hit Ctrl+alt+Delete to reboot and choose the recovery mode from the boot options. 
In recovery mode, it goes into a black screen and a bunch of white text flies across the screen as it boots. I am then prompted while in the black screen with white text to enter in my password. I believe this is the unlock request you are referring to. And yes I can type then. The only time I cannot type is when I boot my laptop from off and I get the purple screen that says "Ubuntu" and the black bar where I am suppose to type in my password, but am unable to type anything.

That makes things a bit easier.

Removing the splash should allow you to login with the text console similar to what you see in recovery mode.

At the grub menu, highlight the non-recovery mode and press 'e' (I think it is 'e', it says what key it is on the grub menu)

There is a line that says something similar to
```

linux   /boot/vmlinuz-3.16.0-31-generic.efi.signed root=UUID=2921683e-6768-4e5b-b483-360c5592f73f ro  quiet splash $vt_handof
```

Mine is likely different due to use of secure boot, but it doesn't matter.

Remove the word 'splash' from the line, and follow the directions to boot.

---

### Post by Justin_Yarrington on 2015-03-05
> **sandyd said:**
> That makes things a bit easier.

Removing the splash should allow you to login with the text console similar to what you see in recovery mode.

At the grub menu, highlight the non-recovery mode and press 'e' (I think it is 'e', it says what key it is on the grub menu)

There is a line that says something similar to
```

linux   /boot/vmlinuz-3.16.0-31-generic.efi.signed root=UUID=2921683e-6768-4e5b-b483-360c5592f73f ro  quiet splash $vt_handof
```

Mine is likely different due to use of secure boot, but it doesn't matter.

Remove the word 'splash' from the line, and follow the directions to boot.

I believe this has resolved my issue. You are a life saver! Thank you very much for your help and assistance.

> **sandyd said:**
> That makes things a bit easier.

Removing the splash should allow you to login with the text console similar to what you see in recovery mode.

At the grub menu, highlight the non-recovery mode and press 'e' (I think it is 'e', it says what key it is on the grub menu)

There is a line that says something similar to
```

linux   /boot/vmlinuz-3.16.0-31-generic.efi.signed root=UUID=2921683e-6768-4e5b-b483-360c5592f73f ro  quiet splash $vt_handof
```

Mine is likely different due to use of secure boot, but it doesn't matter.

Remove the word 'splash' from the line, and follow the directions to boot.


Is there a way to save this change without having to do it on each bootup?

---

### Post by sandyd on 2015-03-05
> **Justin_Yarrington said:**
> I believe this has resolved my issue. You are a life saver! Thank you very much for your help and assistance.




Is there a way to save this change without having to do it on each bootup?

Good, we can now make it permanant.
Either
```

sudo nano /etc/default/grub
```
Remove 'splash' from GRUB_CMDLINE_LINUX_DEFAULT
PRess control+x to save,
Then
```

sudo update-grub
```

Or for one line magic...
```

sudo sed -i 's/\<splash\>//g' /etc/default/grub && sudo update-grub
```

---

