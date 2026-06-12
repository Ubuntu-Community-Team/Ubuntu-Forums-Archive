---
title: "updating Transmission and connections"
date: 2022-06-04
forum: General Help
---

### Post by jgw on 2022-06-04
I am occasionally getting an error that I am asking for too many connections.  I am using usenetserver and they give me 20 connections.  I have sabnzbdplus set for 16 connections to try and fix that problem.  Then I thought I had better check on Transmission as that might be causing the problem.  I took a look at transmission (haven't messed with that for a very long time)  The only thing that I thought might be a problem is the settings in "download sharing data ...." which is set for 30.  I have not changed anything and figured I had better ask why somebody else might thing of my problem.  

While looking around I found that there is a newer version of Transmission.  I am running with version 2.94 and the newer version is 3.0   I thought this is strange as the newer version is over 2 years old and Ubuntu seems to be sticking with the old version.

All that being said I am not so sure I should update so I thought I would also ask about that one. 

Thank you............

---

### Post by #&amp;thj^% on 2022-06-04
I haven't used Transmission for years now, but upgrade to 3.0: [https://www.omgubuntu.co.uk/2020/05/install-transmission-3-0-ubuntu-ppa](https://www.omgubuntu.co.uk/2020/05/install-transmission-3-0-ubuntu-ppa)
EDIT I forgot to add this suggestion>> Disabling UTP  to try.

---

### Post by Impavidus on 2022-06-04
> **jgw said:**
> 
While looking around I found that there is a newer version of Transmission.  I am running with version 2.94 and the newer version is 3.0   I thought this is strange as the newer version is over 2 years old and Ubuntu seems to be sticking with the old version.

For most software, Ubuntu sticks to the version that was the latest when that version of Ubuntu was released (or actually, feature-frozen). So Ubuntu 20.04 sticks to Transmission 2.94, but Ubuntu 21.10 and 22.04 use Transmission 3.0. Critical bugfixes get backported, so there should be no security risk. In fact, it should be more secure, as you don't get new features that might contain new critical bugs.

---

### Post by jgw on 2022-06-04
Thank you for the replies!

I just check up on UTP and it seems to me that this is what I need to fix my problem with too many connections.  Thanks again!  (marking this one solved)

---

### Post by Dennis N on 2022-06-04
If you want a newer version of Transmission, look to Flatpak which would allow you to use the current stable version on Ubuntu 20.04:

```
Name                     Description                                                                  Application ID                       Version     Branch     Remotes
Transmission             Download and share files over BitTorrent                                     com.transmissionbt.Transmission      3.00        stable     flathub

```

---

