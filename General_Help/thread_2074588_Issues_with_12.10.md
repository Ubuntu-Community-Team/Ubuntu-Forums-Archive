---
title: "Issues with 12.10"
date: 2012-10-21
forum: General Help
---

### Post by Hyper Tails on 2012-10-21
Hey guys, I recently install Ubuntu 12.10;

After I installed it via flashdrive, I have been experiencing the following issues:

1) It barely boots into the OS half the time; as it freezes during the boot time.

2) I constantly get an "System has experienced a problem" window

3)I get "error, Check your internet connection" message in the update manager and sometimes the software center (I think).

4) Anywhere I can get some ATI Drivers for this? :confused:

Any help will be thanked.

---

### Post by ~LoKe on 2012-10-21
> **hyper tails said:**
> 2) i constantly get an "system has experienced a problem" window

+1

---

### Post by 2F4U on 2012-10-22
> 2) I constantly get an "System has experienced a problem" window

Can you provide more details about the error. I had a similar problem in 12.04 and the system reported that the GPU was hanging. I found out that this error was totally harmless and ended up by turning off Apport through /etc/default/apport.

> 4) Anywhere I can get some ATI Drivers for this?

What is your graphics card model? ATI stopped supporting certain older model with their recent version of the proprietary driver.

---

### Post by Hyper Tails on 2012-10-22
> **2F4U said:**
> Can you provide more details about the error. I had a similar problem in 12.04 and the system reported that the GPU was hanging. I found out that this error was totally harmless and ended up by turning off Apport through /etc/default/apport.



What is your graphics card model? ATI stopped supporting certain older model with their recent version of the proprietary driver.

> Can you provide more details about the error. I had a similar problem in 12.04 and the system reported that the GPU was hanging. I found out that this error was totally harmless and ended up by turning off Apport through

I contionuosly get a window poping up with that message on my screen, this never happened in 12.04

> What is your graphics card model? ATI stopped supporting certain older model with their recent version of the proprietary driver.

I have an ATI Radeon HD 5770 graphics card.

---

### Post by Hyper Tails on 2012-10-23
bump

---

### Post by awr on 2012-10-23
Hyper Tails,

May I suggest you title your posts with something a little more descriptive than "issues with 12.10", perhaps something like "Freeze during boot/12.10" or similar.  It makes it much easier for other people with similar problems to find an answer, and helps people that know stuff to answer your questions :)

Aside from that.

> **Hyper Tails said:**
> 
1) It barely boots into the OS half the time; as it freezes during the boot time.

At what point does it freeze?  Is there anything on your screen?
Do you have multiple boot options, if so which did you choose?

> **Hyper Tails said:**
>  2) I constantly get an "System has experienced a problem" window

When do you get this error?  Is it a text error during boot, or is it an error in the graphical user interface?  Does the error say anything more?

> **Hyper Tails said:**
>  3)I get "error, Check your internet connection" message in the update manager and sometimes the software center (I think).

Can you connect to the internet in some other way or are you unable to connect to the internet at all?  Does update manager work sometimes and not others?

> **Hyper Tails said:**
> 4) Anywhere I can get some ATI Drivers for this? :confused:

Possibly, but we need to know what card you are using.

---

### Post by Frogs Hair on 2012-10-23
> 4) Anywhere I can get some ATI Drivers for this? 

Have you checked software sources > additional drivers ?

---

### Post by Mark Phelps on 2012-10-24
> **Hyper Tails said:**
> 2) I constantly get an "System has experienced a problem" window
Same here -- Canonical rushed yet another version out the door!

> 4) Anywhere I can get some ATI Drivers for this?

Since you're seeing a desktop, you already HAVE ATI drivers installed -- the default open-source Radeon drivers.

Don't rush into installing restricted AMD drivers.  Folks who have are reporting lots of problems as a result.  AMD is announcing another beta nearly every day.  You should wait a couple of weeks until their beta rate slows down and their drivers become more stable.

---

