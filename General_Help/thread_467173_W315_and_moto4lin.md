---
title: "W315 and moto4lin"
date: 2007-06-07
forum: General Help
---

### Post by justinjstark on 2007-06-07
I'm trying to connect my W315 phone with moto4lin.  My AT Vendor ID, etc are all set right.  I get Phone plugged as p2k.  But when I try to connect,

```

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Form1
PhoneMan
New mode: 2
doActConnect
doActConnect
P2kProc::doConnect()
doActConnect
sendControl Error:[error sending control message: Operation not permitted]
sendControl Error:[error sending control message: Operation not permitted]
(E_getPhoneName: E001)

```

---

### Post by adewale on 2007-06-07
i had a similar problem all i did was to visit the supported phones page of moto4lin and corrected my p2k values then i hit run from my pannel and entered sudo /moto4lin's bin directory can't remember and it worked except i couldn't install applications

---

### Post by justinjstark on 2007-06-07
Nevermind, I managed to get bitpim to work.

---

### Post by Solomoriah on 2007-08-03
> **justinjstark said:**
> Nevermind, I managed to get bitpim to work.
HOW?  What did you do to get it working?  I've been trying for hours...

---

### Post by justinjstark on 2007-08-03
I haven't used it in a while.  But I remember it being a real pain in the *** to get it to read the filesystem.

[http://www.howardforums.com/showthread.php?t=1145121&highlight=w315](http://www.howardforums.com/showthread.php?t=1145121&highlight=w315)

You have to set it to other CDMA phone and you will have to figure out the com port.  There are some tutorials out there so I suggest searching.  THe program itself was very buggy and it took several attempts to get to the filesystem.

EDIT:
My settings were
Com Port: /dev/ttyACM0
Phone Type: Other CDMA phone

You should be able to find your com port in "dmesg" after you plug in your phone, I think.

---

### Post by Solomoriah on 2007-08-06
Ah, so.  Bitpim doesn't seem a bit buggy to me, now that I know how to use it.  I've successfully installed an MP3 ringtone and a MIDI ringtone, as well as a wallpaper.

Now I just have to find the contact list to back it up, since Bitpim doesn't know how to do it automatically for this phone yet.

---

### Post by justinjstark on 2007-08-06
> **Solomoriah said:**
> Ah, so.  Bitpim doesn't seem a bit buggy to me, now that I know how to use it.  I've successfully installed an MP3 ringtone and a MIDI ringtone, as well as a wallpaper.

Now I just have to find the contact list to back it up, since Bitpim doesn't know how to do it automatically for this phone yet.

Nevermind, that was moto4lin that was really buggy.  Bitpim is fine.

I never did find out how to back up the contact list.  There is a file (if you can find it) that has all of the numbers stored in it but I could not find the contact names with which they were associated.

---

### Post by Dogmeat Jack on 2007-08-18
**Note to USB cable users**

Note to USB cable users (p2k), make sure your "AT product ID" is some random number not listed in the "USB View". Otherwise the program will try to connect using AT connection, which won't work. --Voidvector 20:08, 10 September 2006 (PDT)
[edit]
A couple of tips

After reading the "Note to USB cable users" above and after some guessing I was able to make my V3 connect by:

   1. Setting the AT Vendor ID to 22b8
   2. Setting the AT Product ID to a random number (4164 in my case :P)
   3. Setting the P2K Vendor ID to 22b8
   4. Setting the P2K Product ID to 4901 (the auto detection set it to 4902, which wouldn't work)
   5. Clicking on "Switch to P2K"
   6. Connecting to the phone on the main window 


REF: [http://moto4lin.sourceforge.net/wiki/Razr_V3-HELP]("http://moto4lin.sourceforge.net/wiki/Razr_V3-HELP")


 - Making the AT Product ID random worked for me, please follow these instructions. More info is available from the original site

---

### Post by ominous zib on 2007-08-23
OK, so this worked to a point with my L7. Moto4lin is now seeing my phone, but every time I try to connect it says "phone busy - try again later."

Any clues?

---

### Post by ominous zib on 2007-08-24
Here's a bit more detail about my predicament.

I connect the phone to the computer no problem.
I run Moto4lin and click the preferences tab
I enter the details as described in the post above and click switch to P2K mode
The program reports that the phone is connected.
I click OK on prefs pane
When I return to the main screen, the program reports that the phone is disconnected and I cant connect again.

When I now check the phone I find that it has powered off, and the only way to turn it back on is to remove the battery, replace it and power up the phone.

Also, after this happens, the USB port I am using is dead, the only way to get it functioning is to restart the computer. It also kills the internet connect app and a few of my menu bar icon programs, mostly ones concerning I/O of some kind.

For reference I am on 10.4.9 and using a Mainland China flashed L7.

If anyone is able to help me or suggest an alternative program for installing/managing content on the phone I would truly appreciate your help.

---

### Post by crtlbreak on 2008-05-30
hmmmm - just found your thread about this as I am in the same jam - and have been so for days now!
I found a possible resolution - this might be a possibility - do you have Lotus Notes installed on your machine?
I was having similar connectivity issues to my blackberry - and upon removal (uninstallation) of Lotus Notes Client V 8.0 the connectivity with my blackberry was restored.
Hope this helps
Regards

---

