---
title: "&quot;Try Kubuntu15.10&quot; asks for password???"
date: 2015-11-20
forum: General Help
---

### Post by ags40 on 2015-11-20
I have installed and working perfectly Kubuntu LTS 14.04. Two days ago I try to install Kubuntu 15.10 in the "Try  Kubuntu" mode to see how it works. Well, very interestingly, after installation is asking me for a password. I press return and is not taking "Enter" for an answer. Any help would be apppreciated. Thanks.

---

### Post by cariboo on 2015-11-20
Are you typing a password before pressing Enter?

---

### Post by Topsiho on 2015-11-21
[COLOR="#008000"]***After installation***[/COLOR] it is normal that you have to enter your password when logging in or altering something in the system.
It is the password that you had to give (twice) during the install.

So I don't see any problem here :)

Topsiho

---

### Post by sudodus on 2015-11-21
Please describe how you installed Kubuntu!

Did you install it via clicking on the icon on the desktop and getting into the installer program (ubiquity)? See the attached picture! In that case you should have been asked to select a user name and a password (entered twice). And you should use a real password with at least 6 characters (more characters and 'non-letter' characters add the quality of the password).

Or did you 'install a live system' into a USB pendrive or into an internal drive with a tool like the unetbootin, mkusb, pendrivelinux?

See these links

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by ags40 on 2015-11-21
When you instaall in the "Try Kubuntu" mode you are not asked for a password. "Try Kubuntu" mode goes to RAM, when you turn the computer off everything is gone. I was trying to see how 15.10 worked. If it was worth it to upgrade.

What you say is if you install to the HD, not when you install in "Try Kubuntu" mode, that goes to RAM.

I installed from both DVD and USB. Both take you to a screen that lets you choose, install your HD or just try the distribuition: "Try Kubuntu" mode goes only to RAM, this install never asks for a password.

---

### Post by sudodus on 2015-11-22
I agree with your posts #5, 6, 7. But I still do not understand what was the problem described in post #1.

If you install directly (instead of "Try Kubuntu"), or if you install via the desktop icon (illustrated by the attached screenshot in post #4), you start the same installer program (ubiquity), and you make the same kind of installation. Both of these installations should ask for password.

---

### Post by Topsiho on 2015-11-22
I guess the word "install" is not used correctly here. Installing is not the same as just trying it and loading it into RAM.

When just trying *ubuntu you are not asked, normally, for a password. Why you are asked for a password, when trying the *ubuntu, is a mystery to me, as you are not supposed to have one.

Topsiho

---

### Post by ags40 on 2015-11-22
A live CD (or USB) has two options: one that installs itself in RAM and it does not affect at all the contens of your computer, it is to "try" the distribuition, to see how it works it; this one at no time asks for a password, it just runs and you have all the options available, software, terminal, etc., including the icon that you refer in your attachment. If you use it, the install proper starts. You create your partitons, time zone, passwords, etc, etc. You are puting the actual OS on your HD. After reboot asks for your name and password.
The "try" mode shuld not ask for a password, if it does entering <RETURN> is enough.

---

### Post by sudodus on 2015-11-22
If you log out from the live session (not shutdown, not reboot, 'only' logout), you will be asked for user name and password. This is user 999, in Kubuntu its verbose user ID is kubuntu, and the password is (probably) blank (only the Enter key). At least that is how it works in Lubuntu.

Please explain in which situation you had to enter a password, and blank (only the Enter key) did not work :-)

---

### Post by ags40 on 2015-11-22
One minue ago: With USB 3.0 fron ISO image (tested write and hash). 

1 - I pick start Kubuntu
2 - Some seconds later multicolored screen appears
3 - Some seconds (something is loading)
4 - The options, in perfect graphics, of: "Try Kubuntu" and "Install Kubuntu" appear
5 - I pick "Try Kubuntu". KDM loads plasma. 
     At center of screen: Live session user. Just under it two rectangles: 'password' and 'login'
     At left rectangle showing 'plasmoid' with dropdown menu offering 'failsafe'.
     At right the icons of: 'Reload' and 'Shutdown'. 
6 - The shutdown botton does not offer the option of 'logout'. No dropdown menu, sends you to the screen of 30 seconds delay.

As an aside, I have fully installed Kubuntu LTS for my daily work. Thank you very much.

---

### Post by sudodus on 2015-11-23
I tested with a Kubuntu iso file that I have already, 14.04.1 LTS. I will download and look at 15.10 now, to look for a change, that is probably a bug.

---

### Post by sudodus on 2015-11-23
I made a USB boot drive from kubuntu-15.10-desktop-amd64.iso

```
sudo -H mkusb kubuntu-15.10-desktop-amd64.iso
```

and booted it. Items 1-4 in post #10 match.

> 5 - I pick "Try Kubuntu". KDM loads plasma.
At center of screen: Live session user. Just under it two rectangles: 'password' and 'login'
At left rectangle showing 'plasmoid' with dropdown menu offering 'failsafe'.
At right the icons of: 'Reload' and 'Shutdown'.
6 - The shutdown botton does not offer the option of 'logout'. No dropdown menu, sends you to the screen of 30 seconds delay.


At item 5 I pick "Try Kubuntu". KDM loads plasma and I arrive at the 'logged in' desktop ready to go. There is nothing at the center of the screen, only the desktop folder thingy at the top left, and it contains the 'Install Kubuntu 15.10' icon. See the attached screenshot.

I cannot reproduce your problem, not in BIOS mode and not in UEFI mode.

-o-

- Are you using the 64-bit version?

- Have you checked with ***md5sum*** that the iso file was downloaded correctly? See [UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

- In BIOS mode, when you see the small symbols at the bottom of the screen, press a key, for example the Enter key. Select language, and at the next screen, select 'Check disk for defects'. It should finish with 'Check finished: no errors found'.

- In UEFI mode you will arrive at a grub menu with only three lines to select

Start Kubuntu
OEM install (for manufacturers)
Check disk for defects

Select 'Check disk for defects'. It should finish with 'Check finished: no errors found'.

- Which tool did you use to create the boot drive?

- Could there be a problem with the driver for graphics or wifi, that confuses the startup sequence, and brings you to a login screen?

---

### Post by ags40 on 2015-11-23
I will do a new USB with: sudo -H mkusb kubuntu-15.10-desktop-amd64.iso
This is what I used: dd bs=4M if=/media/data_b3/ISO_Linuxes/kubuntu-15.10-desktop-amd64.iso of=/dev/sdg
I'll keep you posted. Thanks for everything.

---

### Post by sudodus on 2015-11-23
Have you tested the md5sum of the iso file?

Your dd command may be risky, but when you set it correctly it is very reliable. mkusb uses dd under the hood. So I don't think that is the problem. But mkusb wraps a safety belt around dd, so it is worth using it (instead of dd directly).

---

### Post by ags40 on 2015-11-23
I tried with the mkusb tool (nice liitle tool). Nothing, everything the same. Yes I did check the md5. So I'm giving up, I already installed the last Sabayon monthly and already had a taste of how the evolution of plasma goes.
Thank you very much, you're quite a great guide. See you in next releases.

---

### Post by sudodus on 2015-11-24
Sorry that I could not help.

Maybe if you want another try:

Could there be a problem with the driver for graphics or wifi, that confuses the startup sequence, and brings you to a login screen? In that case you should try with some boot options, for example nomodeset, but you could try several of those suggested in the following links and links from them.

[Is the computer running in UEFI mode or in classical BIOS mode?](http://ubuntuforums.org/showthread.php?t=2230389&p=13370798#post13370798)
[**Boot options**](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

---

