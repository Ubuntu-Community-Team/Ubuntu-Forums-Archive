---
title: "evince and evince-gtk"
date: 2014-11-02
forum: General Help
---

### Post by vasa1 on 2014-11-02
I was going through [http://ubottu.com/meetingology/logs/xubuntu-devel/2014/xubuntu-devel.2014-10-31-11.01.log.html](http://ubottu.com/meetingology/logs/xubuntu-devel/2014/xubuntu-devel.2014-10-31-11.01.log.html) and came across this:> 
11:43 <bluesabre> so, we're considering swapping evince to evince-gtk... there doesn't seem to be a functional difference, and it reduces gnome dependencies
11:43 <knome> any downsides?
11:43 <ochosi> yeah, i tried -gtk and it looked/behaved the same
11:44 <bluesabre> none discovered so far... I'm thinking it might be a good idea to go ahead and switch now since we're so early in the cycle
11:44 <ochosi> +1
11:44 <knome> then a +1 and "go ahead" from me
11:44 <bluesabre> and we can reevaluate at a later point as needed
11:44 <bluesabre> got it
11:44 <slickymasterWork> +1 from also
11:44 <bluesabre> will do tonight/tomorrow
11:44 <ochosi> yeah, better switching now and having more timeThen I ran *apt-cache show* for both evince and evince-gtk: the former had an "Installed-Size" of 1207 while the latter was 1159. The evince-gtk  version "is built without GNOME keyring support".

So if I don't need "GNOME keyring support" is there any drawback to using evince-gtk? From what I quoted above, the people @ Xubuntu are leaning that way.

---

