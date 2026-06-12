---
title: "unable to play MP4 video, etc."
date: 2007-04-27
forum: General Help
---

### Post by andre2p on 2007-04-27
Hello:

I used Edgy for several months before deciding to do a clean install of the new 7.04.  The install went well, and I restored my files into it without any problems.  Unfortunately I cannot get Ubuntu to play any movies now.  I tried MP4, WMV, AVI, etc.  None work.  I can get sound but no video.

I followed the Sticky HOW-TO; I even re-installed the whole system again.  Still no luck.  In the meantime I installed OpenSUSE last night on a second available drive and that played all movies just fine.  

I would prefer to use UBUNTU since I like it more than SUSE,  but after hours of trying to get this to work I am about to give up.  

Please help.  Thanks.
Andrew

---

### Post by adza on 2007-04-27
Andrew,

       What architecture are you running? i386 or AMD64?

---

### Post by andre2p on 2007-04-27
I am using i386 (Dell).  Like I said, I had no problems under Edgy.  Thanks. I believe the video card is ATI.

---

### Post by adza on 2007-04-27
this script may help... it's for 64 bit, but it works by installing all the 32 bit stuff... i've installed a few of kilz's scripts.. they're all very good... 

[http://ubuntuforums.org/showthread.php?t=202537&highlight=kilz+feisty+script](http://ubuntuforums.org/showthread.php?t=202537&highlight=kilz+feisty+script)

maybe browse his posts for a 32 bit version?

---

### Post by strabes on 2007-04-27
Did you install the package ubuntu-restricted-extras ? Suse comes with proprietary codecs and ubuntu doesn't.

---

### Post by andre2p on 2007-04-27
Yes. Did that too.

When I play a movie,  the player rezises like it knows what is playing,  but no visual,  just black.  Sound works.

Thanks.

> **strabes said:**
> Did you install the package ubuntu-restricted-extras ? Suse comes with proprietary codecs and ubuntu doesn't.

---

### Post by marco123 on 2007-04-27
Just a thought but desktop effects aren't enabled are they?

I posted a few days ago and was having the same problem, the video was only appearing when i moved the window.  I turned off desktop effects and video works perfectly now.

---

### Post by andre2p on 2007-04-27
> **marco123 said:**
> Just a thought but desktop effects aren't enabled are they?

I posted a few days ago and was having the same problem, the video was only appearing when i moved the window.  I turned off desktop effects and video works perfectly now.


Not sure what desktop effects are.  Is that enabled by default when you install 7?  Thanks.

---

### Post by xoros on 2007-04-27
Not sure if it will help you may want to try this too: 
[http://ubuntuforums.org/showthread.php?p=2547672#post2547672](http://ubuntuforums.org/showthread.php?p=2547672#post2547672)

---

### Post by andre2p on 2007-04-27
I went to menu System,  Administration, and enabled the restricted ATI driver and that solved the problem.

Not sure what potential problems that may bring, but so far it works fine.

Thanks.

---

