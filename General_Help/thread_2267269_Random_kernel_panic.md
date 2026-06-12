---
title: "Random kernel panic"
date: 2015-02-28
forum: General Help
---

### Post by lui4 on 2015-02-28
First off, this is my first time posting in the Ubuntu Forums, hello! I've used these forums extensively over 18 months getting used to Linux but only just got round to joining - you people here are really great for the valuable info you share!

Right, my problem. Completely randomly earlier whilst using my laptop, I got a kernel panic. Was simply browsing the web, searching something on Google and it happened. It's the second kernel panic I've had since I started using Linux (Ubuntu for about 15 months then Xubuntu for the past 3) and it hasn't happened again (I wasn't doing anything abnormal to try and reproduce it) so it's probably a one-off. However, I'd still like to know what caused it and thereby learn how to get to the bottom of any future kernel panics - my days of fixing others Windows-based systems (as a hobby I must enforce, I'm self-taught over about 5 years) means I get to the root of BSOD issues, but with Linux it's such an infrequent occurence it's not something I'm sure about yet.... I'm sure someone will enlighten me here :) I did search the forums first to see if there was a match to the information below but to no avail.

Here's what I scribbled down when it happened (I assumed this was the right/useful information), not exactly copied as I only quickly wrote what looked important...

Bad RIP value (<null>)
RSP: <ffff8801cf2c3d38>
end trace 6727fa3ba5826d6e
Kernel panic - not syncing: Fatal exception in interrupt
Shutdown cpus with NMI
drm_kms_helper: panic occured, switching back to text console

My system:
Acer Aspire v3-571
6gb RAM
500gb HD
Intel Core i3 2370M 2.4 GHz
Ubuntu(Xubuntu) 14.04 LTS/Windows 7 dual boot (HD partitioned 400gb:100gb Ubuntu:Windows)

Programs running at the time of kernel panic (by memory):
Tor Browser
Mozilla Firefox
Pidgin Instant Messenger
Thunderbird Mail
File Manager

Hope that's enough info to get started?
Thanks :)

---

### Post by kc1di on 2015-02-28
Hello lui4 and Welcome to the Forums,

Not exactly sure lots of things can cause kernel panics they are never good :(

can be a simple as bad ram chip of even dirty connection on ram chip on the hardware side.
I've most often trace it down to Flash content on the net (Had that problem with my wife's Lenovo laptop about a year ago. 
or GPU (Graphics card driver also gives trouble from time to time on my desktop machine I have Nvidia graphic card and can not use the opensource driver with it it just crashes.

Sorry can't be of more help but some one is sure to be along who can - but those are some areas that are possibilities. 
Good luck in finding it.

---

### Post by tgalati4 on 2015-02-28
NMI stands for non-maskable interrupt which means the CPU encountered an error it didn't know how to handle and just shut down.  Try booting without a battery and place the laptop on a table with the power cord taped to the table.  Let the system run for several days in this configuration.  If it is stable, then shut down and put in the battery and run it.

A bad battery (one less than 50% of original capacity) is subject to sudden voltage drops which can cause random shutdowns.

Sometimes the power brick becomes too noisy and fails as well, but that requires buying or borrowing a new power brick.

Welcome to the forums.

---

### Post by sandyd on 2015-02-28
If your really interested, you can use [CrashDumpRecipe]("https://wiki.ubuntu.com/Kernel/CrashdumpRecipe") to do a debug of the panic :)

You can then produce a full crash dump, and do a debug on it

---

### Post by lui4 on 2015-02-28
Thanks for your replies.

The laptop is almost always plugged in when I use it, I barely use it on battery power although it is always connected. I replaced the power brick about 4 weeks ago as the old one failed. Is there a means of testing the battery to determine its current full capacity to compare against its original capacity?

---

### Post by lui4 on 2015-02-28
> **sandyd said:**
> If your really interested, you can use [CrashDumpRecipe]("https://wiki.ubuntu.com/Kernel/CrashdumpRecipe") to do a debug of the panic :)

Wouldn't this only apply if I could reproduce the panic?

---

### Post by sandyd on 2015-02-28
> **lui4 said:**
> Wouldn't this only apply if I could reproduce the panic?

Yes

---

### Post by tgalati4 on 2015-03-01
Run the laptop on battery.  If you get less than 1 hour, then you have a bad battery.  The previous power supply may have failed because you had a weak battery that was pulling all the current.  Does the battery get warm?

---

### Post by lui4 on 2015-03-02
> **tgalati4 said:**
> Run the laptop on battery.  If you get less than 1 hour, then you have a bad battery.  The previous power supply may have failed because you had a weak battery that was pulling all the current.  Does the battery get warm?

Ran it on battery until critical, lasted 3.5 hours and didn't get warm.

---

### Post by tgalati4 on 2015-03-02
That is good news.  The replacement power supply that you purchased, is it the same brand and model as the original or is it a generic power brick?

---

### Post by lui4 on 2015-03-02
Generic replacement adapter

---

### Post by tgalati4 on 2015-03-02
What is the output voltage and current that is printed on the generic power adapter?  What does your laptop require?  What was the original adapter rated for voltage and current?

---

