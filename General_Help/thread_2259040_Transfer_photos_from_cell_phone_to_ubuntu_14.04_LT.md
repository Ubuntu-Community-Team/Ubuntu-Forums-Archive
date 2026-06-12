---
title: "Transfer photos from cell phone to ubuntu 14.04 LTS"
date: 2015-01-01
forum: General Help
---

### Post by delanov on 2015-01-01
Currently I use AT&T Z222 and LG A380 cell telephones.  I'm unable to transfer photos from either cell phone using ubuntu 14.04 LTS.  I would appreciate help with this matter. 

Perhaps if I use a different cell phone manufacture, is there any suggestions?

---

### Post by whitesmith on 2015-01-01
Bluetooth, when feasible, usually works. For me it seems simpler to connect phone and computer via a USB cable. What happens when you hook up the pair this way?

---

### Post by delanov on 2015-01-01
> **whitesmith said:**
> Bluetooth, when feasible, usually works. For me it seems simpler to connect phone and computer via a USB cable. What happens when you hook up the pair this way?

There is no indication by ubuntu the phone is connected via usb.

---

### Post by coldraven on 2015-01-01
On my Moto G I have to set the phone's USB to connect as a Camera (PTP) to copy photos.
The Media device option (MTP) does not seem to work with Ubuntu.

---

### Post by delanov on 2015-01-01
> **coldraven said:**
> On my Moto G I have to set the phone's USB to connect as a Camera (PTP) to copy photos.
The Media device option (MTP) does not seem to work with Ubuntu.

Thanks,  I'll give it ago provided the phones I have give that OPTION???  I will post the results tomorrow..

---

### Post by delanov on 2015-01-01
The AT&T Z222 phone does not have an option, that I can find, to set the phone USB to connect as a Camera?  I need to wait to check the LG phone.

---

### Post by 3246251196 on 2015-01-01
I hate this new MTP nonsense tbh. One - of the many - alternatives is to run an ftp server and do things that way.

---

### Post by delanov on 2015-01-01
> **3246251196 said:**
> I hate this new MTP nonsense tbh. One - of the many - alternatives is to run an ftp server and do things that way.

That's a novel approach, I like it :-) 

But I'll need to scratch my head for quite awhile before I'll understand it :-)

---

### Post by entropy1 on 2015-01-01
I have an ATT Z221, and the only way I found was to text message to my gmail account, where instead of typing a message, I select Options > Insert > Picture.  Depending on the picture sizes, I can insert up to 3 pictures per text message.

---

### Post by delanov on 2015-01-01
> **entropy1 said:**
> I have an ATT Z221, and the only way I found was to text message to my gmail account, where instead of typing a message, I select Options > Insert > Picture.  Depending on the picture sizes, I can insert up to 3 pictures per text message.

It's an easy and quick solution for me.  Thank you very much :-)

---

### Post by coldraven on 2015-01-03
I see the USB options only when I connect the cable. That would be the case but I just looked and it seems that I left my phone in the pub last night :(  ooops!

You could install the free app SSHDroid. If your phone is on your home wifi then running SSHDroid will show you an IP address.
In Nautilus select "Connect to server" and type in the address. You can then copy your files via wifi but it is a little slow

Edit: I found my phone in my car. Phew! It is running Android 4.4.4

---

### Post by efflandt on 2015-01-03
While I was still using Ubuntu 12.04 which I could not get MTP to work on at all, on my Android phone (Samsung S3) I installed ConnectBot (ssh client), AndFTP (for sftp client), and SSHServer to be able to connect it with Linux in either direction, as long as the phone was connected to WiFi. I used my Linux ssh keys on the phone (instead of password) for all of those, since I normally have Linux set for keys only.

Although, one thing that did work with the USB cable in 12.04 is that when I was having trouble with my DSL, I could enable tethering on my phone, connect it with USB cable to my PC, and Linux would automatically switch from WiFi to it as though it was ethernet. Of course the phone also worked as a WiFi hotspot (I have a suitable data plan).

When I tried Ubuntu 13.10 on a laptop I had no trouble with MTP on USB and since I recently installed 14.04 on my desktop MTP seems to work fine with that too. The only thing I noticed is that I cannot open files on the phone from Linux, I have to copy them to Linux first to be able to open them.

---

### Post by delanov on 2015-01-03
> **coldraven said:**
> I see the USB options only when I connect the cable. That would be the case but I just looked and it seems that I left my phone in the pub last night :(  ooops!

You could install the free app SSHDroid. If your phone is on your home wifi then running SSHDroid will show you an IP address.
In Nautilus select "Connect to server" and type in the address. You can then copy your files via wifi but it is a little slow

Edit: I found my phone in my car. Phew! It is running Android 4.4.4

I appreciate all responses to my enquiry, they cover a lot of technical methods.  I hope you recovered your phone without difficulty.  Of course I will give each suggestion a go and post back when something works.  

I note you used the term Pub are you in the UK?

---

### Post by delanov on 2015-01-03
> **efflandt said:**
> While I was still using Ubuntu 12.04 which I could not get MTP to work on at all, on my Android phone (Samsung S3) I installed ConnectBot (ssh client), AndFTP (for sftp client), and SSHServer to be able to connect it with Linux in either direction, as long as the phone was connected to WiFi. I used my Linux ssh keys on the phone (instead of password) for all of those, since I normally have Linux set for keys only.

Although, one thing that did work with the USB cable in 12.04 is that when I was having trouble with my DSL, I could enable tethering on my phone, connect it with USB cable to my PC, and Linux would automatically switch from WiFi to it as though it was ethernet. Of course the phone also worked as a WiFi hotspot (I have a suitable data plan).

When I tried Ubuntu 13.10 on a laptop I had no trouble with MTP on USB and since I recently installed 14.04 on my desktop MTP seems to work fine with that too. The only thing I noticed is that I cannot open files on the phone from Linux, I have to copy them to Linux first to be able to open them.

Your technical ability is quite a bit greater than mine, however, even if I never get to the point of transferring;  My enquiry generated a multitude of technical challenges which I will attempt to work through.  I thank everyone for that :-)

---

### Post by Holger_Gehrke on 2015-01-03
Are you using a SD-Card in the LG phone ? If you do it should be simple, just get a card reader (and perhaps an adapter for micro SD to full size SD) and that's that. Just have to make sure that the phones saves photos to the card and not to internal memory.

---

### Post by delanov on 2015-01-04
> **Holger_Gehrke said:**
> Are you using a SD-Card in the LG phone ? If you do it should be simple, just get a card reader (and perhaps an adapter for micro SD to full size SD) and that's that. Just have to make sure that the phones saves photos to the card and not to internal memory.

My computer is an HP that came with windows 7, which I do not use, however I left windows on the machine and dual booted ubuntu.  The machine is equipped with four card slots which accept many different Cards - SD is one of them.  

For general information: #1 slot: Smart Media / xD;  #2 slot: SD/Mini/MMC/RS/Plus/Mobile; #3 slot: Compact Flash 1 / ll / MD;  #4 slot: MS/PRO/Duo/Pro Duo

I like this solution and will purchase an SD-Card and perhaps it will solve the issue.  BTW - I did try to transfer from cell to widows.  No luck, however, windows did download the drivers for the cell ???????

---

