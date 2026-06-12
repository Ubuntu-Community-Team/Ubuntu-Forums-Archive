---
title: "Trying to get my scanner to work"
date: 2022-06-02
forum: General Help
---

### Post by jonfisher on 2022-06-02
Fresh install of Ubuntu 20.04 lts

My HP all in one printer that has a scanner in it, well I use to be able to use it.

Document Scanner - finds the scanner, but won't scan
Skanlite - reports finding the scanner failed
Xsane - fails to open the scanner

Seems like something more fundamental is the problem besides the program being used....

(?)

```

michael@michael-HP-EliteDesk-800-G1-SFF:~$ scanimage -L 
device `hpaio:/usb/HP_LaserJet_Pro_MFP_M127fn?serial=CNB9H7FDXQ' is a Hewlett-Packard HP_LaserJet_Pro_MFP_M127fn all-in-one
michael@michael-HP-EliteDesk-800-G1-SFF:~$ 

```

---

### Post by ActionParsnip on 2022-06-02
If you run document scanner as root, does it work (this will highlight access/permissions issues)

---

### Post by jonfisher on 2022-06-02
> **ActionParsnip said:**
> If you run document scanner as root, does it work (this will highlight access/permissions issues)

How do I do that?  I tried:

```

michael@michael-HP-EliteDesk-800-G1-SFF:~$ kdesu skanlite
kdesu: command not found
michael@michael-HP-EliteDesk-800-G1-SFF:~$ kdesu Skanlite
kdesu: command not found
michael@michael-HP-EliteDesk-800-G1-SFF:~$ kdesu XSane
kdesu: command not found
michael@michael-HP-EliteDesk-800-G1-SFF:~$ 

```

Also, even though Ubuntu got my HP printer working without me installing hplip or something else, perhaps hplip or one of these in the software center should be installed?

---

### Post by jonfisher on 2022-06-02
I installed the 3 programs, from the Software center, as included as a screen shot in the last post.

I've rebooted and run all the scanning programs again, with no luck.
 
Sometimes the program will recognize which device the HP all in one is, but it never scans, usually saying "unable to connect to scanner."

Any help would be much appreciated...

---

### Post by jonfisher on 2022-06-04
bump
Still need help getting the scanner on my all in one HP printer to work.  It's the HP Laserjet Pro MFP M127fn 
I have ps-printer-app and hplip-printer-app installed.

When opening the scanner app called "XSane" I get the message "Failed to open devidce 'hpaio:/usb/HP_LaserJet_Pro_MFP_M127fn?serial=CNB9H7FDXQ':Error during device I/O.

---

### Post by aeronutt on 2022-06-05
Scanners are Ubuntu's Achilles heel.

I have a handful of various commands I run to get something working on my HP MFP laser scanner.
I've tried installing the MFP via CUPS and via HPLIP.  Mixed results of course.

Can you scan using the command line?:
> hp-scan

I've also had good results installing the MFP manually using hp-setup, and typing in the IP address manually.
Also, running hp-plugin and/or hp-plugin-ubuntu sometimes fixes the problem.

Also, even when it's working, it fails when it tries to scan an image that creates a file larger than some arbitrary size (10G, I think).
It's messy and frustrating.

---

### Post by mIk3_08 on 2022-06-05
> **jonfisher said:**
> I installed the 3 programs, from the Software center, as included as a screen shot in the last post.
I've rebooted and run all the scanning programs again, with no luck.
Sometimes the program will recognize which device the HP all in one is, but it never scans, usually saying "unable to connect to scanner."
Any help would be much appreciated...
Have you installed the HP printer/scanner driver coming from Hp website? [Click here]("https://developers.hp.com/hp-linux-imaging-and-printing/") for more hp driver details. Regards and Cheers.

---

### Post by kurt18947 on 2022-06-05
If you haven't installed HPLIP, I would certainly try that next. mlk3_08's post has the link.

---

### Post by dragonfly41 on 2022-06-05
This thread reminds me that I must resume my attempts .. again .. to get my Canon scanner working on Ubuntu (and dual boot Windows 10).

Comparing notes:-

I have an old Canon scanner CanoScan LiDE 600F which worked fine on older Windows which I would like to get working on Ubuntu.

I also have separate HP LaserJet 2100/M/TN/

In my attempts to get my Canon Scanner working on Ubuntu I did try VueScan.

[https://www.hamrick.com/linux-scanner-software.html](https://www.hamrick.com/linux-scanner-software.html)

&#8220;Works on Windows, macOS, and Linux&#8221;

[https://www.hamrick.com/download.html](https://www.hamrick.com/download.html)

But my conclusion was that I need to get Canon Scanner working again in Windows 10.

Conclusion. You could give VueScan a try .. but there is a price attached.

[P.S.] Here is list of supported HP scanners.
[https://www.hamrick.com/vuescan/hp.html](https://www.hamrick.com/vuescan/hp.html)

---

### Post by mIk3_08 on 2022-06-06
> **kurt18947 said:**
> If you haven't installed HPLIP, I would certainly try that next. mlk3_08's post has the link.
Thanks a lot kurt18947. Yeah. maybe this will help solve his issue. If you haven't try it, please try it. Regards and Cheers.

---

### Post by jonfisher on 2022-06-06
```

