---
title: "Motherboard Bios Unable to access"
date: 2017-05-31
forum: General Help
---

### Post by doomsdaystar on 2017-05-31
After rebooting my pc changing the booting sequence I cannot open my bios settings I tried everything f1,f2,delete,f11 
everything only thing its been able to open is the gnu grub opening while not being able to use my keyboards up and down keys or enter or anything how can I  fix this!?
Motherboard Msi Military Class 4 
Also the old keys to open it were f11 and delete
tried but doesnt work

---

### Post by QIII on 2017-05-31
Hello!

MSI has a lot of "Military Class" motherboards, so that's not terribly helpful.

Do you have the user manual that came with the unit?  Perhaps that will give you an alternative.

---

### Post by doomsdaystar on 2017-05-31
> **QIII said:**
> Hello!

MSI has a lot of "Military Class" motherboards, so that's not terribly helpful.

Do you have the user manual that came with the unit?  Perhaps that will give you an alternative.
i bought it from someone else so i dont know

---

### Post by deadflowr on 2017-05-31
Does it still have Ubuntu installed on the system?
(I know you are trying to nuke Ubuntu from the machine, but not sure where you are with that, currently)
If you can boot into Ubuntu
run
```
sudo dmidecode -t baseboard
```
copy and paste the results here in you do not understand them.

---

### Post by doomsdaystar on 2017-05-31
> **deadflowr said:**
> Does it still have Ubuntu installed on the system?
(I know you are trying to nuke Ubuntu from the machine, but not sure where you are with that, currently)
If you can boot into Ubuntu
run
```
sudo dmidecode -t baseboard
```
copy and paste the results here in you do not understand them.
what will that do?

---

### Post by QIII on 2017-05-31
It will give us some information about your motherboard that may help us help you out.

---

### Post by doomsdaystar on 2017-05-31
> **QIII said:**
> It will give us some information about your motherboard that may help us help you out.
alright ill do it ,but right now im going to sleep

---

### Post by oldfred on 2017-05-31
We asked specifically what motherboard.
If you run that command from terminal in Ubuntu it will tell you what motherboard so you can answer our question.
You have to help us help you.

Many new systems have fast boot in UEFI. 
Fast boot in UEFI assumes no system changes and immediately boots system. Assumed that you then get into UEFI from within Windows & reboot. Or from last item in grub menu.
If nether system boots, often full cold boot, not warm reboot works as then it does a normal boot and gives you just enough time to press keys to get into UEFI.
Cold boot:
Shut down system, remove all power, remove battery if laptop. And hold power switch for 10 sec or so to drain any remaining power. The connect power & boot.

---

### Post by deadflowr on 2017-06-01
> **doomsdaystar said:**
> what will that do?

It'll output a lot of useless junk for the most part, but it should give you the Maker and Model (or Product name) of the motherboard.

---

### Post by doomsdaystar on 2017-06-01
Getting SMBIOS data from sysfs.
SMBIOS 2.8 present.


Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: MSI
	Product Name: H81M-E34 (MS-7817)
	Version: 3.0
	Serial Number: To be filled by O.E.M.
	Asset Tag: To be filled by O.E.M.
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: To be filled by O.E.M.
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0


Handle 0x003A, DMI type 41, 11 bytes
Onboard Device
	Reference Designation:  Onboard IGD
	Type: Video
	Status: Enabled
	Type Instance: 1
	Bus Address: 0000:00:02.0


Handle 0x003B, DMI type 41, 11 bytes
Onboard Device
	Reference Designation:  Onboard LAN
	Type: Ethernet
	Status: Enabled
	Type Instance: 1
	Bus Address: 0000:00:19.0


Handle 0x003C, DMI type 41, 11 bytes
Onboard Device
	Reference Designation:  Onboard 1394
	Type: Other
	Status: Enabled
	Type Instance: 1
	Bus Address: 0000:03:1c.2

---

### Post by doomsdaystar on 2017-06-01
this is what i got

---

### Post by doomsdaystar on 2017-06-01
hello can anyone help me?

---

### Post by oldos2er on 2017-06-01
Please be patient. We have members from all over the world, so it takes time for everyone to see your post.

---

### Post by QIII on 2017-06-01
Please see page 25 of the manual, which can be found and downloaded [here]("https://us.msi.com/Motherboard/support/H81M-E34.html#down-manual").

Is this how you have been attempting to enter the BIOS setup?

---

