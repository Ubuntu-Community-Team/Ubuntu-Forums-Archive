---
title: "Epson scanner not working - Help is needed"
date: 2014-08-01
forum: General Help
---

### Post by markodd on 2014-08-01
Hey there,

I've an "**Epson SX 525WD**" and the scanner stopped working in the 14.04 version of xubuntu/Ubuntu; It was working fine on Xubuntu/Ubuntu 13.10.

I've installed both ***iscan***, ***iscan-data*** and ***iscan-network*** from [here]("http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=24993&DSCCHK=fd5cb71b1b7dcca4b2eba38afa9631e914a5e10f") and [here]("http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=28880&DSCCHK=ec6ec9b0ae7d86aeadf2c0b88252dbe4149a9831").

It is still not working.

Note: It worked once, with "Image scan! for linux", but I want/need Simple Scan to work, and I cannot get "Image scan! for linux" to work again.

Any suggestions?

Thanks in advance.


EDIT: I'm really not interested in being able to scan wirelessly. I only want it to work via usb!

EDIT2: I'm now running Ubuntu 14.04 on my desktop. At the time of this post, I was running Xubuntu 14.04. I still have the problem with the scanner though.

---

### Post by rbmorse on 2014-08-01
Does the scanner show up when you run:

lsusb

from a terminal (make sure it's powered up and connected when you do this)?

---

### Post by markodd on 2014-08-02
It's working (on my laptop)!! What I did was exactly the same as what I did on my desktop, however, on the laptop it works.

Weird. I've both (laptop and desktop) running Xubuntu 14.04. However, I want to install Unity on my desktop. I'll do it and see if the scanner works after that.

EDIT: Please, see the next post. It is **NOT** working on my desktop, and I want it to work ://

---

### Post by markodd on 2014-08-02
It does **NOT** work on my desktop.

Doing *lsusb* gives the following:

```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 2516:0003  
Bus 003 Device 002: ID 045e:0780 Microsoft Corp. 
Bus 003 Device 006: ID 04b8:085e Seiko Epson Corp. PX-503A [ME OFFICE 900WD Series/Stylus Office BX525WD]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I guess the printer/scanner is the second-last line. What should I do now?

EDIT: I think I found what the "problem" is. The only difference between the laptop/desktop (other than, one is using Xubuntu and the other Ubuntu) is that the laptop doesn't have the printer installed. Now, I'm not sure how to "fix" this..

---

### Post by Doj on 2014-08-02
Have you tried "dpkg --purge"ing the package?

Also are you sure you're installing the right version (x86 or amd64)? I've also had problems in the past with drivers not depending on their dependencies properly (a printer), so the package installs but doesn't work.

Try running simple-scan from terminal and seeing the output.

Edit: simple-scan --debug might be helpful

---

### Post by markodd on 2014-08-02
> **Doj said:**
> Have you tried "dpkg --purge"ing the package?

Also are you sure you're installing the right version (x86 or amd64)? I've also had problems in the past with drivers not depending on their dependencies properly (a printer), so the package installs but doesn't work.

Try running simple-scan from terminal and seeing the output.

Edit: simple-scan --debug might be helpful

I removed the packages using the Synaptic Package Manager. Isn't it the same as "dpkg --purge"ing the package? Because I wouldn't know what to name of the package is, I guess I'd have to use Synaptic to find the package name? 

But yes, I did remove the printer package and everything else (scanner software) and installed only the scanner. It's still not working. (I've removed everything using Synaptic, I haven't tried the purge command)

Running simple-scan from terminal just opens the GUI and when I press "scan", nothing happens. No output whatsoever. It just "hangs".. Like it's forever loading..

Doing "simple-scan --debug" got me this:

```
markodd@desktop:~$ simple-scan --debug
[+0,00s] DEBUG: simple-scan.vala:596: Starting Simple Scan 3.12.1, PID=2485
[+0,00s] DEBUG: Connecting to session manager
[+0,03s] DEBUG: ui.vala:1648: Loading state from /home/markodd/.cache/simple-scan/state
[+0,03s] DEBUG: ui.vala:1629: Restoring window to 600x400 pixels
[+0,03s] DEBUG: autosave-manager.vala:64: Loading autosave information
[+0,03s] DEBUG: autosave-manager.vala:258: Waiting to autosave...
[+0,03s] WARNING: autosave-manager.vala:76: Could not load autosave infomation; not restoring any autosaves
[+0,04s] DEBUG: scanner.vala:1443: sane_init () -> SANE_STATUS_GOOD
[+0,04s] DEBUG: scanner.vala:1449: SANE version 1.0.23
[+0,04s] DEBUG: scanner.vala:1510: Requesting redetection of scan devices
[+0,04s] DEBUG: scanner.vala:802: Processing request
[+0,13s] DEBUG: autosave-manager.vala:280: Autosaving book information
[+0,15s] DEBUG: ui.vala:1739: Saving state to /home/markodd/.cache/simple-scan/state
[+2,75s] DEBUG: scanner.vala:338: sane_get_devices () -> SANE_STATUS_GOOD
[+2,75s] DEBUG: scanner.vala:350: Device: name="epkowa:usb:003:004" vendor="Epson" model="Stylus NX625/SX525WD/TX560WD/Stylus Office BX525WD/ME OFFICE 900WD/WorkForce 625 Series" type="flatbed scanner"
[+3,03s] DEBUG: ui.vala:1739: Saving state to /home/markodd/.cache/simple-scan/state
[+4,70s] DEBUG: simple-scan.vala:310: Requesting scan at 300 dpi from device 'epkowa:usb:003:004'
[+4,70s] DEBUG: scanner.vala:1556: Scanner.scan ("epkowa:usb:003:004", dpi=300, scan_mode=ScanMode.COLOR, depth=8, type=ScanType.SINGLE, paper_width=0, paper_height=0, brightness=0, contrast=0)
[+4,70s] DEBUG: scanner.vala:802: Processing request
[+6,20s] DEBUG: ui.vala:1739: Saving state to /home/markodd/.cache/simple-scan/state
[+6,39s] DEBUG: ui.vala:1739: Saving state to /home/markodd/.cache/simple-scan/state
[+6,62s] DEBUG: ui.vala:1739: Saving state to /home/markodd/.cache/simple-scan/state
[+7,39s] DEBUG: ui.vala:1739: Saving state to /home/markodd/.cache/simple-scan/state
[+8,59s] DEBUG: ui.vala:1739: Saving state to /home/markodd/.cache/simple-scan/state
[+10,72s] DEBUG: ui.vala:1739: Saving state to /home/markodd/.cache/simple-scan/state
[+10,88s] DEBUG: ui.vala:1739: Saving state to /home/markodd/.cache/simple-scan/state
[+11,20s] DEBUG: ui.vala:1739: Saving state to /home/markodd/.cache/simple-scan/state
[+13,50s] DEBUG: ui.vala:1739: Saving state to /home/markodd/.cache/simple-scan/state
[+14,72s] DEBUG: ui.vala:1739: Saving state to /home/markodd/.cache/simple-scan/state
[+59,41s] DEBUG: ui.vala:1739: Saving state to /home/markodd/.cache/simple-scan/state
^C

```

In the /home/markodd/.cache/simple-scan/state file there's only this:

```
[window]
width=600
height=400
is-maximized=false

[last-page]
width=595
height=842
dpi=72
scan-direction=top-to-bottom

```

Does it look fine? Any other suggestions?

---

### Post by markodd on 2014-08-03
Comparing my packages in the desktop with the packages in the laptop (using synaptic), I found that the laptop (on which the scanner works just fine) has a package installed that the desktop does not, called: 

```
 libsane:i386
```

So perhaps there's something I installed (32bits) that maybe makes it work? I now need to find it what it is.. Any suggestions?


EDIT: I installed that package from the ubuntu software center, and it's still **NOT** working.. Now I'm all out of ideas.

---

### Post by markodd on 2014-08-04
Oh well, seems like noone can help me. Guess I'll have to dual-boot windows...

EDIT: If someone comes across this thread and you've the same problem, please let me know.. Also, **if you have a fix for this, please let me know! Leave a reply here or PM me.**

---

### Post by canhoto on 2015-01-03
Well, I have the same problem with the EPSON SX 525WD, but with Linux Mint 17.1. I was using elementaryOS before (which was based on Ubuntu 12.04) and my wife was using Linux Mint 16. Scanning was working fine. Both me and her changed for a 14.04 based OS (Mint 17.1 in both cases), and neither me (with my desktop) nor she (with her laptopt) can have the scanner detected (although we can print). 

Have you managed to solve this in your case?

Thanks

---

### Post by markodd on 2015-01-04
> **canhoto said:**
> Well, I have the same problem with the EPSON SX 525WD, but with Linux Mint 17.1. I was using elementaryOS before (which was based on Ubuntu 12.04) and my wife was using Linux Mint 16. Scanning was working fine. Both me and her changed for a 14.04 based OS (Mint 17.1 in both cases), and neither me (with my desktop) nor she (with her laptopt) can have the scanner detected (although we can print). 

Have you managed to solve this in your case?

Thanks

Sadly, I have not. It works on my laptop though, with exactly the same packages as the desktop. (At-least it did, 1 month ago. I reformatted and I haven't tried it again). It's really weird, I'm thinking it might be something hardware related? Is this even possible?

Either way, I don't need it to work on my desktop anymore, I moved my scanner to another room. However, if you find a fix, please let me know!

---

### Post by pdc on 2015-01-08
Hi there canhoto;

if you are still out there: Mint does have its own forums too [http://forums.linuxmint.com/](http://forums.linuxmint.com/) and there is a Printers and Scanners section

let's see if we can get things going here; I would feel you could look at installing the drivers that Epson provide for your device: 

you need to install 

1) the iscan data file first            [COLOR="#008000"]iscan-data_1.33.0-1_all.deb[/COLOR]
2) the main iscan driver
3) a network plugin package

first tell us if you are using a 32bit system please

If you subscribe to a thread, you can get email notification that there is a reply

---

### Post by Mike_Walsh on 2015-01-08
Are you aware that for Epson printer/scanner 'filters' (drivers) to work correctly, that you need to do

```
sudo apt-get install lsb
```

first?

Don't ask me what it does (I honestly haven't got a clue!).....I'm simply following the fine print on the Epson driver download pages. But it DOES seem to work. I believe, if you install the drivers through the Software Centre, that the system will perform this first, BEFORE commencing the printer/scanner driver installations.


Regards,

Mike.

---

