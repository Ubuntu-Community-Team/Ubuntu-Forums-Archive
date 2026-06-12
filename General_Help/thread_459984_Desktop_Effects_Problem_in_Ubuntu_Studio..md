---
title: "Desktop Effects Problem in Ubuntu Studio."
date: 2007-05-31
forum: General Help
---

### Post by omgDarkWillow on 2007-05-31
I installed the desktop effects from Syanptic, and when I click "Enable Desktop Effects" the screen turns completely white, and I have to try to find the button to turn desktop effects off, and when I do, the screen turns back to normal..I don't know what's wrong.

---

### Post by omgDarkWillow on 2007-05-31
Here's a video, to show you what's happening.
[[IMG]http://i77.photobucket.com/albums/j67/Natey168/th_output-1.jpg[/IMG]](http://s77.photobucket.com/albums/j67/Natey168/?action=view&current=output-1.flv)

---

### Post by omgDarkWillow on 2007-05-31
Nobody? :(

---

### Post by Azakus on 2007-05-31
What video card do you have and what drivers are you using?
If you have an ATI card, they are notorious for not working with Compiz/Beryl which powers the Desktop Effects.

---

### Post by omgDarkWillow on 2007-05-31
How would I find that? I know it's Intel Chipset, but nothing specific.

Also, the desktop effects worked when I had regular Ubuntu..

---

### Post by corester on 2007-06-05
ive got the same problem post if u guys find anything helpful thx :)

---

### Post by dysonsphere23 on 2007-06-13
Similar problem:

I had Beryl running great with Ubuntu and Kubuntu.  Then switched to Ubuntu Studio.  I had to install special nvidia packages for the short latency kernel for my Nvidia GeForce 6800 to work.  I am on a Dell Inspiron 9300 laptop.  Now an Nvidia screen appears before the login.  Anyway all seems well except that 

when I enable desktop effects the windows freeze.  Meaning they can not be resized, closed or moved with the curser. I can minimize by using the panel though.

Any thoughts on a course of action?

---

### Post by Patrick K on 2007-06-13
Why would you want desktop effect on U-Studio? You should preserve all the processing power your system has for multimedia production. That's what U-Studio is designed for, not eye candy. Why do you think it's not included with the install.

---

### Post by dysonsphere23 on 2007-06-13
> **Patrick K said:**
> Why would you want desktop effect on U-Studio? You should preserve all the processing power your system has for multimedia production. That's what U-Studio is designed for, not eye candy. Why do you think it's not included with the install.

Why ask why?  I am exploring this stuff.  Do I need to justify my motives in this forum, or can I just ask a question?  I saw some cool screen shots  on ardour.org and thought I would give it a try is all.

---

### Post by ikonia on 2007-06-13
it's good to ask why - that way if you've missunderstood what you're actually want or we can recommend alternatives that are better for you.

the ubuntu studio distro is not aimed at fancy desktop effects.

I find it alarming that you've had to install "special drivers" yet don't know what video card your using 

If possible try to use the products for what they are meant for if your at a basic level rather than having people go all around the houses to support your "testing" needs.

eg: for desktop effects use ubuntu - not ubuntu-studio.

---

### Post by dysonsphere23 on 2007-06-13
> **ikonia said:**
> it's good to ask why - that way if you've missunderstood what you're actually want or we can recommend alternatives that are better for you.

the ubuntu studio distro is not aimed at fancy desktop effects.

I find it alarming that you've had to install "special drivers" yet don't know what video card your using 

If possible try to use the products for what they are meant for if your at a basic level rather than having people go all around the houses to support your "testing" needs.

eg: for desktop effects use ubuntu - not ubuntu-studio.

Ikonia,

My point about asking why was that it sounded kind of condescending.  A simple "Studio is not optimized for effects" would have sufficed to answer my question.

And BTW I did post the video card I am using (Nvidia GeForce 6800).  You must have me confused with the other poster from this thread.  So no need to be alarmed about my "special drivers".

Peace

---

### Post by ikonia on 2007-06-13
I gave you that answer - ubuntu studio is not geared that way.

I got yourself and the origional posters hardware confused.

FYI: your attitude sounds condencending - so perhaps you may wish to review your own advice.

---

### Post by dysonsphere23 on 2007-06-14
> **ikonia said:**
> I gave you that answer - ubuntu studio is not geared that way.

I got yourself and the origional posters hardware confused.

FYI: your attitude sounds condencending - so perhaps you may wish to review your own advice.

Ok, so relevant to this thread:

You don't have an answer for why desktop effects are not functioning in U-Studio or how to get them to work.

Thanks

---

### Post by dysonsphere23 on 2007-09-11
In case anyone else is having this problem with Ubuntu Studio and Beryl/Compiz, I have found a solution, and it works just fine while running multi-media applications.  And effects can be shut off if there are problems with cpu usage during sytem heavy tasks.

I have abandoned Beryl for Compiz-Fusion.

First off get Envy ([http://www.albertomilone.com](http://www.albertomilone.com)) to set up with the latest drivers for the graphics card.

Compile and install Compiz-Fusion using this[[COLOR="DarkOrange"] tutotial[/COLOR]]("http://forum.compiz-fusion.org/showthread.php?t=1985#post16628").

As I said before if you find multi-media programs runnning sluggishly with effects on the can be turned off during these tasks from the Fision-Icon in the system tray.

I hope this works for you as it has for me.

---

