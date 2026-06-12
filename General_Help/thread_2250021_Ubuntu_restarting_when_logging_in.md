---
title: "Ubuntu restarting when logging in"
date: 2014-10-26
forum: General Help
---

### Post by saravanan6 on 2014-10-26
Hi all,

i have installed dual OS, first one is Windows XP and Ubuntu 14.04. 
When i use Ubuntu OS, my machine getting restart automatically without any notification once i successfully log in. Some time its showing Home and restarting when i use any applications.
And the same thing happen in Windows XP also but the different is, I can work in windows and its very rare condition for computer to get auto restart without any notification. i.e restarting when i watching film in VLC player and when i play games.[B] But I can't able to use Ubuntu OS even a five minutes, because its getting restarting very often.
[/B]I have tried like installed Ubuntu 12.04 also, but no luck, same problem happened in that version also.
Can anyone help me?

**Note: Intel core 2 duo, 4 GB RAM**
Thanks!
Saravanan P

---

### Post by ajgreeny on 2014-10-26
What graphics card?
Does the machine get noticeably hot, and hotter in Ububtu than WinXP?

---

### Post by saravanan6 on 2014-10-27
am not use any special graphic card, just an default one **I**[B]ntel(R) G41 Express Chipset.
[/B]
i dont know what you mean by hot... but my machine is not hot and fans are working perfectly.

---

### Post by ajgreeny on 2014-10-27
OK.
Now from the grub menu run the **memtest86+** for as long as possible, even overnight if you can, and see if any errors show after running it.

---

### Post by saravanan6 on 2014-10-29
Here i attached **memtest86** result image. There is no error till 7 time success test.[ATTACH=CONFIG]257582[/ATTACH]

---

### Post by jhay2 on 2014-10-29
try to install xsensors on your ubuntu system .. and monitor your temperature "sudo apt-get install xsensors" and also check your power manager settings ,

---

### Post by Alireza_Zamani on 2014-10-29
check you runlevel and tel me :
> $ runlevel 

---

### Post by saravanan6 on 2014-10-29
I have installed xsensors in recover mode and attached here that screenshot[ATTACH=CONFIG]257597[/ATTACH]

---

### Post by saravanan6 on 2014-10-29
Temperature:

core 0 sometime coming 62 and core 1 sometime coming 53

I ran the "runlevel" in my terminal in recover mode...
Result:
saravanan@saravanan-desktop:~$ runlevel
N 2
saravanan@saravanan-desktop:~$

---

### Post by jhay2 on 2014-10-30
monitor the xsensors temperature before the ubuntu restart automatically as you said . if the temperature is greater that 80% and your system restart on its own , it might problem on cpu power fan?   




have you tried to install other distro's? a much lightweight than ubuntu ? like xubuntu or lubuntu ?

---

### Post by saravanan6 on 2014-10-30
Okay let me watch xsensors and reply here.
i have not tried to install other distro but i have tried installing lower ubuntu versions, 12.04 but the problem still happear :(

---

