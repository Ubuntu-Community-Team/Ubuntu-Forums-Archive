---
title: "HP MICROSERVER GEN8 + Ubuntu Server"
date: 2014-11-16
forum: General Help
---

### Post by daemoncesar on 2014-11-16
I'm having a lot of problems with this server.

Already updated the bios.

When I set up RAID1 (Array), the system recognizes two installation disks. And is not recognizing the DRIVE VOLUME (RAID1).

---

### Post by daemoncesar on 2014-11-17
up!

---

### Post by nerdtron on 2014-11-17
Does this server have the RAID utility after the BIOS POST? Is this a dedicated hardware RAID controller or just embedded on the motherboard? Did you initialize/activate the RAID 1 on the BIOS after you created the volume?

If not a using a hardware RAID controller, you'd be better off setting software RAID1 on the ubuntu server installation.

---

### Post by daemoncesar on 2014-11-17
raid onboard.

[http://www.ubuntu.com/certification/hardware/201306-13791/](http://www.ubuntu.com/certification/hardware/201306-13791/)

---

### Post by daemoncesar on 2014-11-17
raind controller b120i

---

### Post by daemoncesar on 2014-11-17
I did test with the hum Archive in pendrive
hpvsa-3.13.0-23-generic_1.2.10-0~17~ubuntu14.04.1_amd64
 

not work !

---

### Post by nerdtron on 2014-11-17
> **daemoncesar said:**
> I did test with the hum Archive in pendrive
hpvsa-3.13.0-23-generic_1.2.10-0~17~ubuntu14.04.1_amd64
 

not work !

I have no idea what you are doing and how far you gone. You can't expect people to instantly help you with this little information.

It would be better is you say, I created a USB boot disk, trying to install this.. and then I see this screen..(then a screenshot), I have these settings currently in the BIOS (screenshot to), I have configured this and I want to configure that...
Details like these matters to us.

It's hard to put ourselves in your situation, especially on specific type of equipment which is not owned by everyone.

---

