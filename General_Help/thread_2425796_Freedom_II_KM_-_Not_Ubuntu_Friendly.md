---
title: "Freedom II KM - Not Ubuntu Friendly?"
date: 2019-08-30
forum: General Help
---

### Post by ACMarina on 2019-08-30
Hi All,

I'm trying to get a Blackbox Freedom II KM working with my (X)Ubuntu machine and I'm running into a little trouble.

The device is essentially a KVM without the video - it should allow me to seamlessly control up to 4 computers using a single mouse and keyboard, without having to push any buttons or anything. 

Currently I have a Windows machine on the first input, and it works fine. The *buntu machine is on the second input, a second Windows machine on port 3 and a Mac on port 4. The other 3 work with no trouble (I have rearranged the ports to rule out issues with the #2 port and have no issues there, so it appears to be something with the way it handles the information going from the KM to the PC. 

If I manually select the second channel, I have partial functionality - the mouse connected to the KM never does anything with the cursor on the screen, but the mouse buttons and wheel work as expected. The keyboard works - even multimedia buttons - but the 10-key does not work.

Any ideas?

---

### Post by crip720 on 2019-08-30
Is 10-key for mouse or keyboard, if for mouse just wondering if it needs specific driver that ubuntu doesn' have available/installed yet.  Googling says the switch it self is supposed to be ubuntu/linux friendly.

---

### Post by ACMarina on 2019-08-30
I was referring to the Keyboard's 10-key number pad.. if I have to type numbers I have to use the top row. LSUSB shows the devices, they just don't function fully. Blackbox did tell me that they use Absolute Mouse (no idea what that means) so maybe that's something I could look into? I've only found information in regards to Wacom tablets and that sort of thing, so I'm at a loss of how I would apply that here..

---

### Post by crip720 on 2019-08-30
Would it be possible to hook up mouse and keyboard directly to xubuntu computer and see if they will work?  At least find if problem in switch or mouse.  Do you have the Num Lock on for the ten-keys?

---

### Post by ACMarina on 2019-09-03
Directly plugging in works fine, so there's something that is changing the way the device data gets to the computer - and apparently Ubuntu is the problem child in this . I need to get out another test machine to see if it's distro-specific to Ubuntu or if all linux distros have this struggle..

---

