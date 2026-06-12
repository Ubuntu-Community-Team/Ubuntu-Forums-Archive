---
title: "laptop with great specs not running smoothly"
date: 2016-06-11
forum: General Help
---

### Post by ryan219 on 2016-06-11
This will be my first post and I'm glad to be a part of this community as I've been a huge Linux advocate for years however was just an average desktop user. Now I am studying for the Linux+ cert and want to be a "Linux Guru" :)

My laptop has an Intel i7 processor and TWELVE GB or Ram. With that being said, why does it take almost 2 full minutes for my linux system to boot? it's the only OS on my HDD. I no longer have Windows as I am disgusted with the direction it's been going since Vista. 

Once my system boots, performance is mediocre given I spent quite a lot of money on my laptop. It's not terrible but it's bad enough that it gets in the way of several tasks such as music production using Ardour. 

First question, how can I see what my CPU is clocked at? I know it's an i7 obviously but I don't know the speed of the processor itself. Can I overclock it safely? Would that even help?

How can I optimize the boot process? 

Is there specific window managers/desktop environments that I can use to further improve system performance? 

Lastly, if I were to install a flavor of Ubuntu like Lubuntu or Xubuntu would that make everything run a lot faster since my computer has more than enough resources for those OS's? Or would it still run slow since they were intended to be run on legacy systems?

Sorry for the long post, but I'm lost here and still learning.

Thanks in advance fellas!

---

### Post by izznogooood on 2016-06-11
First of all take a look in the System Settings --> Software and Updates. Choose Additional drivers and make sure you are using the Proprietary drivers for your system.

[ATTACH=CONFIG]269523[/ATTACH]

When it comes to your boot time I have a suspicion it has to do with your network service or another service waiting for something. Have a look in "journalctl" in a terminal and see if you see something suspicious. Also do a search on this forum for slow boot!

---

### Post by sudodus on 2016-06-11
Welcome to the Ubuntu Forums :-)

I suspect that you have problems with some hardware driver, for example the driver for your graphics chip/card or wifi chip. Please tell us about those chips/cards, and someone might be able to help improve the performance.

Please tell us as much as possible about your computer

- hardware: You can run the following command (copy and paste it into a terminal window) and attach the compressed output text file lshw.txt.gz to a reply

```
sudo bash -c 'lshw -sanitize | gzip > lshw.txt.gz'
```

Click on the red button **[COLOR="#FF0000"]Go Advanced[/COLOR]**, and then **Manage Attachments**.

- software: Which version of Ubuntu are you running? 14.04.4 LTS or 16.04 LTS?

-o-

There are lighter desktop environments than standard Ubuntu, for example Lubuntu, Ubuntu MATE and Xubuntu, but with an Intel i7 you should have enough horsepower for standard Ubuntu or Kubuntu with all the bells and whistles :-) This is why I suspect problems with a hardware driver.

---

### Post by ryan219 on 2016-06-11
Great thanks! All I needed was a place to start. I'll go from here. If I run into some problems I can't solve I'll post back here. Take care!

Ok,


[ATTACH]269524[/ATTACH]

I am running 16.04 kernel 4.2.0-38

Sorry for double posting, I thought I was editing the previous post.

---

### Post by sudodus on 2016-06-11
> **ryan219 said:**
> Ok,


[ATTACH]269524[/ATTACH]

I am running 16.04 kernel 4.2.0-38

Sorry for double posting, I thought I was editing the previous post.

- There is something wrong with the attachment. I can't read it. Please try again!

- 16.04 LTS should have a kernel in the series 4.4. You seem to have a Wily kernel (15.10 or 14.04.4).

```
uname -a
```

shows that mine is 4.4.0-24-generic #43-Ubuntu

---

### Post by ryan219 on 2016-06-11
yeah, that's the kernel it says it's running. I used the same command.

"Linux eLogic 4.2.0-38-generic #45-Ubuntu SMP Wed Jun 8 21:21:49 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux"


Sorry you're right, I am using 15.10. This is gonna get frustrating for me. Pardon my ignorance....

Hopefully this attachment works:

---

### Post by sudodus on 2016-06-11
Don't worry about that. You are here to ask and learn. Soon you will know more ... :-)

Yes I can read the attached file.

- You have integrated Intel graphics - and there is probably no better driver.

- You have Intel wifi - should also work with the built in driver.

- Realtek Ethernet should work too.

Maybe someone reading this has detailed knowledge about your hardware.

---

### Post by ryan219 on 2016-06-11
I hope so...

The weird thing was when I did the fresh installation and deleted Windows in the process it ran great. It booted in under a minute but now it's doubled that time. In my opinion this honestly has something to do with the user who doesn't have the greatest idea of what he's doing... lol. 

I will check out startup services and other background services in the meantime as someone mentioned earlier to see if that could be a problem. I'm sure after some software is installed it automatically gets added in the startup process. 

btw not that this is related, but do you think 3 or 4 months is enough time to learn all the info for the Linux+ exam? I only have about 8-10 hours a week to study as I work 30-35 hours a week.

