---
title: "Private keys for SSH"
date: 2014-04-10
forum: General Help
---

### Post by greeny2 on 2014-04-10
Hello ,I realy need your help ,

I have nanostation M5 that i cant login into it after i enabled ssh and unchecked password authentication without

adding any key in the nano and now when i try to login from putty it asks me for a private key and i dont have that to give it , i was able to pull out the public key from it is there anyway u know to help me login to it

like to convert the public key to a private key that fits ??

---

### Post by lisati on 2014-04-10
I've changed the title of your request to something that might attract more attention from those who are able to help.

As I understand it, private and public keys are usually established prior to using a tool like SSH or PuTTY.

---

### Post by greeny2 on 2014-04-10
Yes exactly my bad i didnt know that i have to generate the keys before I unchecked the bottom for pass authentication 
so my nano was left without keys and now it asks me for a key

---

### Post by Lars Noodén on 2014-04-10
You could regenerate the public key from the private key using [ssh-keygen -yf](http://manpages.ubuntu.com/manpages/saucy/en/man1/ssh-keygen.1.html), if you had the private key, but not the other way around.  If the private key is gone, it is over for that key pair and you need a new pair.  Cracking your way in to the device is not likely to be publicly documented even if it is possible.  

I think your main option at this point is to reset the device to factory defaults and start over.  There was a video for a similar model on Youtube entitled "How to Reset Ubiquiti Devices to Factory Defaults"

---

### Post by greeny2 on 2014-04-10
Thanks u for your reply I get what u mean , MY problem that I disabled  the reset bottom for the device so I cant reset it using it

---

### Post by Lars Noodén on 2014-04-10
Ouch.  If you are good with hardware and have the parts available, this might be an option:

[http://dren.dk/mreset.html](http://dren.dk/mreset.html)

But have you tried querying their forums to be sure of your situation?  Maybe there is an internal switch that would work with the cover off.

---

### Post by Impavidus on 2014-04-10
> **greeny2 said:**
> ... is there anyway u know to help me login to it like to convert the public key to a private key that fits ??
Not unless you have several million years of processor time available (or find a security hole). The basic idea behind public key encryption is the fact that it's practically impossible to find the private key from the public key.

I hope you haven't completely bricked your device.

---

### Post by greeny2 on 2014-04-10
Thank U all I got the answer for what i needed , They told me there is a hardware reset bottom I'll try it, I just needed to know if There is a simple way to crack into the private key and I got the answer,TY.

---

