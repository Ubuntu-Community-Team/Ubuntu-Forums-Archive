---
title: "Ubuntu appears to be running in safe mode"
date: 2016-04-28
forum: General Help
---

### Post by eipapp on 2016-04-28
I installed both Ubuntu and Ubuntu Mate (at separate times) and in both cases they installed fine. I had issues with each of them starting after install and had to add nomodeset after quiet splash in order for them to boot up.
However, when they did, both appeared to running as if in safe mode and I don't know what to do to get them running as they should. Any ideas ??

Thanks,
Bruce

---

### Post by mastablasta on 2016-04-28
> **eipapp said:**
> I installed both Ubuntu and Ubuntu Mate (at separate times) and in both cases they installed fine. I had issues with each of them starting after install and had to add nomodeset after quiet splash in order for them to boot up.
However, when they did, both appeared to running as if in safe mode and I don't know what to do to get them running as they should. Any ideas ??

Thanks,
Bruce

you need to install graphic drivers, if possible. at this point some system information would be good in order to advise further.

see here on how to do it: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by grahammechanical on 2016-04-28
What OS are you using now? If it is Ubuntu Mate I cannot help. If it is Ubuntu then the About this computer option on the power/cog menu will give some information about the video adapter and driver being used.

You might need to go to Additional Drivers and try another video driver.

Regards.

---

### Post by eipapp on 2016-04-28
Currently I'm running Win 10 which I defaulted to when I couldn't get either of the Ubuntu distros to work. This from my registry entry DeviceO \Registry\Machine\System\CurrentControlSet\Control\Video\{400ABB9B-3985-4CCA-AC52-022AB6BFC8CE}\0000
Do not know if this is of any help. 
Would I go to AMD to check or update video drivers ?? Machine is running AMD E2-1800 processor, again, for what it's worth. 

Thanks,

---

### Post by eipapp on 2016-04-28
From what I could find out, my system is using AMD Radeon HD 7340 Graphics and AMD does not show any other available at this time.

---

### Post by mastablasta on 2016-05-01
that CPU & GPU is slow and nothing to be impressed with. However the Mate desktop should still run fluently.

i believe the 16.04 will no longer have closed source drivers support for that chip, however if you install 14.04 you will be able to install the closed source driver fglrx. this should help you at least until they get the opensource driver fixed or until the fglrx support runs out.

info on opensource driver: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
Info on closed soruce driver available in 14.04: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

cards supported by amdgpu: [https://wiki.gentoo.org/wiki/Amdgpu](https://wiki.gentoo.org/wiki/Amdgpu)

the APU is similar (and slightly better) to the E-450 which i have and that one is working well with fglrx drivers on 14.04. but it is also performing well with opensource drivers only the power management is worse (note that i haven't tried the latest opensoruce driver version). the nomodeset (more info on it here: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)) should not be necessary on your chip. you can use the linked pages to see if you have hardware support enabled or not and also explore the ***dmesg*** command in terminal which will tell you what went wrong on boot.

---

