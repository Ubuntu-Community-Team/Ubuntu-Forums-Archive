---
title: "Sudden Inability to Boot Ubuntu"
date: 2017-01-28
forum: General Help
---

### Post by harleybronco on 2017-01-28
Standard facts first.

Ubuntu 16.10 dual booted with Windows 10 on a Dell Inspiron Laptop with an AMD processor.

I installed Ubuntu on this box easily enough. (Actually upgraded it from 16.04 to 16.10) Had no problems with it. Was using it normally, then suddenly, I can't boot Ubuntu up. I can still boot up Windows, however. It gets stuck on a screen that says the following:

/dev/sda6: clean, 22672/26894336 files, 3588715/107564288 blocks
_


And that's it. Can't get past that. Suddenly, I can't boot up a live cd or usb to attempt to fix it, either.

I'm stuck...both with bootup and with ideas. Some Googling really got me nowhere. Hoping you guys can.

Thank you in advance!

---

### Post by oldfred on 2017-01-28
Did a Windows update turn UEFI secure boot on or something in UEFI?

You may also in UEFI specifically allow USB boot. If Secure Boot is on that setting may get turned off.

Also fast boot in UEFI may prevent you from pressing correct key to get to UEFI boot menu, often f10 or f12. Make sure that is off.

You need to boot Ubuntu installer and add Boot-Repair.
Then run its report to see if you have issues.
The entry you show is from a fsck of sda6, but with booting it often is just reporting an internal setting saying it is ok, but not running a full fsck.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by harleybronco on 2017-01-28
I've changed multiple settings in the UEFI section. (BIOS?) 

Still can't boot to USB or CD, or the installed Ubuntu.

Here are pictures of each BIOS screen, just in case I'm doing something wrong.

[http://myorlandomovingservices.com/ubuntu/2.jpg](http://myorlandomovingservices.com/ubuntu/2.jpg)

[http://myorlandomovingservices.com/ubuntu/1.jpg](http://myorlandomovingservices.com/ubuntu/1.jpg)


[http://myorlandomovingservices.com/ubuntu/3.jpg](http://myorlandomovingservices.com/ubuntu/3.jpg)[http://myorlandomovingservices.com/ubuntu/4.jpg](http://myorlandomovingservices.com/ubuntu/4.jpg)

---

### Post by harleybronco on 2017-01-28
Never mind! I figured it out!

---

### Post by wildmanne39 on 2017-01-28
Please use thumbnails or url's when posting images because many people have slow or limited connections.

Please post the solution so everyone can benefit from your answer.
Thanks

---

### Post by harleybronco on 2017-01-29
I put the pictures on my own web server so that they wouldn't tax the server on this website, but well enough. I'll do that henceforth.

The solution I came to probably isn't one that most folks would want to do, so I didn't post it.

My windows AND Ubuntu installation were both fairly new, so I didn't have a lot of personal info or programs loaded into either one, and it wasn't a primary use computer, so I basically wiped the whole thing out on both sides, and reinstalled both OS's. In my reading here, however, I decided not to put 16.10 back on, but rather went to 16.04. Many people, as I was reading, were saying that they stick with only LTS versions. I decided to go that route, myself.

---

### Post by oldrocker99 on 2017-01-29
Thanks for the explanation. Please mark this thread as [SOLVED] in the Thread Tools to help other users.

---

