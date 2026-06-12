---
title: "amarok won't play mp3's on ubuntu 6.06"
date: 2006-09-08
forum: General Help
---

### Post by senorgato333 on 2006-09-08
yea i just got amarok and it just skips through my mp3's what do i have to do to get it to work?

---

### Post by wieman01 on 2006-09-08
You need to install a package called "xine" via Synaptic. Then go to "Settings->Configure Amarok->Engine" and choose "xine Engine" as your "Sound System". That's it I think.

---

### Post by senorgato333 on 2006-09-08
sry i'm a noob how do i do that in terminal?

---

### Post by Sweet Spot on 2006-09-08
Ubuntu doesn't support mp3's straight out the box because of lisencing issues and such, so you have to get all the packages from the repositories, OR you can just use Automatix to install all non free codecs. I used Automatix, as it's really NO muss, NO fuss, straight up works. 

For the i386 kernel, I found that the easiest way to install Automatix, was the "old fashioned way" :

```
wget [http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix_6.4-6-6.06dapper1_i386.deb](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix_6.4-6-6.06dapper1_i386.deb)
sudo dpkg -i automatix_6.4-6-6.06dapper1_i386.deb
```

---

### Post by wieman01 on 2006-09-08
> **senorgato333 said:**
> sry i'm a noob how do i do that in terminal?

You do that in Amarok... the GUI. You know how to use Synaptic?

---

### Post by Sweet Spot on 2006-09-08
Question:  Is another one of your media players playing your MP3's, and just not Amarok ? If so, I guess disregard my last post. I was under the impression that you didn't have LAME or other things installed.

---

### Post by senorgato333 on 2006-09-08
thank you very much!

---

### Post by wieman01 on 2006-09-08
> **Sweet Spot said:**
> Question:  Is another one of your media players playing your MP3's, and just not Amarok ? If so, I guess disregard my last post. I was under the impression that you didn't have LAME or other things installed.

Good point you have though. I think "xine" is sufficient if you want to play MP3 using Amarok as far as I remember. But your post is correct. 

These are all so-called "restricted formats" if you want to use Ubuntu as a Media Center:

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

This link is useful if you want to achieve the mentioned in just 3 steps (very useful):

[http://www.ehomeupgrade.com/entry/2663/how-to_get_full]("http://www.ehomeupgrade.com/entry/2663/how-to_get_full")

---

### Post by senorgato333 on 2006-09-08
ok thank you i will try both the ways if  they dont work back to the forums for me haha thank you!

---

### Post by SableSlayer on 2006-12-01
,

---

