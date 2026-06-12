---
title: "nvidia trouble"
date: 2013-01-27
forum: General Help
---

### Post by avoozuk on 2013-01-27
Hello,
 
I am new to Ubuntu. I installed the latest version of the software, and I had the option to use an nvidia proprietary driver from the System Settings > Software Sources > Additional Drivers menu. I selected this driver, and now on rebooting the system I receive three copies of the same error message: 'kvm disabled by bios', and I am expected to login in a command prompt. If I do login, I see nothing but a smaller resolutions blank background with a mouse cursor, but the Unity interface seems to be missing.
 
I would like to use hardware acceleration with nvidia, and I do not know how to correct this problem.
 
Can somebody help me regarding this, please?
 
Thanks.

---

### Post by omeomi on 2013-01-27
If you uninstall the driver, does the problem go away? 

Also, have you tried installing one of the other drivers?

---

### Post by papibe on 2013-01-27
Hi avoozuk. Welcome to the forums ):P

I would start by booting into the BIOS. There's a chance you can solve the problem by activating a setting there.

The particular setting name varies depending on the brand. Take a look at these suggestions [here]("http://www.linux-kvm.org/page/FAQ#.22KVM:_disabled_by_BIOS.22_error") and [here]("http://askubuntu.com/questions/206148/kernel-update-kvm-disabled-by-bios").

Let us know how it goes.
Regards.

---

### Post by avoozuk on 2013-01-27
Thanks for the replies. The card I have is an nvidia geforce 470. The BIOS I have is an ASUS UEFI. I have scanned through the settings in the BIOS utility but cannot seem to find any that match those on the KVM links.
 
I cannot revert back to the normal drivers because logging into Ubuntu now shows me a default 800x600 (perhaps) interface with only the desktop background visible. The application bar is missing, and I do not know the shortcut to shut down or reset so I simply have to turn off the power. I tried a re-install from the CD (I did NOT erase the ubuntu install), but that did not solve the issue at all.

---

### Post by HiImTye on 2013-01-27
try
```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall nvidia-current
```
then reboot

if you're not sure how to get to a terminal, hit *ctrl+alt+f1*. this will take you to tty1 and let you type stuff. to reboot issue
```
sudo reboot
```
or switch back to tty7 using *ctrl+alt+f7* and reboot from there

---

### Post by omeomi on 2013-01-27
> **avoozuk said:**
> I cannot revert back to the normal drivers because logging into Ubuntu now shows me a default 800x600 (perhaps) interface with only the desktop background visible. The application bar is missing, and I do not know the shortcut to shut down or reset so I simply have to turn off the power. I tried a re-install from the CD (I did NOT erase the ubuntu install), but that did not solve the issue at all.

If you get to the login screen press CTRL+ALT+F1, this will get you a console. Then uninstall the nvidia driver by
```
sudo apt-get remove nvidia-current
```

---

### Post by avoozuk on 2013-01-28
> **HiImTye said:**
> try
```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall nvidia-current
```then reboot

if you're not sure how to get to a terminal, hit *ctrl+alt+f1*. this will take you to tty1 and let you type stuff. to reboot issue
```
sudo reboot
```or switch back to tty7 using *ctrl+alt+f7* and reboot from there

That worked. Thank you very much. I just wish I knew some of these commands so that I did not feel so powerless and intimidated every time an error like this occurs. On a side note, I find it slightly strange that I can press the 'enter' key in the Ctrl+Alt_f1 mode to insert a new line even when the OS appears still to be processing something. Is there a reason for that?

---

### Post by papibe on 2013-01-28
> **avoozuk said:**
> On a side note, I find it slightly strange that I can press the 'enter' key in the Ctrl+Alt_f1 mode to insert a new line even when the OS appears still to be processing something. Is there a reason for that?

Ctrl+Alt+F1 gets you to a text mode console, but it does not stop or kill the graphical environment by itself. For instance, you can get back by pressing Ctrl+Alt+F7

Regards.

---

