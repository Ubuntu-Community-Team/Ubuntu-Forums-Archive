---
title: "First Ubuntu Install"
date: 2007-08-31
forum: General Help
---

### Post by Imperdimper on 2007-08-31
I'm thinking this is going to be more of a rant than anything else, but it will allow me to get my thoughts together and possibly get moving on fixing some stuff.

How can a current, modern day operating system fail so horribly right out of the box?  I do want to use Linux, mainly to get away from Windows, but Ubuntu isn't making this easy on me.  First it started out with a wireless problem, something about KNetworkManager was acting up because of WPA.  Then amaroK would crash when starting.  Even after I got that fixed, I found out that there is no sound.  Then I had a hard time installing Firefox, then I found out I couldn't boot back into Windows.  Then I installed Xfce because KDE was running a little slow, only to find out that the network isn't automatically started when I start the environment.  And to make matters worse, half the time the network manager picks the wrong router.  And when I do select the right router I find out that it has forgotten my WPA key.

I'm sure there's some other problems I've forgotten to mention, but they are of less importance.  Though the 'not booting back into Windows' problem is really irking me,  That just leaves me with one half-working OS to work out of, Linux.

Getting that rant out pleases me, even if it doesn't please anyone else.  Now I guess I have to sit down and spend a few hours banging my head on the keyboard, hoping that the random keys I hit will magically enter in the proper terminal commands to get things fixed.

Imper

---

### Post by atlfalcons866 on 2007-08-31
the wifi issue might be releated to the driver. What wifi card do you have?
Also the ubuntu version with KDE is Kubuntu. Ubuntu has gnome.

---

### Post by Imperdimper on 2007-08-31
Don't think the Wifi has any driver issues, it works fine when I want it to.  I know I just have to put in some settings so it will automatically load the network manager and automatically input the WPA key for my main router.

And yeah, I installed Kubuntu then installed the Xfce environment.  But I figured that Kubuntu was the exact same as Ubuntu, just a different environment, so I could get help here.  Should I be heading to a different forum when I get off my *** and start asking questions?

---

### Post by robotii on 2007-09-01
Hi Imper,

Firstly I just want to say two things about your post.

1. Thanks for approaching the problems in the right manner, with the right attitude. With some of the posts on here that is a refreshing attitude.

2. You will find that (hopefully) having already done the above, that people on the ubuntu forums are usually pretty helpful.

With regards to your windows problem could you post the contents of /boot/grub/menu.conf, how many drives you have installed, and what partition the windows install is on. I will try to help you fix it - I ran into a similar problem when first installing. Thankfully I was still able to read the forums :-)

robotii

---

