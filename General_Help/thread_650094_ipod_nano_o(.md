---
title: "ipod nano :o("
date: 2007-12-25
forum: General Help
---

### Post by jamesbeat on 2007-12-25
I bought my girlfriend an ipod nano video (8Gb black) for christmas, but I can't get it working!

I have tried using gtkpod, and it works to an extent. The ipod mounts fine and an icon appears on my desktop, and gtkpod recognises it. I can write music to it and read music from it, but when I eject the ipod, it tells me that there is no music installed (although it does acknowledge that some storage space is used up)
The music is definitely on there because I can access it using other audio prgrams such as banshee.

I understand that this is to do with a database file on the ipod not being written correctly.

I followed these instructions to get the firewire ID set up:

[http://bbs.archlinux.org/viewtopic.php?id=41426](http://bbs.archlinux.org/viewtopic.php?id=41426)

but still no joy!

Can anyone shed any light on this?

---

### Post by bigmahlman on 2007-12-26
I am having the same problem.  I have been using itunesand i just cant seem to get it to work,  i have followed multiple tutorials,  and nothing seems to work,  my firmware is 1.03,   I am tring to get rid of windows,  this and tablet function is the only things I need to say goodbye to windows.   

Please try to point us to a solution,  This is essential in my move to ubuntu!

---

### Post by HermanAB on 2007-12-26
Hmm, Apple Ipods are the worst.  I'm sure you don't want to hear that, but honestly, my heart bleeds for the souls who fall for the Apple cool-aid.  Here is something I wrote a while ago, but it is for older Nanos: 
[http://aeronetworks.ca/ipod-howto.html](http://aeronetworks.ca/ipod-howto.html)

I suggest that you Google for help.  There is a special project somewhere to try and make the latest Nano devices work - I searched but could not find it.  The best use I have for a Nano is to use it for target practice.

You can get a 1GB Philips for all of $40 and it behaves like a USB memory stick:
[http://wal-mart.ca/wps-portal/storelocator/Canada-FeaturedPage.jsp?selection=listingDetails&tabId=1&singledept=null&lang=&assetId=27925&imageId=38971&suggestedItem=&priceType=1&page=null&departmentId=64&categoryId=354](http://wal-mart.ca/wps-portal/storelocator/Canada-FeaturedPage.jsp?selection=listingDetails&tabId=1&singledept=null&lang=&assetId=27925&imageId=38971&suggestedItem=&priceType=1&page=null&departmentId=64&categoryId=354)

Cheers,

Herman

---

### Post by jamesbeat on 2007-12-26
Well, my problem is that I already rid myself of windows. I haven't used it for around two years now, and I certainly don't want to mess around with it now just to get one device working.
I have trawled the internet for hours trying to find a solution to this problem but to no avail. The only help I have found refers me to gtkpod, but as I said above, this doesn't seem to work for me.

Maybe Apple have recently changed the firmware?

Herman, I understand what you are saying, but I'm afraid I don't agree. I have had two ipods since I have been using Ubuntu and they have both worked seamlessly straight out of the box. The ipod costs a little more, but the hardware is so *nice * that, at least to me, the price is justified.
The nano is the nicest ipod I have handled, it just oozes quality.
If only I could get the damn thing  to work!

The frustrating thing is that all the references I have found by googling have either said that the nano works perfectly, or if there's a problem, it always seems to be that the nano wouldn't even mount.
When I plug the thing in, Ubuntu recognises it perfectly and pops an icon on my desktop. I can browse through it, and if I use gtkpod, banshee etc I can transfer music and play it back.
The only problem seems to be getting the ipod to realise that it has music on it.

I have read that the first time the ipod connects to itunes, it gets initialised in some way. Could this be the problem? I have looked in the ipod's directory and found a file called 'firsttime' which presumably would be altered when the device is first used.
Do I have to connect it to a windows box once to initialise it?

---

### Post by siwilson on 2007-12-26
Follow this: [http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

It worked for me on a new iPod nano 8Gb.

HTH

/Simon

---

### Post by GackY2K on 2007-12-26
siwilson,

I just tried that on my sons new 4GB Nano...and it still wont show any music installed, but that the space is used...indicates 3.1 GB free.   Grrr...I'm not wanting to dual boot any more than is absolutely necessary...guess I'm going to have too though.  I hate apple...too bad I freaking love their ipods.

---

### Post by siwilson on 2007-12-26
If you have Windows or OS X available try using pukka iTunes once - put a couple of songs on using that.

I did that sometime during the testing and it could be that initialised something?

/Simon

---

### Post by jrattner on 2007-12-26
IT worked for me too...WAHOOO!

---

### Post by dark_harmonics on 2007-12-26
This worked flawlessly for me as well. YES!! I love Ubuntu :). Now i just wish i had a way to write my MP4 video files down. If you are trying to get this same thing working, the newest version of gtkpod (i compiled it from source) doesn't seem to work for me. It says i need to compile it togeter with some libmp4 thing.

---

### Post by jamesbeat on 2007-12-27
> **siwilson said:**
> Follow this: [http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

It worked for me on a new iPod nano 8Gb.

HTH

/Simon

THANKYOU!
It worked perfectly!
Couple of things, when I tried to install the first package, I got an error and it wouldn't let me install.
I installed the second one, which went ok, then I installed the first one, which again installed ok.
For good measure, I reinstalled the second one so that they had been installed in the correct order.
I also got an error when I tried the terminal commands further down the page, but when I plugged the ipod back in, it worked just fine.

Thanks, again

---

### Post by sandwormblues on 2007-12-28
Message to Canonical:

I'm supported many Ubuntu users, and i daresay I've lost a few to the sad twitching MS operating system that shan't be named.  From a business perspective, Ipods should be a TOP priority among proprietary devices that need 100% compatibility.  I hate the darn things, from that obnoxious click to the awkward UI to the yuppie-minimalist aesthetic.  But everybody's got 'em.  An OS that doesn't integrate with Ipod is like a burger joint that doesn't sell cola.  Good luck.

---

### Post by officeboy on 2007-12-28
Hmm, any ideas why those instructions wouldn't work for me?  Newly installed 7.10 system. Both debs installed fine (after doing them in reverse). No errors.  But Rythembox just pop's open and then closes right away.

---

### Post by bigmahlman on 2007-12-28
Does this fix work with amarok?

---

### Post by Waikei666 on 2007-12-28
I seem to have the same problem with officeboy - Rhythmbox pops up and closes immediately - this only happens when ipod nano is connected.

unfortunatley this period i am back to XP whilst put the videos and music in.... (and spending the free iTune voucher I got given :D)

thanks in advance.

---

### Post by siwilson on 2007-12-28
All of the iPod applications seem to work fine for me (Rhythmbox, gtkpod, Amarok).

If your application opens then immediately closes, try starting it from a terminal and see if anything output there gives you a clue.

(Applications > Accessories > Terminal, then enter eg rhythmbox)

/Simon

---

### Post by bigmahlman on 2007-12-29
everything is working great for me.    
Now i just have to get my tablet pen working

---

### Post by amorangi on 2007-12-30
It appears to work for me - rythymbox can see all the songs, I can transfer songs to the ipod, however once I eject and try to use the ipod it says there's no music, even though there is. Any ideas why the ipod can't see the music stored on itself? It seems GackY2K has the same problem.

---

### Post by dark_harmonics on 2008-01-02
> **officeboy said:**
> Hmm, any ideas why those instructions wouldn't work for me?  Newly installed 7.10 system. Both debs installed fine (after doing them in reverse). No errors.  But Rythembox just pop's open and then closes right away.

Did you make sure to point that command at your ipods mount point? I named mine Thomas so it mounts to /media/Thomas instead of /media/IPOD

---

### Post by dark_harmonics on 2008-01-02
> **sandwormblues said:**
> Message to Canonical:

I'm supported many Ubuntu users, and i daresay I've lost a few to the sad twitching MS operating system that shan't be named.  From a business perspective, Ipods should be a TOP priority among proprietary devices that need 100% compatibility.  I hate the darn things, from that obnoxious click to the awkward UI to the yuppie-minimalist aesthetic.  But everybody's got 'em.  An OS that doesn't integrate with Ipod is like a burger joint that doesn't sell cola.  Good luck.

So did this process not work for you? I followed it and am delighted to have read/write access to my new ipod. Oh by the way, the cause of this problem is apple. They are trying to shut out third-party apps. This means any linux/windows/mac program that is not  iTunes. Thankfully this work around lets me utilize Rhythmbox. 

A quick google search would prompt ya with further info on their "lock out" strategy. They must be learning from Microsoft.

---

### Post by []Milo on 2008-01-04
I think the point is that 3G Nano's are not supported out of the box especially if there is a fix available. Much as I love it, Ubuntu will only ever be an OS for the technologically curious and never a consumer product until this sort of thing is sorted out (and tbh I am so sick of saying this) it has to work easily.

---

### Post by CheeseEatingBulldog on 2008-01-05
I get an error when typing in the command:

root@ifrit:~# /usr/bin/ipod-read-sysinfo-extended /dev/sdc2/ /media/disk
Couldn't read xml sysinfo from /dev/sdc2/

---

### Post by evil316 on 2008-01-07
> **siwilson said:**
> Follow this: [http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

It worked for me on a new iPod nano 8Gb.

HTH

/Simon

This worked for my daughters new Ipod, many thanks!

---

