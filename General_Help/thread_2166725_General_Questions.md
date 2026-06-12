---
title: "General Questions"
date: 2013-08-10
forum: General Help
---

### Post by Jason_Maynor on 2013-08-10
Hello everyone, let me start by saying thanks for taking time to read this. Before I ask my question I want to let you guys know I am a computer tech, I worked on Windows systems and Mac systems until now, I just decided to start diddling with Linux. I am not afraid to dig deep into the kernel  or do whatever needs to be done so you guys dont have to baby talk me :P If I dont understand Ill ask or look it up :D

For starters I am having a bit of an issue with my WiFi card on both my Tower and my Laptop. (Yes I decided do dual boot both tower and Laptop :P ) 
It works fine for awhile, but at completely random times it will disconnect, and then constantly ask me for the WiFi key. I keep typing it in, I know it is the right key, but constantly says wrong key and will not connect.. Sometimes I can disable WiFi and re-enable it and it will work, other times I have to completely restart the unit. I know its not my router because my Windows unit that is on at the same time has no issues what-so-ever during all this, and never does. I can browse the net without any issue. 

Another question I have, does anyone have any real experience with Crossover, or Wine ? I would really really like to try out gaming on the Linux platform. To be quite honest I am tired of windows and I want to completly 100% replace it. So far from what I have been seeing on this setup its nice, I like the UI and how it is all layed out, but unfortunately for me its performance on gaming is absolutly Critical. So any advice on any of that would be appreciated. Thanks

There was a few other issues that I was going to ask, but they have not shown thier ugly head for quite awhile, and as a result my brain conveniently forgot about them :P

---

### Post by Petro Dawg on 2013-08-10
Since you are on these forums, I'm assuming you are using Ubuntu or one of its derivatives, it might be helpful if you let us know the flavor and version of Ubuntu you are using.   

I find it interesting you having the same issue on two separate network cards, are they the same brand?  

Also, do you login to Ubuntu automatically or do you provide a password at the login screen each time?

---

### Post by Jason_Maynor on 2013-08-10
Well I just ran into a completly new issue... I am trying to install this neat little addon on both my Linux systems.

[http://www.noobslab.com/2013/07/deepin-software-center-version-30-and.html](http://www.noobslab.com/2013/07/deepin-software-center-version-30-and.html)

I followed the commands to the T
Terminal Commands:
```
sudo add-apt-repository ppa:noobslab/deepin-sc 
sudo apt-get update
sudo apt-get install deepin-software-center

``` 

It worked fine on my Laptop, but my Desktop it wont..

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-security/Release](http://archive.ubuntu.com/ubuntu/dists/raring-security/Release)  Unable to find expected entry 'main/binary-1386/Packages' in Release file (Wrong sources.list entry or malformed file)

That is the error therminal dumps at me after the sudo apt-get update command... and it will not let me download it from there on... But works great on my laptop....

---

### Post by Jason_Maynor on 2013-08-10
Yes two separate networks cards I agree it is a bit strange, No my windows systems do not disconnect at all, or if they do they re-conect so quickly and without issue that I dont even notice it.

I am currently using Ubuntu 13.04

And I do login Automatic. I must admit the constant asking for passwords is getting quite annoying...

---

### Post by Petro Dawg on 2013-08-10
> **Jason_Maynor said:**
> Yes two separate networks cards I agree it is a bit strange, No my windows systems do not disconnect at all, or if they do they re-conect so quickly and without issue that I dont even notice it.

I am currently using Ubuntu 13.04

And I do login Automatic. 

Ok, the reason I ask about the automatic login is that some programs will ask for a "keyring password" that is different than the password you use to login to what ever service you are actually trying to use (ie, account passwords, router passwords, ect.)  I believe if you log in to Ubuntu using your password each time, the keyring stuff goes away.  It may not solve your issue, but it's worth a shot.


> **Jason_Maynor said:**
>  I must admit the constant asking for passwords is getting quite annoying...

Ubuntu definitely asks for passwords way more than windows, but its a small price to pay to be virtually immune to viruses; IMO.

---

### Post by Jason_Maynor on 2013-08-10
I do have to input my keyring password once per login session, but it only asks for it once I start the system up

---

### Post by Petro Dawg on 2013-08-10
> **Jason_Maynor said:**
> I do have to input my keyring password once per login session, but it only asks for it once I start the system up

I just wanted to be sure your weren't getting the keyring and your network passwords mixed up (a similar issue threw me for a bit the first time I ran into it).  I was thinking perhaps after the connection is dropped the keyring password might need to be re-entered before the system is allowed to enter the router password.  Again, manually entering your password at login for each session will determine if this is indeed the issue (if you are needing to enter a keyring password each time, you might as well manually login anyway).

---

### Post by Jason_Maynor on 2013-08-10
Yea I read each dialog box to make sure what it is, I need to teach myself linux anyways so its the best way :D

---

### Post by JKyleOKC on 2013-08-10
> **Jason_Maynor said:**
> I am currently using Ubuntu 13.04.Is it the 32-bit version, or the 64-bit one? I ask because the error message indicates it's looking for a 32-bit package and not finding it; it's possible that you have a bit-ness mismatch with the new program on your desktop, but not on the laptop.

Packages that include "i386" in their names are 32-bits, while those with "amd64" are 64-bits. While the help pages used to say that 32-bit versions were recommended, that's no longer the case -- and 13.04's 32-bit version requires PAE capability from the CPU. Since your systems are running, that's obviously not the problem here, but it's good to know. Especially when installing things from sources other than the official repositories, the kind of mystifying result you're seeing is not uncommon...

---

### Post by Jason_Maynor on 2013-08-11
Both systems are running 64 bit

---

### Post by Jason_Maynor on 2013-08-11
Ok so I went all day with no WiFi issues at all on both systems, but now out of the blue my Tower disconnected from the Wifi, and no refuses to re-connect with it. I tried re entering the password, restarting the system, Deleting the connection, Disabling WiFi .. For whatever reason, I cannot conect to my Router at all with my tower.. Now dont say its the routers fault, I am posting this through the very same router I am trying to connect to on my tower using my laptop, so I really don't think its the Router

---

### Post by Petro Dawg on 2013-08-11
Just a list things I would think to check...

Is your router equipped with a firewall that might be blocking you (correct ports open)?

Are your IPv4 and IPv6 settings correct (static vs dynamic, ect.)?

Is the router speed set to a compatible speed for your network cards (B, G, or N)?

Are you using the correct security protocol (WEP vs WPA, ect)?

Have you installed any network related utilities since your fresh install?

---

### Post by Jason_Maynor on 2013-08-11
> **Petro Dawg said:**
> 
Is your router equipped with a firewall that might be blocking you (correct ports open)?
It is not

> **Petro Dawg said:**
> 
Are your IPv4 and IPv6 settings correct (static vs dynamic, ect.)?
Yup

> **Petro Dawg said:**
> 
Is the router speed set to a compatible speed for your network cards (B, G, or N)?
It is set to N which is good for my Adapter

> **Petro Dawg said:**
> 
Are you using the correct security protocol (WEP vs WPA, ect)?
WpA and it works fine with everything else, and I am inputting it correctly


> **Petro Dawg said:**
> 
Have you installed any network related utilities since your fresh install?
Negative

---

### Post by wildmanne39 on 2013-08-11
Really it is best to have one issue per thread per the CoC. I recommend starting a thread on the wifi issue in the networking section you will receive more help there for wifi.
Thanks

---

