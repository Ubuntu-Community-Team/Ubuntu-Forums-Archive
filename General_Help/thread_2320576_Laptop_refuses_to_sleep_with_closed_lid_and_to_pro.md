---
title: "Laptop refuses to sleep with closed lid and to properly wake up"
date: 2016-04-15
forum: General Help
---

### Post by Le3eVolfoni on 2016-04-15
Hello,

I installed ubuntu 14.04 on an old Toshiba. I have two problems that could possibly be linked. I tried to fix them separately with no luck and I am running out of ideas.

The first issue is that when I close the lid, nothing happens. The computer stays on. I checked logind.conf and found > HibernateLidSwitch=suspend If needed I can cp the rest of the logind content.

The second one seems odd. When the computer sleeps, sometimes it wakes up just fine, and sometimes it wakes up with a black screen. When the screen is black the fan is on, the LED, that is orange when the computer is asleep, is green, but I can't get the computer to reboot through the terminal, meaning it probably freezes. 

It is a fresh install, ubuntu 14.04, kernel 4.2.0-35generic, processor AMD Sempron(tm) SI-42, graphic card AMD/ATI RS780MC Mobility Radeon HD 3100. I installed Lubuntu 14.04 kernel 3.13.0-24-generic, with the same issues, and came back to ubuntu.

Thanks for any help you could bring, I can provide any other information if needed.

---

### Post by mörgæs on 2016-04-16
Have you tried 16.04?

---

### Post by Le3eVolfoni on 2016-04-16
No I didn't, the computer being old I supposed 14.04 was the newer version it could run and didn't even tried the 16.04. I will install it today, I let you know if anything changes. Thanks for the idea.

---

### Post by mörgæs on 2016-04-16
Good. 
As you mention yourself it's only an idea, not a promise that it will work.

---

### Post by Le3eVolfoni on 2016-04-16
I installed Ubuntu 16.04 beta2 and nothing changed, the problem remains the same.

The more I read about similar problems the more I think it is linked  with the ATI graphic card. I tried to install proprietary drivers (even  if unadvised everywhere, the graphic card being very old). I didn't find  a way to properly install it. I forced the installation of a legacy  driver, an AMD dialogue poped up to tell me both "installation  successful" and "some errors occured...". Among these errors it was  written that the hardware acceleration hasn't been installed. And  finally Ubuntu doesn't start anymore, stuck on the purple page. I tried  with both 14.04 and 16.04.

Maybe a solution would be to find proper drivers, but I start to doubt  they exist. I could as well try another distro, but the only linux I  ever had was ubuntu, I have no idea by what to start.

Edit: double post

---

### Post by Le3eVolfoni on 2016-04-17
Nobody has an idea ?

---

### Post by dFlyer on 2016-04-22
Just to let ya know, I'm on a fresh install of 16.04 and have suspend problem. To make it short, suspend works with the timeout period, with the suspend from the main menu, but not with the close lid. On close lid it wait for the time out period. I'm on an hp and never had any suspend problems with 14.04.

---

### Post by sammiev on 2016-04-22
I know on some flavors you can choose what will happen when the lid is closed. 

I'm not having issues here so far.

What flavor are you using so I may try it?

---

### Post by dFlyer on 2016-04-23
16.04 LTS Unity

---

### Post by sammiev on 2016-04-23
> **dFlyer said:**
> 16.04 LTS Unity

Hi,

Just tried Unity 16.04 with suspend by closing the laptop lid with no issues.

Took a snapshot of my settings.

---

### Post by dFlyer on 2016-04-23
Exact same settings except for I have mine suspend at 10 minutes.

---

### Post by sammiev on 2016-04-24
> **dFlyer said:**
> Exact same settings except for I have mine suspend at 10 minutes.

This one has me at a loss, hope someone jumps in that may have ran into the same problem.

It seems to be working very well on different Toshiba's.

---

### Post by dFlyer on 2016-04-24
I went ahead and filed a bug report on this.

[https://bugs.launchpad.net/bugs/1574161](https://bugs.launchpad.net/bugs/1574161)

---

### Post by dFlyer on 2016-04-26
> **dFlyer said:**
> I went ahead and filed a bug report on this.

[https://bugs.launchpad.net/bugs/1574161](https://bugs.launchpad.net/bugs/1574161)

Adding HandleLidSwitchDocked=suspend

to /etc/systemd/logind.conf seems to have fixed the problem on my HP.

---

