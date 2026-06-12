---
title: "install trouble"
date: 2008-04-17
forum: General Help
---

### Post by cmay on 2008-04-17
hi
i just bourgt a new computer but ubuntu would not install in it.
i have installed debian instead.i had to becouse ubuntu could not find the grafiks and other things i suppose
how do i let the ubuntu developers know about incompatibles on this computer type
its a amd based chipset on the mother board. 
 it doesnt tell me a whole lot but thats the motherboard.k9agm4
will hardy be able to install. i got a new computer because i use computer more and more and the old ones getting too old. i was hoping to use ubuntu on this one.

and a anhoter question is why could i not post the first time i tried to post just 6 minutes ago.
i was logged in . somehow i got trown away by a your are not logged in message and am sure i was. 
does that happen sometimes . or was this me not finding my way around right.
thanks for the time.

---

### Post by forrestcupp on 2008-04-17
Well, you probably could get Ubuntu working, especially if you got Debian working.  The first place to start would be to download and install the Alternate CD for Ubuntu.  It's a text based installation.  

Then after it installs, if it won't boot to your desktop because of video card conflicts, you can boot to the recovery mode and when it gets to the command prompt, type
```
dpkg-reconfigure xorg-xserver
```Go through the process of setting up X and when it gets to the video card driver part, choose Vesa.  That will pretty much guarantee that you will get to your desktop, where you will be able to set up the correct drivers for your chipset later.  Hopefully, you won't have to do that, though.

---

### Post by cmay on 2008-04-17
thanks.
i think will wanna wait for the hardy heron when it comes out. but i will sure renember this if the problem comes again.i know its the graficks thats the trouble. but hardy comes out soon i think so i wanna try download the alternate first. i am used to debian installs anyway. i just find it very great to use a livecd for
internet use. so i miss the ubuntu livecd now . i have still the good old dusty computer so i can use that for internet instead. 
but thanks for the reply. i am very gratefull for the assistance.

its just a matter of 14 days before hardy will be released right:)

---

### Post by forrestcupp on 2008-04-17
> **cmay said:**
> 
its just a matter of 14 days before hardy will be released right:)

I think it's only 7 days now.

---

### Post by cmay on 2008-04-17
7  days???.
well what can i say
hoopde doo 
i look forward to that.
thanks

---

