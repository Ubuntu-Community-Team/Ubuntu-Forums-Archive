---
title: "Try Ubuntu 16.04LTS from USB not showing 'try' as option"
date: 2017-06-09
forum: General Help
---

### Post by emonti on 2017-06-09
Hi,

I'm trying to boot from USB stick to see if I can use ubuntu from USB stick. 

I found this page: [https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu) ("**How to create a bootable USB stick on Ubuntu**

")

It then says :

'To create a USB stick from which you can install Ubuntu, you must first [download Ubuntu]("https://www.ubuntu.com/download") '.

I previously downloaded an iso so I don't need to download another one.

Then I followed the instructions which say to use '**Startup Disk Creator'. **All is well so far.

Then I follow the link to :**Try Ubuntu before you install it**


and it tells me...

"Most newer computers can start up from a USB stick. You should see a welcome screen prompting you to choose your language and giving you the option to either install Ubuntu or try it from the USB."


When the machine boots up with the USB stick plugged in, it doesn't give me the 'try it' option. It seems only to provide several ways of installing.


What can I do about this?

I only want to boot Ubuntu 16.04 from USB and have a look at it without touching my hdds. 

Any help appreciated.

---

### Post by oldfred on 2017-06-09
Are you not getting first screen shown here?
[https://www.ubuntu.com/download/desktop/install-ubuntu-desktop](https://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Or are you already in the try mode and have the Unity screen? But with extra install icons?
[https://www.google.com/search?client=ubuntu&channel=fs&q=Ubuntu+unity+desktop+screenshots&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=Ubuntu+unity+desktop+screenshots&ie=utf-8&oe=utf-8)

---

### Post by emonti on 2017-06-09
Yes. I see the first screen. But this is just one of the instruction pages prior to booting from usb stick.

So I have already prepared the usb stick and I'm expecting that when I reboot I will see the try option... but alas... it just thinks I'm only interested in a variety of install options such as configuring partitions and such like. It's a bit confusing.

When I reboot I see no option to 'try ubuntu from usb' as mentioned in the first page you link to. 

I see this in the instructions
[h=3]Using a USB drive?[/h]                Most newer computers can boot from USB. You should see a welcome screen prompting you to choose your language and giving you the option to install Ubuntu or try it from the USB. 

Well... this is not the case. I only see install options. Beginning with language selection and then going on to partition and mounting/unmounting mounted partition. It's not clear why I'm seeing all of that.

---

### Post by oldfred on 2017-06-09
That sounds like you are more into the install screens.

About a third of the way down is a typical live install Unity screen.
Right under the Boot into Live Session.
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by emonti on 2017-06-10
"[COLOR=#000000]That sounds like you are more into the install screens.[/COLOR]"

Exactly. I get the same install screens but they are rendered in a more elementary graphics format... as though the X-Server hasn't started yet. And you are right it takes me straight to the language options... so it has skipped booting into a live/demo version on the usb stick, it seems.  

What do I need to do differently? Any ideas?

---

### Post by oldfred on 2017-06-10
Did you download the server version?
It does not have a live mode.

Edit:
Just noticed this about 2/3 way down on this page, so what tool you use can make a difference:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
> I have been happy using **unetbootin**, because of its high success rate. I also tested Ubuntu's startup disk creator **usb-creator-gtk**, which has the advantage that you reach Ubuntu's first screen, that is skipped by unetbootin

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by emonti on 2017-06-11
> Did you download the server version?
It does not have a live mode.

Oh, man! That was the solution. Thank-you.

I was a little annoyed because of a lack of direction. I guess I could have deduced it from the name of download, but I don't think it's that obvious. There is no mention of which version to use for trying it out.... a newbie would struggle. I did.

Thanks, though.

---

