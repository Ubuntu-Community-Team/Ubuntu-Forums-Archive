---
title: "Windows open Slow/ Firefox Scroll Slow"
date: 2007-11-16
forum: General Help
---

### Post by ricanelite on 2007-11-16
Alright! I have been running Linux for about 2 weeks now. I have Ubuntu Linux Gusty installed on a Gateway Notebook which has a ATI Xpress 1150, Turion 64x2 running at 1.60ghz and 1gig of RAM. Now everything works perfect I have Compiz-Fuzion running with all the 3D Effects going and everything is smooth. Now I decided to also put Ubuntu Linux Gusty on my new Gateway Desktop PC which is GT5464 which has a Pentium Dual Core E2140 running at 1.6ghz and 1gig of ram. Now where this Desktop Lacks big time is a onboard Intel Graphics Media Accelerator 950 which has NO memory at all. So here is my question I have Compiz and the 3D effects running on this machine as well. It runs but here is where I'm confuse and hopefully someone has seen this or hopefully will have a answer for me. When Ubuntu is running as for Opening Apps, it opens and closes nicely but when I'm either on Firefox or any App where I'm scrolling down like view a site where I'm reading a Article and when I scroll down on my Mouse Wheel it moves very slow. When I mean by that it movvery jaggy. Not like when you scroll and everthing is smooth. Now I went into Firefox Options and I turned on Smooth Scrolling and still it moves very jaggy. Also it goes for when I open up apps. Like when the window opens it appears very slow. Or if I hit the action for the cube it takes a quick second to show the cube but when I see the hole cube it runs smooth. Now do you think the reason why I'm experiencing this is because the graphics card is not powerful enough being that it has no graphics memory at all. It depends on the System Memory? Because either way I'm going to upgrade my graphics card on my Desktop. Just wanted to make sure that is the case. 

What type of graphics card should I get? Because I do not want to spend a lot of money on a Graphics card because I'm not a big PC Gamer at all. I also do not do very much video editing. But I will like to run Compiz-Fuzion and all of this effects at a nice rate. Which is a shame because my Notebook has a ATI Radeon Xpress which has 128mb and it runs perfect. The only PC game I will play will be World of Warcraft. So will I be able to find a good graphics card that will give me enough performance where I could have a good experience of Ubuntu Linux Gusty. Because these past 2 weeks has been awesome and honestly I have not missed Windows at all. If I could get Desktop running smooth, Then I will make a full move and just keep Ubuntu Linux dedicated onto my Desktop and have Windows run on Linux. Or use Wine for certain Apps.

---

### Post by mikeyfbi on 2008-01-02
I don't know if this will help or not, but I stumbled across this thread trying to speed up my unusually slow firefox.

Mine was taking abnormal amounts of time to load new tabs, switch tabs, and scroll.  But my FF in virtualbox under XP was quick as it should be.

I found this and applied it, and it seemed to fix it :)

> I think what you are referring to is 'about:config'. Type that into your Firefox browser to get lots of config options. The one that is most popular to change is the IPV6 value.

network.dns.disableIPv6

changing this value to 'true' can help speed things up on some systems.

Mike

---

### Post by knowmonger on 2008-01-10
Nope. I had it as "false". But I made it true but no effect whatsoever. ****, I regret changing over to Ubuntu. If I can't do basic stuff fast, why should I use it ? Not to mention the bootup which takes upto 4-5 mins. My XP loads in 24 secs.

No wonder they're giving this for free. Is there any other method ? Or else, I'm done. Good riddance.

P.S: Slightly hot tempered at the moment.  :mad:

---

### Post by GlennW on 2008-01-11
I'm not sure, knowmonger, if my situation isn't similar to yours. I have a P4 1.6 Ghz, 1 Gb RAM with an nVidia GeForce 6200 256Mb vid card and I experience the same symptoms. Pages in FF take forever to load, scrolling is interminable and often the screen "greys" out. I thought that when I upgraded my RAM to 1 Gb that it would improve but there was no change. I have globally disabled IPv6 and that, too, changed nothing.

So, does anyone have any suggestions on how to fix this issue?

---

### Post by bartcramer on 2008-03-28
Hi!

FF3.0, on Hardy beta, is veeery slow for me too. Most annoying is within Gmail and I believe websites using the same technology (Ajax?). It is just not responsive at all: typing, scrolling, mouse-overs etc... 

Anyone an idea?

---

### Post by strabes on 2008-03-28
Disable compiz on the computer with the intel card.

---

### Post by jjbarrows on 2008-05-25
I have the same problem;
on some pages (gmail) scrolling is very slow
on some pages (this forum) scrolling is fine

on both the above ctrl-mouse wheel text resizing is painful - can take a minute to take effect (and by that time is very small or very big) it is realtime on my windows machine

i have nvidia propietary module installed, and have tried disabling desktop effects to no avail.

-joseph

---

### Post by eklypze on 2008-06-06
Yeah, I must say that I am experiencing the same problem.

My computer specs I would not say are weak and everything basic such as scrolling works 100% smooth and fast on Vista, but extremely laggy on Kubuntu 8.04.

I am using FF3.0 RC2 on a Dual Core 1.8GHz processor, 2GB RAM, 8800GT 512 MB video card, and the x64 Kubuntu OS.

---

### Post by rickatnight11 on 2008-07-19
Disabling Desktop Effects did it for my desktop (Athlon XP 2400+ and ATI Radeon 9700.)  When Desktop Effects were enabled, scrolling in Firefox was very laggy.  Now it's smooth as butter.  I still wish I could have at least basic Desktop Effects on though.  I'm not sure why that stresses the card so much.

---

