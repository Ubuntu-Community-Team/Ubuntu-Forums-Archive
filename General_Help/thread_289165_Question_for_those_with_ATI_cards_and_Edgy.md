---
title: "Question for those with ATI cards and Edgy"
date: 2006-10-30
forum: General Help
---

### Post by Cable on 2006-10-30
I'm still using Dapper, but am thinking about doing a fresh install of Edgy.  I have an ATI card, and have seen some people talking about having problems.  I do play games, so I need 3D acceleration to work.  I see [here]("http://https://help.ubuntu.com/community/BinaryDriverHowto/ATI") that there are detailed instructions for installing the ATI driver and getting it working properly.  Does this indeed work and get 3D acceleration functioning properly?  How are your Edgy/ATI boxes working?

Also, as a bit of a side question:  now that AMD and ATI have merged, can we expect better driver support for ATI cards since (I believe) AMD wants to better support the Linux community?  For example:  properly supporting AIGLX so that X.org 7.1 doesn't cause problems with ATI cards.   Please post links to any news or articles dealing with this subject, as I think it holds a lot of interest for those who use ATI.

---

### Post by ltmon on 2006-10-30
On upgrade to Edgy I had to modify xorg.conf to get my card working fully by adding the following lines:
```

Section "Extensions"
  Option "Composite" "Disable"
EndSection

```

Since then it has been fine.  The only other problem I have had is that hardware accelerated vido (i.e. Xv with Avivo) doesn't work on Edgy if you have an x1000 series card (I have a mobility X1600).  So my video quality is not as good, although I only really notice on HD videos or videos that need to be scaled a lot.

As for your other question: your guess is as good as mine.  There have been a few comments reported in the press that AMD is looking to support Linux better and even open-source the driver (or a subset of it).  But it's all smoke until it actually happens.  I find a good source of info for the ATI linux drivers is phoronix.com (look for their "Redblog").

---

### Post by jocko on 2006-10-30
[]("http://www.infoworld.com/article/06/08/02/32OPcurve_1.html")[ ]("http://www.infoworld.com/article/06/08/02/32OPcurve_1.html")[]("http://www.infoworld.com/article/06/08/02/32OPcurve_1.html")Here is something interesting:
[http://www.infoworld.com/article/06/08/02/32OPcurve_1.html](http://www.infoworld.com/article/06/08/02/32OPcurve_1.html)

See the last section:
"AMD is strongly considering open-sourcing at least a functional subset of ATI’s graphics                                  drivers."

We'll just have to wait and see what happens, if it happens.

---

