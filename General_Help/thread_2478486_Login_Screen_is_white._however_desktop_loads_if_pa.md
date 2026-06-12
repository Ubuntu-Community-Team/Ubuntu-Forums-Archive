---
title: "Login Screen is white. however desktop loads if password entered."
date: 2022-08-28
forum: General Help
---

### Post by syednizamudeen on 2022-08-28
Hi all,

I have a weird issue on Lubuntu 20.04 LTS. when Lubuntu boots, I'm greeted with a plain white screen instead of the Login screen. However, If I type the password,  The desktop environment loads without an issue and the computer works as its supposed to be.

If I try to enter recovery mode and boot normally with limited display driver support, I can see a login screen. 

Can anything be done to fix the login screen?? I'm a novice user of Linux, kindly help.

The system is more than 15 years old and its an AMD64 processor and has 2GB of RAM, 

Thanks.

---

### Post by HermanAB on 2022-08-29
You should be able to boot in text mode, log in and then launch LXDE, but how I cannot tell.  This may be something for you to explore.

---

### Post by guiverc on 2022-08-29
A correction should be made to HermanAB's post; Lubuntu uses LXQt and not LXDE (*last eight releases not counting respins*).

The Lubuntu manual page (for 20.04 currently) can be found here - [https://manual.lubuntu.me/lts/3/3.1/3.1.9/sddm_configuration.html](https://manual.lubuntu.me/lts/3/3.1/3.1.9/sddm_configuration.html)

Note:  When Lubuntu 22.10 is released in October; that manual link will contain the Lubuntu 22.04 LTS (*where that page has a different section; Lubuntu 22.04's manual is currently the **stable**manual).  When this change occurs; I'll update [https://discourse.lubuntu.me/t/manual-links-currently-available-20-04-lts-22-04-stable/3242](https://discourse.lubuntu.me/t/manual-links-currently-available-20-04-lts-22-04-stable/3242)*

You didn't say which kernel stack you're using (*GA meaning 5.4 for 20.04, or HWE which is now 5.15 for 20.04.5*) but I did experience some issues before in QA-testing on some video cards (*i386* and *amd64*) with kernels >=5.3 (*which you'll have*) where the easiest option was to replace `sddm` with another DM, ie. use a different greeter.  In this [thread]("https://discourse.lubuntu.me/t/login-screen-flashes/1634/5") you'll find some reference to it, but switching to another DM maybe an easy workaround.

---

