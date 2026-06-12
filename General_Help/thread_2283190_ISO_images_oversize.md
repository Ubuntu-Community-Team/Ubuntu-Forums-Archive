---
title: "ISO images oversize"
date: 2015-06-19
forum: General Help
---

### Post by gonzalo-vc on 2015-06-19
Guys, I've downloaded a Lubuntu 14.04.2 ISO that  says to have 703 MB and it gets 731 when it is downloaded, not making into a CD to boot. 
I  have downloaded it in different machines, also. No deal, it always gets bigger than announced  :-(

Is this a problem of sectors in the drives (including pen-drives)?

---

### Post by v3.xx on 2015-06-19
Just downloaded this
[ATTACH=CONFIG]262721[/ATTACH]
And the size after download is 737M, not sure whats up.

[http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/)

I am now downloading Lu14.04.1, which should be 696M.  See how it turns out in a few minutes.

---

### Post by v3.xx on 2015-06-19
Lu 14.04.1 32bit download is 729M :confused:

Next is the Alt install CD, see what happens with it.

BB

---

### Post by v3.xx on 2015-06-19
Lu Alternate install CD 14.04.1/32bit is suppose to be 612M.  Download size is 641M.

I have no idea why this is.

---

### Post by HermanAB on 2015-06-20
Put the image on a USB memory stick and stop wasting plastic...

---

### Post by lisati on 2015-06-20
Possibly because there's Mb and there's Mb. One is 1000 bytes, and the other is 1024 bytes.

---

### Post by sudodus on 2015-06-20
1 Mibibyte (base 2) is 2 [SUP]20[/SUP] bytes = 1024*1024 bytes = 1048576 bytes

1 Megabyte (base 10) is 10 [SUP]6[/SUP] bytes =1000000 bytes

1 Mibibyte = 1.048576 Megabytes

The typical CD disk type '700 MB' (which can store maximum ~703 Mibibytes) is often considered as the standard. See this link,

[https://en.wikipedia.org/?title=CD-ROM#Capacity](https://en.wikipedia.org/?title=CD-ROM#Capacity)

---

### Post by v3.xx on 2015-06-20
> there's Mb and there's Mb
1 Mibibyte = 1.048576 Megabytes
Yep, the math works.  I guess I just never took this close of a look before.  Still, this is confusing.

@gonzalo-vc
You could use the Alt install CD.  Its the same as the regular installer, just lacks the eye candy by using a UI instead of a GUI.  And will fit on a CD.

And thanks to all

---

### Post by vasa1 on 2015-06-20
I recently downloaded the 32-bit and 64-bit versions of Lubuntu 14.04.2 and here's what I see ... And +1 to the USB route.

---

