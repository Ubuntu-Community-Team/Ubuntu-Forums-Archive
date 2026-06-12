---
title: "When was the last time I did a software update?"
date: 2016-01-08
forum: General Help
---

### Post by carmen2012 on 2016-01-08
I found an Ubuntu CD that I created with Remastersys.

Is there any way (eg file and/or command) that will allow me to to see when was the last software update performed on this CD?

Thank you

---

### Post by Bucky Ball on 2016-01-08
Which release is it? If it is an unsuppported one (too old) it doesn't matter anyway. :)

---

### Post by carmen2012 on 2016-01-08
It is Ubuntu 14.04 LTS.

I'm just wondering if there is a way to figure out the last time it was updated before it was converted to a CD?

---

### Post by Bucky Ball on 2016-01-08
I might suggest booting from it, 'Try Ubuntu', open a terminal at the desktop and 'uname -a'. Which kernel is it using? We are currently at 3.13.0-74 for 14.04 LTS.

As for a specific date and time of the last update/upgrade, hopefully someone can be more specific than I can. Good luck.

(PS: A mentor of mine told me many years ago, if it's not labelled, its not worth having. :))

---

### Post by deadflowr on 2016-01-08
I'd run 
```
df
```
to help figure out where the cd's location in the file system is (most likely /media/something/something)
Then
```
ls -la /media/something/something
```
the date should be the last modified date, Me thinks.

Beyond that Ubuntu's update history is logged into  /var/log/apt/history.log
So if you can run
```
tail /var/log/apt/history.log
```
the last date would be the last date in which you ran an update for that.
If that makes sense.

---

### Post by carmen2012 on 2016-01-09
> **Bucky Ball said:**
>  (PS: A mentor of mine told me many years ago, if it's not labelled, its not worth having. 

That's really well said, thank you

---

### Post by Bucky Ball on 2016-01-09
As you probably know, 14.04 LTS is a long-term support release until 2019, plenty of support left, so see how you go with deadflowr's advice. 

Just curious as to why you are wanting this info. If it is so long ago you can't remember, it may be a better option to download a fresh ISO and create new install media. That way you'll have the latest and few updates to do after install. If you install from the old disk you are going to need to update/upgrade quite a bit. Either/or really. Good luck.

---

