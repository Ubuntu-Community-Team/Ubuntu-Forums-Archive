---
title: "Minimal install on a computer without Ethernet Cable"
date: 2014-05-27
forum: General Help
---

### Post by Romeu_Tristo on 2014-05-27
I have a really old computer (Compaq Presario 1200) and I would like to try to install Lubuntu on it. I was trying to do the Lubuntu Minimal Install but I realized I needed internet connection. The thing is that this computer doens't even have an ethernet port. All I have that could eventually work to connect to the internet are USB ports and a phone cable port. What can I do? Thanks in advance for any help.

P.S.: I'm not an expert on computers, so try to explain things in a way most people would understand, please.

---

### Post by LastDino on 2014-05-27
I dunno, I don't think you should try Lubuntu with only 128MB RAM. And USB/Phone modem internet connection works too as long as it is connected to internet, I think.   

Maybe, try DSL linux?

---

### Post by Romeu_Tristo on 2014-05-27
I've installed Damn Small Linux but it seems to confusing for me. I saw in Lubuntu's website that "for very old computers, down to 128MB of RAM, a minimal install (with additions later) is the way to go", so I would like to try it. And it's more an experience, rather than trying to get it to work as my main computer.

---

### Post by LastDino on 2014-05-27
So, if you've internet connected by USB or inbuilt Phone modem, I think it should work. Is it not detecting the connection while installation?

---

### Post by Rex Bouwense on 2014-05-27
While Lubuntu has been known to install with 128 Mbs of RAM, I am not sure that you could do much with it other than hold the door open.  Good luck if you want to try for the learning experience.

---

### Post by Romeu_Tristo on 2014-05-27
I've tried to connect my computer to my internet modem by USB and by phone cable, but when I'm running the installation and it gets to the part when I need internet connection I can't connect. And also with the Damn Small Linux installed on that computer, I don't have internet after pluging in the UBS or the phone cable. I guess it should be automatic... at least it is when I connect a computer with ethernet port to my modem.

---

### Post by nknwn on 2014-05-27
Is a connection required when installing lubuntu? I installed Lubuntu from a pen drive the other day and I don't think I needed an internet connection. I skipped that part, choosing to connect later to downloaded some updates. ( The machine did have a network card so that was very easy) 

Your phone socket will be for a dial up modem. You need to configure the connection by enterng a phone number and a password. There are still some dialup services available. You pay for a local rate call of course. Search for 'local rate dialup' or 'free dialup' to get the login details.

---

### Post by mörgæs on 2014-05-27
Before advising people to use a dial-up modem please consider the maximum speed of 56 kb/s = 7 kB/s.

A file of 5 MB takes 731 seconds or 12 minutes to download. In reality a bad signal quality lowers the speed even more.

Must be 14-15 years ago I last used one of these.

---

### Post by LastDino on 2014-05-28
I've used one of those too. And yes, it has maximum speed of 56 kb/s :)

Should be good learning experience.

---

### Post by brian_woods on 2014-05-28
is there any other way to get more speed on that .
56kb/s is not good.

---

### Post by marksmarks on 2014-05-28
I don't know,... try a PCMCIA WiFi card?  However, a tiny Linux version may not understand PCMCIA?

There could be some headaches getting outdated video chips configured correctly.   And no one else around who is still using the same hardware, to help you.



wikipedia says: "...Many original models of the Presario 1200 series ran on AMD K6-2 processors ... A number of Presario 1200 series notebooks exist with Celeron or Pentium III processors as well..."

I thought support for K6 was dropped in Ubuntu and possibly support for P3s as well?  (I may be wrong.)

---

### Post by sudodus on 2014-05-28
I looked at the specs for Compaq Presario 1200. If you have 128 MB RAM you cannot use the current Lubuntu version, 14.04 LTS. See this link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)

If you have 256 MB or more RAM, it is possible (but still below the recommended value) ***to install and use*** the Lubuntu system. But a text screen version of Ubuntu 14.04 LTS can be installed with the ***9w*** installer and will work with 128 MB RAM. It is described in the link above about advanced methods (at the bottom of the page). For example you can use it as a small server (if you can connect to to a wired network (ethernet)), or to learn to use 'the command line interface' of the bash shell.

