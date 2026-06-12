---
title: "Toshiba L-300 Lubuntu install issues"
date: 2019-03-24
forum: General Help
---

### Post by ivan1987 on 2019-03-24
Hello friend,

I am trying to install Lubuntu 18.10 32-bit on my Toshiba Satelite L300 laptop but I am getting a problem.
"ACPI BIOS ERROR (bug): Excess arguments ACL declared 5, ACPI required 4 "

Thanks in advance!

[https://ibb.co/g36Bv8b](https://ibb.co/g36Bv8b)

---

### Post by ivan1987 on 2019-03-24
Hello again everyone,

I am trying now to install Lubuntu 14.04.5 but my computer restarts automatically when it reaches the desktop and i cannot complete the installation. 

I had problems with my computer when it was running on windows 7 -it was restarting automatically 2-3 times before loading the windows. 

Thanks

---

### Post by Rex Bouwense on 2019-03-25
> I am trying now to install Lubuntu 14.04.5
I think that you should try a newer version since Lubuntu 14.4 reached End Of Life back in April of 2017 and is no longer supported.  The current LTS version is 18.04.

---

### Post by ivan1987 on 2019-03-26
> **Rex Bouwense said:**
> I think that you should try a newer version since Lubuntu 14.4 reached End Of Life back in April of 2017 and is no longer supported.  The current LTS version is 18.04.

Hi, I have already tried to install 18.10 but it was giving me problem. I described above the exact problem. Is there any big difference between 18.10 and 18.04?

---

### Post by westie457 on 2019-03-26
Try running a 'Memtest' from your usb - the third line of the Menu Screen.
Re-seat or swap the positions of the memory chips.

The restarting issue is usually caused by memory chip problems.

---

### Post by kc1di on 2019-03-26
We really need more to go on to help you.
What type of Machine, model ram video card Etc.

---

### Post by ivan1987 on 2019-03-26
Hello, kc1di

My Laptop is Tosiba L-300, 32-bit, Intel premium Dual-core 2G RAM (year 2007), I am not sure for the video card L
It was running with Windows 7 but it was running slowly and started automatically restarting when I was trying to start it (normally after 2-3 automatically restarts it reached desktop). Then I decide to reinstall the Windows 7 and clean the old windows with all file and started installing windows and it started automatically restarts and installation couldn&#8217;t be completed. Then I tried Lubuntu 18.10 but I am getting a problem - "ACPI BIOS ERROR (bug): Excess arguments ACL declared 5, ACPI required 4 ". Now I am trying now to install Lubuntu 14.04.5 but my computer restarts automatically when it reaches the desktop and I do the first steps of the installation and i cannot complete the installation.

Thanks

---

### Post by oldfred on 2019-03-26
Moved to your own thread as issues and system are different.

You have a 64 bit chip.
Intel Core 2 Duo T8100 with Intel X3100 Integrated Graphics

I have mostly retired my Toshiba laptop from 2006. It has Dual core Intel Core2 T5500, but only 1.5GB of RAM.
I last installed 64 bit 16.04, just to see if it still works.
Was a bit surprised as even Full Ubuntu 16.04 ran, but slow. Before older full Ubuntu with Unity ran so slow it was not at all usable. But I would install gnome panel or fallback witch is also lightweight and worked well on my systems. With only 1.5GB of RAM I could only run one larger program and a couple of small ones at one time. If two larger, it would go to swap, screen turned gray when going to swap for a few seconds.

Try 16.04 64 bit version.

---

### Post by mörgæs on 2019-03-26
Oldfred is correct: There are various T300's but all of them have 64 bit CPU's. 

Anyway, using any 32 or 64 bit ISO can you run a live boot when pushing F6 and choosing the boot option shown here?

[https://i.stack.imgur.com/X6dvz.png](https://i.stack.imgur.com/X6dvz.png)

---

### Post by ivan1987 on 2019-03-27
> **mörgæs said:**
> Oldfred is correct: There are various T300's but all of them have 64 bit CPU's. 

Anyway, using any 32 or 64 bit ISO can you run a live boot when pushing F6 and choosing the boot option shown here?

[https://i.stack.imgur.com/X6dvz.png](https://i.stack.imgur.com/X6dvz.png)

Hi,

I tried to install the lubuntu 16.10 with acpi=off and it reached to this level (see attached pic)

[https://imgur.com/hSv1ctr]("https://imgur.com/a/RdPTwev")

---

### Post by ivan1987 on 2019-03-27
> **westie457 said:**
> Try running a 'Memtest' from your usb - the third line of the Menu Screen.
Re-seat or swap the positions of the memory chips.

The restarting issue is usually caused by memory chip problems.

Hi, 
I run the test and this is the result.

[https://imgur.com/xZkrY8n](https://imgur.com/xZkrY8n)

---

### Post by oldfred on 2019-03-27
That is showing a Intel Dual T2370. Was there an older model L300, look up of specs are much newer.
That is a much older chip, and may be 32 bit only. It was dual core2 that are 64 bit.

---

### Post by ivan1987 on 2019-03-27
Hi fellows,

Do you have another ideas what I can try or I can bury it?

[-o

---

### Post by mörgæs on 2019-03-27
Too early to give up. 

Have you cleaned the hardware thoroughly? A clogged fan or radiator often causes overheating. 
When this is done I suggest that you install using the minimal ISO. More info in the link in my signature.

---

