---
title: "Software that can detect type of CD / DVD"
date: 2013-01-20
forum: General Help
---

### Post by tech291083 on 2013-01-20
Hi,

I wonder if there is any software that can detect the exact type of optical discs ie whether it is a CD or DVD. Then what type it is ie CD-R, CD-RW, DVD-R, DVD+R, DVD-R, DVD-RW. I know this sounds a bit stupid and the media has written on it as to what type it is, but I would love to use this software as there are times when I get DVDs with no label on it. Thanks a lot.

---

### Post by kostkon on 2013-01-20
Of course you can, only for DVDs though.
```
dvd+rw-mediainfo /dev/dvd
```
You can even compare its media id against [this list here]("http://www.digitalfaq.com/reviews/dvd-media.htm") and see if you have actually bought good quality discs.

Hope that helps.

---

### Post by tech291083 on 2013-01-23
> **kostkon said:**
> 
```
dvd+rw-mediainfo /dev/dvd
```



Thanks for the command you gave, it works for all types of dvds that I happen to have ie dvd-r, dvd+r, dvd-rw and dvd+rw. But its a shame that it is only for dvds. I just found out that Nero Info Tool as part of Nero Burning software package gives a great deal of info about various types of optical discs once inserted into the dvd/cd drive, but it works in Windows only.

Please see the link below. It shows a series of tabs namely Drive, Disc, Configuration etc. If you click on the Disc tab, it will show you all the info about a disc that you might have put in your drive. Thanks. I am sure there must be some other way to find out what I want.

[http://www.hotdl.com/dl/uploads/20111116214353.png](http://www.hotdl.com/dl/uploads/20111116214353.png)

---

### Post by black veils on 2013-01-23
the burner k3b seems to, though i didnt test for cd. in the top-left area it says about media, you can right-click for more info.

---

### Post by sudodus on 2013-01-23
> **black veils said:**
> the burner k3b seems to, though i didnt test for cd. in the top-left area it says about media, you can right-click for more info.
I can confirm that k3b also identifies audio CDs and data CDs.

So if you are happy with a GUI application, use k3b :-)

---