michael@michael-HP-EliteDesk-800-G1-SFF:~$ hp-scan

HP Linux Imaging and Printing System (ver. 3.21.12)
Scan Utility ver. 2.2

Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

warning: No destinations specified. Adding 'file' destination by default.
Using device hpaio:/usb/HP_LaserJet_Pro_MFP_M127fn?serial=CNB9H7FDXQ
Opening connection to device...
error: SANE: Error during device I/O (code=9)
michael@michael-HP-EliteDesk-800-G1-SFF:~$ 

```

---

### Post by jonfisher on 2022-06-06
> **mIk3_08 said:**
> Have you installed the HP printer/scanner driver coming from Hp website? [Click here]("https://developers.hp.com/hp-linux-imaging-and-printing/") for more hp driver details. Regards and Cheers.


I have installed "hplip-printer-app" from the Ubuntu Software Center...

Should I try installing the one from the website also  (?)

addendum:  I've downloaded it from the site.  Waiting for guidance on whether I should install it or not.  Also, it's a ".run" file - not really sure how to execute such a file (?)

addendum 2:  I have the following installed from Ubuntu software:

---

### Post by mIk3_08 on 2022-06-07
> **jonfisher said:**
> I have installed "hplip-printer-app" from the Ubuntu Software Center...
Should I try installing the one from the website also  (?)
addendum:  I've downloaded it from the site.  Waiting for guidance on whether I should install it or not.  Also, it's a ".run" file - not really sure how to execute such a file (?)
addendum 2:  I have the following installed from Ubuntu software:
Try not to install it coming from the Ubuntu software because I don't know why it always encounter to have some issue then. I think it is best to install it via another package manager. ex Flatpak, synaptic and etc. Regards and Cheers

---

### Post by jonfisher on 2022-06-07
> **mIk3_08 said:**
> Try not to install it coming from the Ubuntu software because I don't know why it always encounter to have some issue then. I think it is best to install it via another package manager. ex Flatpak, synaptic and etc. Regards and Cheers

Interesting, this is what is available in Synaptic package manager:

---

### Post by mIk3_08 on 2022-06-08
> **jonfisher said:**
> Interesting, this is what is available in Synaptic package manager: Wow!... cool..... Good Luck! Enjoy using/exploring Linux Ubuntu Operating System. Regards and cheers.

---

### Post by kurt18947 on 2022-06-08
> **jonfisher said:**
> Interesting, this is what is available in Synaptic package manager:
My experience with Synaptic is that if I select the main package, synaptic will select any other required packages.

---

### Post by u2nTu on 2023-02-07
No resolution posted so try:

```

sudo apt install sane-airscan ipp-usb 
```

Copied from [here]("https://askubuntu.com/a/1453948/165265").

---

