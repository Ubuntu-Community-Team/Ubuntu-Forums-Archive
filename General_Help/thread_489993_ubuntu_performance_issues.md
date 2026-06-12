---
title: "ubuntu performance issues"
date: 2007-07-01
forum: General Help
---

### Post by devapea on 2007-07-01
I love ubuntu but everything seems to be acting  jerky and kinda slow.  Videos dont run smooth.  Moving images around in Gimp is kinda jerky.  I'm just wondering if this is normal with ubuntu.  My guess is it's Abby normal.  If anybody out thar has a sec to help me out I'd be grateful.
Lemme know what sys info ya need from me. I'd still consider myself a newbie so bear with me.

I can tell you that Im using the I386 and that I have an NVIDIA card.  I could tell ya more if I knew what commands to enter in the terminal.  Thanks

---

### Post by qamelian on 2007-07-02
Odds are that you are using the open-source nv driver for your video card. The link below has some resources relating to installing the binary drivers from NVidia for your card.

[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

Alternately, you can try the Envy script which has helped many users. 

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by devapea on 2007-07-02
Thanks qamelian is will try this and report back.

---

### Post by devapea on 2007-07-02
NV drivers?  Ive actually looking into this in the past and tried to install the correct drivers but I'm unsure about which ones I have.  Here is result from termimal:

deva@deva-desktop:~$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a4)

1. under restricted drivers man. it sez that I have the NVIDIA accelerated graphic driver and its in use.

2. I also installed envy and so now I have the NVIDIA x server settings window on here...

...thanks again for the links but now I still have the same issues.  Maybe I need to configure something in the NVIDIA x server settings? Just a thought.  

Any suggestions from anyone? Thanks

---

