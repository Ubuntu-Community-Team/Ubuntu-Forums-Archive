---
title: "ubuntu using A LOT of ram"
date: 2014-04-29
forum: General Help
---

### Post by lizpy66 on 2014-04-29
So I'm on ubuntu 14.04 after upgrading to 13.10 and I've noticed I have extremely high ram usage like out of my 4GB, though both have only let me ue 3.3, I'm at 1.6fb, 48% with firefox, banshee and skype open BUT firefox being the largest is only using 338mb it says with 4 tabs open, even if I close everything I usually am still have around 1.3 going. I noticed this on 13.10 too but I've heard many people don't even use a 1 GB with everything close so something is happening here I think, I've noticed xorg is high up there, is this a necessary application or can I kill the program with no reprecussions? Also it should be noted to say that I even put skype on very low priority, same with pulse audio and sometimes firefox yet no change. Swap isn't even doing anything, the most I've ever seen it used is 19.9 mb..out of 5.1 GB.


P.S. out of curiosity, anyone get suspend mode working? Got it working once


Thanks in advance :)

---

### Post by QIII on 2014-04-29
Hello!

Could you give us a bit of info about your hardware, particularly the graphics and whether you are using a proprietary driver?

I'd not kill xorg, unless you fancy a significant (if temporary) emotional event.

Could you run

```
top
```

and copy and paste the entire contents of the terminal back here.  (Please use code tags!)

A screenshot would work too.  (Please use the attachment functionality rather than dropping the image in the response box.)

That will give us a better look at what is going on.

Cheers!

---

### Post by lizpy66 on 2014-04-29
here, hopefully it attached and I took a screenshot, though it kept changing a lot, is this normal?

I don't believe I'm use any propriety driver, last I checked I am not but I forgot how to >< sorry

---

