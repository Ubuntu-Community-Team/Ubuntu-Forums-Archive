---
title: "Nautilus, other programs are crawling"
date: 2015-10-21
forum: General Help
---

### Post by Evil Wayz on 2015-10-21
My system is an old cad/cam machine I bought off a school system.  It's got a dual core Pentium 3.4 in it, and 8 gb of ram.  It came with a sata 40gb hd, and I added a 2tb sata hard drive to it.

Now, my OS is on the 40 gb hd.  ANd things load up SLOOOOOOOOOOOOW.  SOmetimes when I open a folder or start an application, i can count to thirty before it shows up.  I thought that maybe the 40gb was an old SATA drive and so it was just slower, since file management on the 2tb hd was just fine.

Recently i acquired a brand new portable hd.  ANd transferring files was lightning fast until last week.  SUddenly, instead of moving things at 22.mb/s its moving things in kb.  Transfers that used to take minutes are now taking hours.

Now, all three hds in question are almost full.  Is there anything I can do to tune this system up?  I have a laptop that runs ubuntu on a stick and its hellaciously fast.   I was told that because of the nature of the ext filesystem that Linux drives don't need to be defragmented.   But i know that defragmenting offten speeds up WIndoze systems. 
THanks.

---

### Post by yancek on 2015-10-21
> Now, all three hds in question are almost full.

That will slow things down, eventually to a full stop.  On defragmenting, see the link below or just google defragment on linux for a number of links with explanations.  You can run a filesystem check on the drives to see if there are problems.

---

### Post by Evil Wayz on 2015-10-21
I didn't see a link?

---

### Post by Evil Wayz on 2015-10-21
So I found a program called 'defragfs" but it won't compile using the instructions on the webpage.  Anyone?

---

### Post by Evil Wayz on 2015-10-21
So I found a program called 'defragfs" but it won't compile using the instructions on the webpage.  Anyone?

---

### Post by SuperFreak on 2015-10-21
[http://linuxmusicians.com/viewtopic.php?f=19&t=11479]("http://linuxmusicians.com/viewtopic.php?f=19&t=11479")

end of first post there is a description on how to use defrags

---

### Post by Geoffrey_Arndt on 2015-10-21
Fragmentation on Linux is usually not an issue . . . . [http://www.howtogeek.com/115229/htg-explains-why-linux-doesnt-need-defragmenting/](http://www.howtogeek.com/115229/htg-explains-why-linux-doesnt-need-defragmenting/)

Maybe good place to start is running the pre-installed "disks" program, and then checking space allocation via "disk usage analyzer".

---

### Post by Evil Wayz on 2015-10-22
I get a big pretty graphic.  What am I supposed to be looking for?

---

