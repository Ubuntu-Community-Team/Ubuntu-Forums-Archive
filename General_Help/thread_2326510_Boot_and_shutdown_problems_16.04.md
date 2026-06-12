---
title: "Boot and shutdown problems 16.04"
date: 2016-06-01
forum: General Help
---

### Post by ewmcnee on 2016-06-01
I just upgraded my Dell Inspiron-7537 to 16.04. It has an Intel Core i7-4500 and an nvidia GT 750m graphics card (which I've never gotten to work with Linux).

Having upgraded, I have limited success booting and shutting down. Sometimes it works fine, but often I get streams of text (faster than I can read), but if often contains the words "nouveau" and "printk messages dropped" and "GPFIFO GPPTR SIGNATURE".

The text just streams up the screen non-stop and the boot/shutdown does not complete.

Does anyone have any ideas?

---

### Post by gordintoronto on 2016-06-02
Upgraded from what? Do you know about nomodeset?

---

### Post by ewmcnee on 2016-06-02
Poor choice of words on my part. I didn't actually upgrade from an older version, it was a clean install.

Yes, I am familiar with nomodeset. When I add it to /etc/default/grub my system boots and shuts down fine, but it grinds to a halt while it tries to draw anything on the screen.

---

### Post by ewmcnee on 2016-06-03
Some extra information:

* The text streaming happens at startup, shutdown, and when logging out or switching accounts. (GDM issues?)
* When I re-installed 14.04, the problem is gone, so my hardware seems fine.

---

### Post by ventrical on 2016-06-03
> **ewmcnee said:**
> I just upgraded my Dell Inspiron-7537 to 16.04. It has an Intel Core i7-4500 and an nvidia GT 750m graphics card (which I've never gotten to work with Linux).

Having upgraded, I have limited success booting and shutting down. Sometimes it works fine, but often I get streams of text (faster than I can read), but if often contains the words "nouveau" and "printk messages dropped" and "GPFIFO GPPTR SIGNATURE".

The text just streams up the screen non-stop and the boot/shutdown does not complete.

Does anyone have any ideas?

How does the live USB work?  Is that working OK?   I am wondering if it is a beta release or 'final' release. The image may be corrupt  or may be a problem with settings in the BIOS. 

regards..

---

### Post by mc4man on 2016-06-03
On  reasonably similar, ( i7-4700MQ   GeForce GT 755M ) have no start up issues ever, do have on occasion restart/shutdown *hangs*, always at the same place. But I'm using a ubuntu session with lightdm. 
Maybe try switching from gdm to lightdm if I'm reading right that you're using a gnome session.

As far as nomodeset  it shouldn't be used when on the Intel iGPU, only if, in your case, using nvidia drivers. With the intel drivers it'll give you llvmpipe which is worthless.

---

### Post by ewmcnee on 2016-06-05
The live USB works fine. In fact, when it does boot after the install, the installed OS works fine. Until I try to log out or shut down. Then I get streams of text like I mentioned above.

I've also tried 15.10, and it gave the same problem. Going back to 14.04 gives a normal boot/log-off/shut-down again. In fact, I tried the latest Mint, and it also had the issue for me.

I also installed [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), and let it run after the install, but that didn't help matters.

I've been using Ubuntu since 2005 and never had I had this happen before.

---

### Post by ventrical on 2016-06-07
as mac4man  suggested..

```

sudo apt-get remove gdm
sudo apt-get install lightdm

```


regards..

---

### Post by ventrical on 2016-06-07
other:

Are you using 64 bit?

If installing lightdm does not work you may have  to try a fresh install. It would be faster atm.

regards..

---

### Post by ewmcnee on 2016-06-07
Thank you for your replies and attempts to help. I appreciate it.

@ventrical:  I am using 64 bit. I have done a fresh install. Almost always do. Also, I made sure that gdm was uninstalled, and that it was replaced with lightdm. No change.

Since the word "nouveau" keeps coming up in the text that streams up the screen (primarily during shut-down and log-out), I think there's a problem with the open-source nouveau driver and my NVIDIA card. I have a GeForce GT 750m, and I've actually never had it working properly. With older Ubuntu's, I've relied on the integrated graphics on the Haswell chip. The NVIDIA card I have requires software switching to be accessed, and that only seems to work with Windows (the OS I purchased the laptop with some time ago). 

Is the (new?) nouveau driver trying to access my GeForce card somehow and causing problems perhaps?  Like i mentioned, 14.04 doesn't have this problem.

---

