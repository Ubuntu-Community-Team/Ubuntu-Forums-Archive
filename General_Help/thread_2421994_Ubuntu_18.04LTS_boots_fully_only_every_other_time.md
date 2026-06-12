---
title: "Ubuntu 18.04LTS boots fully only every other time"
date: 2019-06-30
forum: General Help
---

### Post by vistauser2 on 2019-06-30
Using 18.04LTS, and last month when it updated and needed to reboot  to 'finish', it locked-up upon reboot and has been doing this ever since  - I go to boot up, it gets to the blank screen where the mouse pointer  shows up, and then the pointer freezes, the light for HD access goes  out, and nothing is responsive - dead.... So, hold down the power  button, reboot, and it goes to the purple page with the count down and  list, defaults, and boots up fine... thankfully there's my VISTA64  laptop that works without all this grief, that I now have to  depend on for daily work - and which btw works flawlessly (but no  'updates' to it to mess it up - too old for microslop). Think I'll have to wipe drive and restore G4L backup image to  fix unless someone knows what is bugging this thing... maybe then just  cut off updates all together as they just seem to cause problems so who  needs them ~ so much for LTS?

  
FYI - The thing did a couple of updates since this issue popped-up,  but none required to be rebooted to 'finish' nor did they fix the  boot/reboot bug... other bugs have seemed to gone away, finally!


  LATER - latest Ubuntu update just required reboot to 'finish'  again... rebooted and hung-up frozen - hit power button, reboots fine  using 'list' w/ timer of purple page. **SEEMS TO BE HANGING EVERY OTHER BOOTUP**
  
WORKAROUND: (FOR MY TOUGHBOOK)...When booting up hit 'esc' when the  'PANASONIC' splash-screen comes up to go see the BIOS terminal output -  Next, when the menu to select CD/HD/USB comes up to boot off of, arrow  down to 'HD' and hit 'enter' - finally, if the purple screen comes up  w/o the Ubuntu menu, hit 'esc' to get it to come up, then hit 'enter'  selecting the default, now hold down power button to reboot. THE NEXT  time around it will not go to the blank purple screen, but rather to the  purple screen with the Ubuntu menu ~ hit 'enter' when it does and it  will FINALLY fully boot (ie not hang) :-\

---

### Post by Dave67 on 2019-07-01
What is the hardware specs for this system? If its a toughbook what model?

---

### Post by vistauser2 on 2019-07-02
> **Dave67 said:**
> What is the hardware specs for this system? If its a toughbook what model?    Panasonic Toughbook CF-73 32-bit system - been doing fine with 18.04LTS for over a year w/o any boot issues 1.86 GHz Pentium - 1 GB SDRAM (DDR2)  - 80 GB H drive (ATA-5) - ATI Mobility Radeon 9000 video card - Max Screen Resolution = 1024 x 768

---

### Post by Dave67 on 2019-07-02
The issues you are going to have is the Panasonic is not a due core processor its a Pentium M single core. Most Linux distributions require duo core processors. Even the light weight distributions require at least a Pentium 3 or 4. 

Ubuntu stopped offering 32bit ubuntu images after 17.10. I would suggest lubuntu 18.04 but even with this distribution for internet access it requires 1GB ram. 

I am installing ubuntu on older systems that Microsoft has abandoned. But I tell potential clients it has to be 64bit due core, and had windows vista and up. 

My suggest is recycle the Panasonic use the vista64 cause its going to work better.

If you want other options thinkpad t420 or t520 ebay has these. I buy from a seller  that I trust which owns his on computer business. There are to thinks to consider new battery and a new hdd cause most sellers do not replace these. Though he does check the hdd for errors.

---

### Post by vistauser2 on 2019-07-02
> **Dave67 said:**
> The issues you are going to have is the Panasonic is not a duo core processor its a Pentium M single core. Most Linux distributions require duo core processors. Even the light weight distributions require at least a Pentium 3 or 4. 

 ...so why would such hardware WORK FINE for over a year? (probably NOT the problem)

> **Dave67 said:**
> Ubuntu stopped offering 32bit ubuntu images after 17.10. I would suggest lubuntu 18.04 but even with this distribution for internet access it requires 1GB ram. 

...got 1GB RAM (probably not the problem either...)

> **Dave67 said:**
> I am installing ubuntu on older systems that Microsoft has abandoned. But I tell potential clients it has to be 64bit due core, and had windows vista and up. 

My suggest is recycle the Panasonic use the vista64 cause its going to work better.

