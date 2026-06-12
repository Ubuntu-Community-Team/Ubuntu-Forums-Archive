---
title: "Cant write username and pass into gdm interesting things.."
date: 2007-10-22
forum: General Help
---

### Post by e77onx on 2007-10-22
Hiho!

 
I have an interesting problem in Gutsy(fresh install) :(
The install works fine without any problems.
After the install i enable the nvidia driver and download the update.
Reboot still works fine . But when i turn off and on the pc, i get the gdm login screen 
the **mouse is moving but i cant write my username and password** i press the buttons but nothing happen. The restart and shut down dont work.
I pressed reset the login scrren comes up and i can log in.... o.O
I tried power off again and same happend.. i can login only after 1-4 reset :(
When i can login everything works fine.
Sometimes after turn on the boot up screen in different higher resolution then normal (1280x1024 my monitor show that ) and sometimes (when i can login) when I logout the screen in another higher resolution o.O.

I try to reinstall 3 times and dont use nvidia restricter driver(I dont touch anything!)  and plug out my ntfs hdds but still same happen.  :(

On other hdd(ata)  win xp and debian works fine.

ubuntu 7.10 386

My pc spec :

atlon64 3500+
asus A8V deluxe
512 ddr 
samsung 250GB sata hdd

Thanks if somebody can help me.
I dont know really if its a hw or software related issue.
 PLS help! :)

Sorry for my bad english !

Regards:

e77onX

---

### Post by ihcnet on 2007-10-22
It kinda sounds like a problem with your keyboard. Try hitting CTRL+ALT+F2 to bring up the virtual terminal just to make sure you keyboard is still functioning after X windows starts.

---

### Post by e77onx on 2007-10-22
Thanks for the answer! I try some other keyboards but still same happend. :(

**when i turn on the pc  the the boot screen in higher resolution(1280x1024).** my desktop in 1680x1050 but the normal boot screen is in 1024x768  and i dont understand why is higher when i start with power button  :confused:
Login screen comes up and keyboard dont work but the screen resolution changes is interesting too.. The mouse work so i push restart or power off and nothin happens just black screen aand my monitor osd show a window with lower frequencies warning 7/17khz  :confused: :( (only reset helps)
I push the reset to restart the pc.
After reset the booting screen resolution is ok(1024x768)  and everything works fine..
Sometimes i need only 1 reset other time i need 2-3 . Annoying :S

Any other ideas?

Thanks :
e77onx

---

### Post by martinrandau on 2007-10-22
I have about the same problem. I don't use any splash screen so I can test when the keyboard works or not outside X. It often takes around 4 hard boots to get it working, sometimes it works by switching kernel (but that might be because it happens to be the 4th boot and would have worked with first kernel as well). I never have problems choosing kernel at the grub list which suggests that the problem is not faulty hardware but something with the kernel. I can use the mouse to shut down or reboot from gdm, it's just the keyboard that doesn't work, both in gdm and at the command line (ie outside X). 

I have Ubuntu 7.10 64-bit, nvidia 8600.

---

### Post by _tom_ on 2007-10-25
Same problem here, 1 in 3 or 4 times I can get the keyboard to work in gdm. I have tried a PS/2 and a USB keyboard, no difference. No problems with the resolution. 

Ubuntu 7.10 i386, ATI Radeon 8500

---

### Post by Bobcatben on 2007-10-28
iam getting the same problem, with the keyboard working only a few times out of many boots.have been since day 1 with 7.10, glad to see its not just me).
it worked fine with feisty, if i watch, the keyboard lights go out right as x starts.

---

### Post by Tim82 on 2007-11-04
Same thing here (Ubuntu 7.10 AMD64)!

My keyboard is not really "dead", because the kernel magic sysRQ keys are still working, which means I can make a "soft" reboot.
I made a diff between the Xorg.0.log (when the keyboard is fine) and the Xorg.0.log.old (from a boot where the keyboard makes problems).
The only difference (additionally the different time) is the last line:
"SetClientVersion: 0 9"
This line is missing in the Xorg.log.old.
I tried to find out something about this log message, but without result.

Someone knows something more?

Thanks!

Bye, Tim

---

### Post by Papillonrus on 2007-11-22
check the "Show Actions menu box" @

System/Administration/Login window Preference  Local Tab  

Try that if it don't work use terminal Command

"sudo shutdown -r now"         "sudo shutdown -h now"             "sudo halt"

---

### Post by Bobcatben on 2008-01-03
dunno if it helps to figure it out or not but, i enabled auto login, and now the times when the keyboard would be not working, i just get a blank screen the color of the default ubuntu color, and a working mouse, sometimes the login sound, but thats it.

---

