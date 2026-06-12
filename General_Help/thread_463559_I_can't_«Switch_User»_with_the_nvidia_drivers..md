---
title: "I can't «Switch User» with the nvidia drivers."
date: 2007-06-03
forum: General Help
---

### Post by loathsome on 2007-06-03
Hi there,

If I use the «Switch User» option, I am unable to login again - the screen just goes black. Sometimes I can press CTRL+ALT+F1 (or equivalent) to access the terminal and eventually kill my shell or something, but most often I have to preform a hard reboot (or ALT+SysRq+B).

Is this a bug in 'gnome-screensaver' or something? It doesn't happen which screensaver I'm using, it happens all the time.

This does **not happen when using the vesa** drivers. Thanks a lot for your replies!

---

### Post by JulianRoot on 2007-06-03
Try
```
sudo dpkg-reconfigure xserver-xorg
```
Maybe it helps.

---

### Post by loathsome on 2007-06-03
> **JulianRoot said:**
> Try
```
sudo dpkg-reconfigure xserver-xorg
```
Maybe it helps.
Thanks, but I don't see how that could help.

THOUGH, I've found out exactly what causes this; **Beryl!** (that also explains why it doesn't happen with vesa ;))

I am able to login if I kill beryl and then log back in. So, anything I could do to solve this, or do I just have to live with it? I mean, it's clearly not Ubuntu's fault, seeing it's a third-party application that does this.

Many thanks.

---

### Post by loathsome on 2007-06-03
Hmm - seems like this also happens with Compiz that comes shipped with Ubuntu.

---

### Post by JulianRoot on 2007-06-03
I'm using Beryl and it works. But I have got an ATI graphic board...

---

### Post by FuturePilot on 2007-06-03
Hmm. I have this problem too when running Compiz. I thought it might have something to do with that. Probably it can't run 2 separate instances of itself.
I've filled a bug report 
[https://bugs.launchpad.net/ubuntu/+bug/112518]("https://bugs.launchpad.net/ubuntu/+bug/112518")
Maybe I should file it against Compiz.

---

### Post by louieb on 2007-06-03
go to [Bugs in Ubuntu]("https://bugs.launchpad.net/ubuntu")  and look up switch user. Feisty has its problems. Fast user switching works great in Dapper. but froze up both computers i had Feisty on. Don't think it has anything to with ATI or Beryl.

---

### Post by loathsome on 2007-06-03
Hmm.

I'm working on this issue, and I hope I'll find the root of this problem.

If anybody else got input - well, you know what to do ;)

In the meantime, is there any way to disable the whole switch user thing? Just to prevent someone in my family from ending up with a black screen.

---

### Post by sycorax on 2007-06-05
Hi,

I can confirm this bug on
- fesity using compiz
- edgy using beryl

On edgy I could fix it by de-activating the option 'sync to vblank' in the Beryl settings.

---

### Post by loathsome on 2007-06-05
> **sycorax said:**
> Hi,

I can confirm this bug on
- fesity using compiz
- edgy using beryl

On edgy I could fix it by de-activating the option 'sync to vblank' in the Beryl settings.
Thanks I'll try that as soon as I'm home! (works perfectly on my Vaio)

---

### Post by darwin81 on 2007-06-06
I too have this problem. When I use the Switch User function, it brings me to the Login Screen and I can log into another account. Then when I log out of that account I get a blank screen with just the cursor working. I tried de-activating the option 'sync to vblank' in the Beryl settings like sycorax suggested and then I can get to the login screen when I log out of the second account, but when I try to log into the first account again I get a blank screen with just the cursor.

---

### Post by loathsome on 2007-06-06
> **darwin81 said:**
> I too have this problem. When I use the Switch User function, it brings me to the Login Screen and I can log into another account. Then when I log out of that account I get a blank screen with just the cursor working. I tried de-activating the option 'sync to vblank' in the Beryl settings like sycorax suggested and then I can get to the login screen when I log out of the second account, but when I try to log into the first account again I get a blank screen with just the cursor.
Yeah, that blank thing was already enabled and did nothing.

Oh well.

---

### Post by oiper on 2007-06-12
I too am having this problem. Seems that compiz is the cause for me. I'm using an Nvidia card. :(

---

### Post by loathsome on 2007-06-13
Let's hope this is fixed when Gutsy is out!

---

### Post by eye208 on 2007-06-13
I'm having the same problem with fglrx (8.34.8 from repository, without Compiz/Beryl).

---

### Post by ushills on 2007-06-13
I originally posted this in absolute beginners but found this thread.

I have a problem with Ubuntu, when I log in as a secondary user from the start screen and then log out, when I try to log in under my admin user account the sceen goes black. 

Eventually a grey box that covers a quarter of the screen appears, however, I cannot so anything but restart X with CRTL>ALT>BKSPCE. 

If I then try to login again the same happens and only a complete restart gets ubuntu working again.

I have delete the secondary user account and re-created it afresh but the same problem exists, the problem occurs with both kernel's that I have under Feisty Fawn.

How can I solve this as I do not want to reinstall.

I did have beryl but uninstalled it, I have configured Xorg and use the ATI drivers, this setup was working fine under Fiesty until a week ago, however the provious kernal exhibits the same behavior if I boot with that.

---

