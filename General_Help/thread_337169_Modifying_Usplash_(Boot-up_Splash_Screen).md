---
title: "Modifying Usplash (Boot-up Splash Screen)"
date: 2007-01-12
forum: General Help
---

### Post by Harr!s on 2007-01-12
Hi... 

I've been searching for information about how I would go about modifying the usplash screen when your system boots. What I would like to do is to replace the existing one with a custom one that I have made, or simply modify the existing one. Pretty much what I would like to do is change the Ubuntu logo with this: [[COLOR="Red"]_LINK_[/COLOR]](http://img105.imageshack.us/img105/2559/eyelo1.jpg) 

The version of Ubuntu that I am currently using is 6.10

I found this wiki article: [[COLOR="Red"]_LINK_[/COLOR]](https://help.ubuntu.com/community/USplashCustomizationHowto) somewhat helpful but there are several steps involved in the process that I am having difficult understanding and was hoping someone on the forum could help me out by explaining certain steps in greater detail. 

From what I gather the process is roughly as follows: convert a .png file to the format used by usplash, then replace existing usplash with newly constructed usplash. My problem is how I go about doing this. 

Thanks.

---

### Post by ciscosurfer on 2007-01-12
> **Harr!s said:**
> Hi... 

I've been searching for information about how I would go about modifying the usplash screen when your system boots. What I would like to do is to replace the existing one with a custom one that I have made, or simply modify the existing one. Pretty much what I would like to do is change the Ubuntu logo with this: [[COLOR=Red]_LINK_[/COLOR]]("http://img105.imageshack.us/img105/2559/eyelo1.jpg") 

The version of Ubuntu that I am currently using is 6.10

I found this wiki article: [[COLOR=Red]_LINK_[/COLOR]]("https://help.ubuntu.com/community/USplashCustomizationHowto") somewhat helpful but there are several steps involved in the process that I am having difficult understanding and was hoping someone on the forum could help me out by explaining certain steps in greater detail. 

From what I gather the process is roughly as follows: convert a .png file to the format used by usplash, then replace existing usplash with newly constructed usplash. My problem is how I go about doing this. 

Thanks.Creating the necessary make files to do this for Edgy is a very tricky process if you don't have any C coding skills.  You can download usplash-dev and mess around with the example given, issue a make; make install, et voila, you have the example usplash installed (there are a few other steps involved as well).  If you'd like, I have created a script that does exactly what I just mentioned that I can upload for you to try out.  Just let me know.  :-)

---

### Post by Harr!s on 2007-01-12
> **ciscosurfer said:**
>  If you'd like, I have created a script that does exactly what I just mentioned that I can upload for you to try out.  Just let me know.  :-)

That would be a big help if you could post it for me. Thanks a lot.

---

### Post by ciscosurfer on 2007-01-13
PM or email me for the code ;-)

---

### Post by m1215 on 2007-01-17
i found this how to [http://ubuntuforums.org/showthread.php?t=82835](http://ubuntuforums.org/showthread.php?t=82835)
maybe that can help you.

---

### Post by ciscosurfer on 2007-01-18
> **m1215 said:**
> i found this how to [http://ubuntuforums.org/showthread.php?t=82835](http://ubuntuforums.org/showthread.php?t=82835)
maybe that can help you.The thread you reference works on Dapper but not on Edgy. :D

---

### Post by dklearhos on 2007-01-19
same problem here.This howto does not work on edgy.while executing > sudo dpkg-reconfigure linux-image-$(uname -r) it say that there is no splash image found

---

