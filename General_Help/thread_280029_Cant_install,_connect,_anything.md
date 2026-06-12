---
title: "Cant install, connect, anything"
date: 2006-10-18
forum: General Help
---

### Post by Mtm199 on 2006-10-18
So I have some problems.

My computer that I have ubuntu on is completely disconnected from the home network.  I have a wireless card for a linksys router, and my ultimate goal is to get that to work with it.  

Since I have no internet, I dont know how to install programs. What I've been doing is downloading the .tar, and then putting it on a removable disk, and loading it to the ubuntu computer.  I'd copy the file over, and extract it.  I'd do ./configure and attempt make commands. I've tried messing with different versions of Wine and NdisWrapper, but I get errors saying I need a C compiler.

Is there any way to get a C compiler over to that computer without using the internet to download it, or needing something i dont have to install it?

OR, any other ways I can get programs installed?  I'm assuming once I get a driver or something working on my computer for the wireless card, everything will snap together.  Till then I'm clueless.  Any help is greatly appreciated.

---

### Post by taurus on 2006-10-18
C should be on your desktop CD (LiveCD) that you used to install Ubuntu from.  So, insert it in the drive, open a terminal (Applications -> Accessories -> Terminal), and do

```

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

```
Now, build whatever you want...

---

