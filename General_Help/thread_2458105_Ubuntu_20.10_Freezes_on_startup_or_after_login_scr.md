---
title: "Ubuntu 20.10 Freezes on startup or after login screen"
date: 2021-02-16
forum: General Help
---

### Post by dhk.naeem on 2021-02-16
I recently installed Ubuntu on this laptop and after installation, it was running fine. However after shutting down my laptop, any startup just freezes on the booting screen or sometimes after logging in. My laptop model is Asus X507UA. I don't know what else to mention, so you can just ask me and I'll tell you.

---

### Post by Jonners59 on 2021-02-16
A question you shall be asked is if it freezes before or after GRUB menu...  Or does it freeze after you enter your password at, normally as an example Lightdm login welcome screen.

What graphics card are you using.  nvidia can be an issue and may need to start with GRUB momodeset.

Have you got a Live Recovery CD to use to start her up in Try Me mode.  Can get some fixes done if you can.

Have you tried the Start Up CD...?

---

### Post by dhk.naeem on 2021-02-16
I'm still new to Ubuntu so I'm not sure about the GRUB menu part. All I can say is that it normally freezes at the part where the only thing on my screen is the name of the laptop brand in the middle and Ubuntu at the bottom. Sometimes however I make it to the login screen and it freezes after I login.

My graphics card is Intel HD graphics 520.

No, I don't have any kind of CD. I installed Ubuntu through a bootable USB. Will that help?

---

### Post by CelticWarrior on 2021-02-16
Welcome.

The specification I've found says this:

> [COLOR=#000000][FONT=&quot]Storage[/FONT][/COLOR][COLOR=#333333][FONT=&quot]**Hard drive:**
[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]1TB 5400 rpm SATA HDD[/FONT][/COLOR]
To put it simply this is your main problem, a huge bottleneck. Realistically you can't expect good performance with any modern OS running in a slow HDD especially when checking for, downloading and installing updates.

Knowing this please describe exactly what you mean by "[COLOR=#000000]just freezes on the booting screen or sometimes after logging in" keeping in mind that a freeze/crash typically implies a forceful reboot. That NOT being the case the answer above is applicable. The only way to improve the performance is by replacing that HDD with a SSD, the cheapest and smallest one will make a difference like night and day. [/COLOR]

---

### Post by dhk.naeem on 2021-02-16
I mean it just gets stuck on the screen and nothing happens. If it's after login, I get stuck on a purple screen.

---

### Post by Jonners59 on 2021-02-16
1. > **dhk.naeem said:**
> I'm still new to Ubuntu so I'm not sure about the GRUB menu part. All I can say is that it normally freezes at the part where the only thing on my screen is the name of the laptop brand in the middle and Ubuntu at the bottom. Sometimes however I make it to the login screen and it freezes after I login.

SO that sounds like it is between GRUP menu and the login screen.  GRUB is a system that Linux installs to allow you to boot into any number of installed OS, often referred to as dual booting.

> **dhk.naeem said:**
> 
My graphics card is Intel HD graphics 520.
Noted

> **dhk.naeem said:**
> 
No, I don't have any kind of CD. I installed Ubuntu through a bootable USB. Will that help?
That is a "Live CD".  So if you plug it in and reboot it will boot to the USB and ask if you want to try or install ubuntu.  Just go into try.

---

### Post by dhk.naeem on 2021-02-16
Ok, booting it with the live CD doesn't do anything.

---

### Post by CelticWarrior on 2021-02-16
> **dhk.naeem said:**
> Ok, booting it with the live CD doesn't do anything.

How so? Doesn't it boot to a menu as indicated in the previous post?
How did you install Ubuntu before? It's the exact same procedure...

---

### Post by dhk.naeem on 2021-02-16
I'm doing the exact same thing and it literally made no change. Amazing.
Edit: Wait, nvm I'm stupid. I forgot to hold down Esc during startup.

---

### Post by CelticWarrior on 2021-02-16
Good...

Now please tells us how it works in a live session. Roughly how long it takes to give a functional desktop environment?
Then try booting normally (to the installed system). How long are you waiting in the (self-reported) "freeze" after logging in?
If it happens to stall when you see only the brand + Ubuntu it's a more serious problem and the first thing to do is to update UEFI ("BIOS"). If that doesn't help you may need to edit a couple of things.

---

### Post by dhk.naeem on 2021-02-16
Ok, I managed to get to this screen before it got stuck again:
[https://ibb.co/vHhxvBF]("https://ibb.co/vHhxvBF")

---

### Post by Jonners59 on 2021-02-16
> **dhk.naeem said:**
> Ok, I managed to get to this screen before it got stuck again:
[https://ibb.co/vHhxvBF](https://ibb.co/vHhxvBF)

> **oldfred said:**
> .
Oldfred, I think this gentleman needs your talents and majic wand.  :-)

---