---

### Post by sudodus on 2016-06-11
What brand name and model is the computer?

It is possible that the graphics is really simple (for example if your computer is intended to be a server). Do you know if that is the case?

In that case you have two options.

1. Get a lighter desktop environment. ***Lubuntu*** has the lightest one, LXDE, and can perform quite well will an old or simple graphics chip. Before deciding:

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

2. Get a more powerful graphics card. Some people here prefer AMD/ATI/Radeon, others prefer nVidia. I have nVidia. nVidia cards usually need the boot option nomodeset at first to get simple graphics (enough to install a proprietary driver).

---

### Post by mc4man on 2016-06-11
I'd start over  with a 16.04 install & take it from there. If still issues then maybe search Broadwell specific. 
A skylake i7-6500U cpu here takes about 35 sec.'s or so with a hdd, an ssd would likely boot up in 15 sec. or less.
( my skylake u cpu is unfortunately only  a dual-core, my Haswell quad core, though older,  is faster with Ubuntu, 8 sec boot with an ssd & overall more responsive in general.

---

### Post by sudodus on 2016-06-11
I don't know about that exam, but I think other people know.

There might be a delay in the boot process, if something is badly configured for ***systemd***. In that case it can cause a delay of 90 seconds. But it does not explain the slow performance after booting.

---

### Post by ryan219 on 2016-06-11
It's an HP Pavilion. I'm not sure about the model number. I certainly don't think it's meant for server use as it came with B&O audio. 

That's what I was thinking of doing though. Just using a very light weight desktop. I'm debating on switching to the xfce flavor of Fedora though instead of Lubuntu. The course I'm taking on TestOut uses Fedora to teach Linux for the certification; however I also know Ubuntu is better for a newbie like myself. :)

Well I will go ahead and try a fresh installation. If that doesn't solve the problem I will switch to Lubuntu. But thanks anyway for your help guys! I'm sure we will meet again on here in the future!

Enjoy your day!

---

### Post by sudodus on 2016-06-11
You are right, HP pavilion is not a server. It should have decent graphics (unless the user is expected to install a separate graphics card).

You can install both operating systems alongside each other - a dual boot system with both Lubuntu 16.04 LTS and the current version of Fedora with XFCE. (By the way, Xubuntu is the Ubuntu flavour with an XFCE desktop environment.) With 12 GB RAM is is best to use a 64-bit system (which you have now).

> **ryan219 said:**
> Well I will go ahead and try a fresh installation. If that doesn't solve the problem I will switch to Lubuntu. But thanks anyway for your help guys! I'm sure we will meet again on here in the future!

Enjoy your day!

Good luck :-)

---

### Post by izznogooood on 2016-06-11
It should not be necessary to opt for a lightweight system with that hardware. I have a the same CPU and run Ubuntu with transparency tweaks and multiple Compiz plugins. I also have a SHDD (hybrid) so my boot time is less than 10sec. That includeds Plexmediaserver and other Desktop deamons...

---

### Post by sudodus on 2016-06-11
What about the graphics chip? (Maybe I missed something?)

---

### Post by RobGoss on 2016-06-11
> **ryan219 said:**
> I hope so...

The weird thing was when I did the fresh installation and deleted Windows in the process it ran great. It booted in under a minute but now it's doubled that time. In my opinion this honestly has something to do with the user who doesn't have the greatest idea of what he's doing... lol. 

I will check out startup services and other background services in the meantime as someone mentioned earlier to see if that could be a problem. I'm sure after some software is installed it automatically gets added in the startup process. 

btw not that this is related, but do you think 3 or 4 months is enough time to learn all the info for the Linux+ exam? I only have about 8-10 hours a week to study as I work 30-35 hours a week.

> btw not that this is related, but do you think 3 or 4 months is enough time to learn all the info for the Linux+ exam? 

Hello and welcome, I wouldn't put any time frame on learning how to use Linux it's an on going process and will take some time, I think three months will give you a head start in your classes. The best way to learn it is by trial and error. Ubuntu it a great OS and so are these forums as there're tons of information within these walls it's just finding things can be a bit tricky

Asking questions is the best way to learn if you don't know something just ask the members here are always willing to give a helping hand

As for your slow startup there are ways to tweak your system to get the best performance possible I don't always think Ubuntu is the culprit when it's comes to a slow boot up sometimes it's the machine it self in my case. I have a Dell inspiron 531 that is kinda slow booting up but I know it must be the machine because it use to have Windows on it and has always booted like this

The **startup application **is a great place to control what programs are being loaded each time your machine is booting up just uncheck what ever you feel is not needed at startup but make sure you know what programs you are removing from the list before you attempt this

Keep in mind not all Linux distro's will run the same, some GREAT some not so GREAT, it's all depends on the hardware and and which version you choose I've made a habit of using only the ones that run the best on my machines and I'm currently running **5-machines** with Linux and **5-more** on the way for testing purposes each one will have a different distribution running on it

I hope these pointers will help you with your learning process and remember the more research you do the more you will learn. Best of luck and again welcome to the forum

---

