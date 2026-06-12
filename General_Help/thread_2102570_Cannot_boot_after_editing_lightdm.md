---
title: "Cannot boot after editing lightdm"
date: 2013-01-07
forum: General Help
---

### Post by SnoopFogg on 2013-01-07
Hi, I have a revo with 12.04.  After trying to set it up to auto start XBMC, the system starts to boot up, then displays messages ending:

- Stopping anac(h)ronistic cron
- Checking battery state 

I tried sudo service lightdm restart but that does not help. Just before the problem started I was following some instructions which suggested I edit /etc/lightdm/lightdm.conf 

[SeatDefaults]
autologin-user=xbmc
autologin-user-timeout=0
user-session=XBMC
greeter-session=lightdm-gtk-greeter

Unfortunately I did not back up lightdm.conf, though I did save it's contents in a file on the desktop (which I cannot now access).

Any ideas how I can get it to boot again?

---

### Post by ibjsb4 on 2013-01-07
Can you get to console?

Ctrl + Alt + F1

Just reinstall lightdm and give it another try.

```
sudo apt-get remove --reinstall lightdm && sudo reboot
```

---

### Post by SnoopFogg on 2013-01-07
> **ibjsb4 said:**
> Can you get to console?

Ctrl + Alt + F1

Just reinstall lightdm and give it another try.

```
sudo apt-get remove --reinstall lightdm && sudo reboot
```

Thanks for the suggestion, but it still hangs at the same stage during boot.  I just presumed that it was the editing of lightdm.  I did make one other change when I edited /usr/share/xsessions/XBMC.desktop

[Desktop Entry]
Name=XBMC
Comment=This session will start XBMC Media Center
Exec=xbmc-standalone
TryExec=xbmc-standalone
Type=Application

Could that have caused the problem?

---

### Post by ibjsb4 on 2013-01-07
Ok, what about using the Live CD to gain access.

---

### Post by Rebelli0us on 2013-01-07
Grub Customizer might fix it if you run from Desktop or USB . File > Change Environment  and select the non-booting partition.

---

### Post by SnoopFogg on 2013-01-08
> **ibjsb4 said:**
> Ok, what about using the Live CD to gain access.

Hi, I'm having some real problems getting the Revo to boot from the USB (or do anything from the USB, and there is no CD/DVD on Revo).  

However, I do have access to the console and can login. What are my options?  Can I reinstall from there?  Is there anything else I can try before that?

---

### Post by steeldriver on 2013-01-08
I'm not surprised that apt-get remove didn't work because by default that doesn't remove conf files - however I was surprised to find that apt-get purge doesn't either!

```
Removing lightdm ...
**Purging configuration files for lightdm ...**
Removing user `lightdm' ...
Warning: group `lightdm' has no more members.
Done.
dpkg: warning: while removing lightdm, **directory '/etc/lightdm' not empty so not removed**.

```However the default /etc/lightdm/lightdm.conf file is only a few lines so you could just open up a text editor in the console (e.g. nano) and write a new one:

```
$ cat /etc/lightdm/lightdm.conf

[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
greeter-setup-script=/usr/local/bin/lightdm-greeter-setup
```Hope this helps

---

### Post by SnoopFogg on 2013-01-09
Hi Steeldriver, I used nano to change the script and typed it exactly as you suggested, but it still won't boot (though I now know how to use nano!)  

Really though that should have worked.  Any other suggestions?  

Cheers

---

### Post by steeldriver on 2013-01-09
sorry don't know what else to suggest - in fact I broke mine trying to figure it out!

---

### Post by SnoopFogg on 2013-01-10
I know you can upgrade, but is it possible to reinstall the same OS from the command line?  I want to use 12.04 LTS but the USB ports don't seem to work and there is no CD/DVD.

---

### Post by SnoopFogg on 2013-01-12
I am unable to boot from the Revo, but can access the command line. Is it possible to reinstall from the command line?    

The Revo does not recognise the 2GB USB I created.  I've tested the USB on my other PC and was able to boot from the USB fine so I don't think there is anything wrong with the USB.

I know you can upgrade from the command line but I'm not sure if that will resolve the problem I am having - Revo boot halts half way through booting until error message:

- Stopping anac(h)ronistic cron
- Checking battery state 

Cheers

---

### Post by SnoopFogg on 2013-01-12
Closing this tread. Managed to reinstall 12.04 using USB creator on an external hard drive rather than USB.  The Revo recongnised this.

---