-o-

You have tried ***DSL***, which is a good alternative and possible to get used to. Other ultra small linux distros are ***Wary Puppy*** and ***Tiny Core***.

Otherwise it might be possible to get a newer and more powerful second hand computer for a low cost. See this link to get tips about what specs are necessary to run a full size modern linux distro
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

---

### Post by Romeu_Tristo on 2014-05-28
From what I understood, installing Lubuntu normally doens't require internet connection. But with "Minimal Install" I think it does. Right?

Ok, I got it, by phone cable it will be a very slow internet connection. And what about the USB? Will it be better? And how can I use it to connect? I tried simply plug the cable between the modem and the computer and it didn't work. Maybe I need to configure something before. Can someone help me?

Thanks for your answers

---

### Post by nknwn on 2014-05-28
I don't really advocate Dialup. Not only is it slow but you pay per minute for the connection. I was only pointing out that that would be the most immediate way to connect using the hardware which appears to be available on that Laptop.

I would suggest getting hold of a WIFI dongle assuming that you have a Wireless router at the moment.
I wonder if someone could suggest a WIFI dongle that works straight out of the box with Lubuntu ...

---

### Post by sudodus on 2014-05-28
> **Romeu_Tristo said:**
> From what I understood, installing Lubuntu normally doens't require internet connection. But with "Minimal Install" I think it does. Right?

If you use the normal mini.iso installer, yes, you need an internet connection. ***The 9w installer installs a portable image, and needs no connection***. But you will get a minimal system. You need a connection to install additional packages.
> 
Ok, I got it, by phone cable it will be a very slow internet connection. And what about the USB? Will it be better? And how can I use it to connect? I tried simply plug the cable between the modem and the computer and it didn't work. Maybe I need to configure something before. Can someone help me?

Thanks for your answers

Your computer has the very old USB 1.1 according to the specs I found via the internet. It is also very slow, but it would be possible to connect an ethernet adapter via a USB 1.1 port. (I did that several years ago with a friend's old Mac PowerPC running Ubuntu 10.04 LTS.)

---

### Post by matt_symes on 2014-05-28
Hi

Is this your first ever play with linux ? 

If it is then i would really recommend not going down this route !

Ditch the computer and get something newer from a second hand shop.

From the questions you are asking, you sound a bit green when it comes to linux.

Please, don't let this be your first experience of linux.

As for internet connectivity, forget it on that old door stop as it'll be too slow unless maybe you can if a plugin pci ethernet adaptor for it.

Can you post a link for the technical specs for it.

I've just been reading that the k6-2 processor may not have had the cmov instruction and, if that is the case, newer versions of lububtu will not run.

Kind regards

---

### Post by mörgæs on 2014-05-28
> **matt_symes said:**
> 
Ditch the computer and get something newer from a second hand shop.


+1.

When a thread about old hardware appears people flock around it to give more or less speculative advice about ways to utilize the stuff. Of course it's a good thing if the hardware is not too old but people should always be willing to post the "sorry, it's a waste of time" answer. 

If one is never posting this answer regardless of the hardware in question it's not really helping.

---

### Post by kalehrl on 2014-05-28
It is possible to install minimal system using Lubuntu alternate and hitting one of the F buttons (may be F4) and choosing minimal install.
This will give you Ubuntu minimal CLI system.

---

### Post by Romeu_Tristo on 2014-05-28
> **matt_symes said:**
> Hi

Is this your first ever play with linux ? 

If it is then i would really recommend not going down this route !

Ditch the computer and get something newer from a second hand shop.

From the questions you are asking, you sound a bit green when it comes to linux.

Please, don't let this be your first experience of linux.

Kind regards

I've installed Linux for the first time 1 or 2 months ago on my main computer and I love it. My computer has never been so fast.
This old computer it's just an old machine I found, lying around in my house, and I would like to try to make it work, just for the fun of it. But thanks for the concern.

---

