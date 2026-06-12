---
title: "Ubuntu 14.04 Logo freeze"
date: 2015-05-01
forum: General Help
---

### Post by Anh-Khoi on 2015-05-01
Firstly, I would like to preface this by saying I am a beginner and fairly new to this sort of thing. I had been using Ubuntu 14.04 alongside Windows 8.1 for a while now and everything was fine. I became irritated with windows so I wanted to shift most of the hard drive space towards my linux partition. Not knowing how to do so, and not comfortable doing so with Gparted (again, I am quite a noob), I thought "Hey I'll just erase all my linux partition and re-install it". After reformatting windows 8.1 (keeping it to play video games), I followed instructions from the following link on how to delete the linux partition, where at the very end, instead of allocating the free space to windows, I kept it free to put Ubuntu (see attachment). 
[https://www.youtube.com/watch?v=heO1n73Ua4Q](https://www.youtube.com/watch?v=heO1n73Ua4Q)

It's been over a year since I first installed Ubuntu, so I followed the steps outlined in the following link:
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

Everything worked fine until I booted from my USB. Windows 8.1 gave me 3 USB boot options with a 4Gb Kingston that had the ISO on it: [COLOR=#373E4D][FONT=helvetica]- UEFI: IP6 Realtek PCIe GBE Family Controller- Ubuntu- UEFI: KingstonDataTraveler 102PMAP[/FONT][/COLOR]

The first one would give me a black screen with a text in the middle. I do not recall what it was, but I think it had something to do with Grub. I only tried that option once. The second one ended up with a black screen and text about "minimal bash-like line editing is supported..." and something about grub 2. The last one gave me a black ubuntu boot screen with the following choices:1. Try Ubuntu 2. Install Ubuntu 3. OEM install 4. Check disk for defects. Options 1 and 2 brought me to the Ubuntu logo screen and would freeze (the loading dots stopped moving), and I didn't try options 3 and 4. I however verified the ISO integraty with Md5 CHecker and found that it was intact using the 14.04.2-desktop-amd64 version. 

I also tried with a 8Gb flash drive and the Ubuntu 15.02 ISO, but nothing different came about. I also tried burning the ISO using unetbootin instead of universal-usb-installer and nothing different. I would also like to add that everything from Windows right now works fine.

Your help would be much appreciated,
Thanks!

---

### Post by tuxHulk on 2015-05-02
> **Anh-Khoi said:**
> 
It's been over a year since I first installed Ubuntu, so I followed the steps outlined in the following link:
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)


I followed a similar guide when I switched from Win7 to Ubuntu. Everything worked, and I even ran into the same issue you did where the little dot/squares would freeze on that screen (5+ mins). My problem initially was I did something wrong. I recreated the USB and it still got stuck again... this time it was my USB stick though, the read was very slow on it for some reason. I let it sit and eventually it the Ubuntu Live installer popped up and it got stuck again after the partitioning bits (same thing 5+ mins) then voila it worked. 

Not the best answer, I'm sure but that was my problem with an older thumb drive.

---