...never gonna happen - the Vista64 is a SONY 'VAIO' laptop working flawlessly, and like my older Windows 98 [1st ed only] desktops that also work flawlessly, is priceless! I have one XP machine for computational fluid dynamics applications like fire modeling, and for the newer DVD games, AutoCAD, etc.

> **Dave67 said:**
> If you want other options thinkpad t420 or t520 ebay has these. I buy from a seller  that I trust which owns his on computer business. There are to thinks to consider new battery and a new hdd cause most sellers do not replace these. Though he does check the hdd for errors.

...but thanks anyway!):P

---

### Post by uRock on 2019-07-02
> **vistauser2 said:**
> ...got 1GB RAM (probably not the problem either...)

Dave was writing about **Lubuntu** not Ubuntu. Ubuntu requires at least 2GB and a least a dual core processor.

[Minimum Requirements for Ubuntu]("https://help.ubuntu.com/community/Installation/SystemRequirements") 

You can check your system's logs for errors that may have been stored for more information on what is happening.

---

### Post by Dave67 on 2019-07-03
Some reading 

[https://www.techrepublic.com/article/ubuntu-19-10-drops-32-bit-support-angering-linux-users/](https://www.techrepublic.com/article/ubuntu-19-10-drops-32-bit-support-angering-linux-users/)

The requirements for ubuntu 18.04 are clear. 

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by vistauser2 on 2019-07-04
> **uRock said:**
> Ubuntu requires at least 2GB and a least a dual core processor.

Ubuntu 18.04LTS been working for over a year with this hardware... machine built for XP :)

> **uRock said:**
> You can check your system's logs for errors that may have been stored for more information on what is happening.

would not know where to find any relevant logs... much less what they mean :confused:

---

### Post by vistauser2 on 2019-07-15
> **Dave67 said:**
> The requirements for ubuntu 18.04 are clear. [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

A good "rule of thumb" is that machines that could run **XP**, Vista, Windows 7 or x86 OS X will almost always be a lot faster with Ubuntu *_even if they are lower-spec than described below_*.
[h=2]Ubuntu Desktop Edition[/h] 
[LIST]
[*]2 GHz dual core processor 
[*]2 GiB RAM (system memory) 
[*]25 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach) 
[*]VGA capable of 1024x768 screen resolution 
[*]Either a CD/DVD drive or a USB port for the installer media 
[*][Internet access]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript") is helpful 

[/LIST]

---

### Post by uRock on 2019-07-15
> **vistauser2 said:**
> Panasonic Toughbook CF-73 32-bit system - been doing fine with 18.04LTS for over a year w/o any boot issues 1.86 GHz Pentium - 1 GB SDRAM (DDR2)  - 80 GB H drive (ATA-5) - ATI Mobility Radeon 9000 video card - Max Screen Resolution = 1024 x 768

> **vistauser2 said:**
> A good "rule of thumb" is that machines that could run **XP**, Vista, Windows 7 or x86 OS X will almost always be a lot faster with Ubuntu *_even if they are lower-spec than described below_*.
[h=2]Ubuntu Desktop Edition[/h] 
[LIST]
[*]2 GHz dual core processor 
[*]2 GiB RAM (system memory) 
[*]25 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach) 
[*]VGA capable of 1024x768 screen resolution 
[*]Either a CD/DVD drive or a USB port for the installer media 
[*][Internet access]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript") is helpful 

[/LIST]
Having had Windows XP doesn't negate the minimum system requirements.

This message when logging in via SSH;```
Welcome to Ubuntu 18.04.2 LTS (GNU/Linux 4.15.0-54-generic x86_64)

 ....

[B]Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.[/B]

```

---

### Post by vistauser2 on 2019-09-08
OK - so, today it updates and asks to reboot... told it I'll shut down later.


  When I did, and then rebooted, the thing looked like it crashed -  kept going on about fsck not being able to work... rebooted and back to  terminal screen with the same error (eg extent tree ... level 2  ...narrower? usb malfunctions...), but this time I typed in **"fsck sda1"** and it ran thru asking to do a bunch of repairs... kept just sayin' 'yes' and let it finish back to terminal screen...


  Rebooted (cold - hold down power button) and it came up without the  hang... been booting without my work around and without hanging!!!


  BACK TO **"NORMAL"** bootups :-) Boots up now without the circus act~

...and nothing to do with system minimum requirements!

---

### Post by mörgæs on 2019-09-08
Good, if the problem is solved please mark the thread so.

---

