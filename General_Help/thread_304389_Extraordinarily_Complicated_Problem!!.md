---
title: "Extraordinarily Complicated Problem!!"
date: 2006-11-21
forum: General Help
---

### Post by lovloss on 2006-11-21
*sigh* okay

 My girlfriend got a laptop with windows already on it from someone else who had already lost the cd. So we have no disk. That wouldnt matter, except I decided to give her ubuntu. She didnt have a problem with that, until I messed things up.

 Her cd drive refused to read the boot cd. It would get an input/output error before it could enter installation, because the drive is lame. So we went online and found netboot options. I created a /boot/ folder manually, put the files where the manual said to, and rebooted. Instead of loading Ubuntu, however, it told me that system32/hal.dll was not right.

 Why that would matter for ubuntu I dont know.

 So i went and found the dll online and replaced the one in her system32 directory with it. Now neither windows OR ubuntu will boot. All I have now is a floppy disk drive, one boot disk that gets me into ms-dos, a network connection and a computer that wont boot up anything but floppies.

 Solutions? :(

---

### Post by x64Jimbo on 2006-11-21
Are you sure on the CD? Did it check out in a defect check? Please be more specific about what you did when you tried to get netboot setup.

---

### Post by lovloss on 2006-11-21
Yes im sure about the cd. It works, but it goes "chunk chunk chunk" and then gives me errors, sometimes early, sometimes after a few processes. It did the same thing to dvds earlier on, when i had windows running.

I added a command to the windows boot.ini file, and upgraded hal.dll

---

### Post by x64Jimbo on 2006-11-21
You might want to get a new optical drive for the system then. The lappy was donated, so $40-50 for a new optical drive is a small price to pay to have it working. 
Changing settings in boot.ini and upgrading dlls in Windows won't help your Ubuntu installation, as Ubuntu does not depend on any Windows files at all.

---

### Post by doobit on 2006-11-21
I had the same problem trying to install from the desktop CD on my old computer. I tried the alternate install CD test based install and the problems went away.

---

### Post by lovloss on 2006-11-21
Yeah i know, optical cd drive... maybe ill do that =)

---

### Post by x64Jimbo on 2006-11-21
It's not your only option, but you have to consider how much your time is worth to you. You could spend a few minutes installing a new CD drive or a few hours trying to make it install over the network. I think the main reason I would replace the drive if I were you is that I don't find a computer to be much use at all without its optical drive(s).

---

