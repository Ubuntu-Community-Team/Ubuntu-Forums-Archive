---
title: "installing wacom configuration app"
date: 2014-09-14
forum: General Help
---

### Post by raghav6 on 2014-09-14
WHERE IS IT? I've been searching about it online for more than eight hour I can see various pics,videos about an app via which you can configure pressure etc. but I just couldn't find it  in lubuntu or how to install it for lubuntu :( my wacom bambo is gets detected just fine all I need is app to configure for example just like the one in this video from 1:27
[http://youtu.be/hcRJDqC9EeA?t=1m27s](http://youtu.be/hcRJDqC9EeA?t=1m27s)
MAN....! some time Ubuntu really plays hard to get :(

---

### Post by raghav6 on 2014-09-26
SERIOUSLY !? WHERE IS EVERYBODY ? IS THIS FORUM WHERE PEOPLE HELP OUT NEW COMERS TO UBUNTU OR JUST SCARE THEM AWAY ? OR MAKE THEM FEEL PATHETIC ? none of my questions answered so for :(   is somebody actually gonna help me or what ? please somebody help me

---

### Post by QIII on 2014-09-26
Yelling at everyone is not likely to gain you much sympathy.

You have asked exactly two questions and waited a week to bump each.

Remember that the forum community is made up of *volunteers* from all around the globe and we live in different time zones. It may simply be that your posts were not seen by anyone who had a good answer for you and then slowly moved down the pages. Rather than yelling at everyone, you might try a *polite* bump a little sooner than a week.

We have relaxed the 24 hour bump rule, so a bump at 12 hours might get your threads seen by an entirely different group of people.

---

### Post by raghav6 on 2014-10-04
OK thank you :) and so sorry for the outburst.it's just so little on the web about some basic ubuntu related info ,even far lesser considering lubuntu. for example here I'm just asking for an app which is already there! and I couldn't find it till today.I thought putting bump again and again might considered as spamming,and I needed to get some attention some how,and I was a little frustrated :( and like you've noticed my other question is fairly basic but still no answer even for that :(  i will just fallow the bump routine then :)

---

### Post by raghav6 on 2014-10-05
Bump!

---

### Post by raghav6 on 2014-10-07
Bump!

---

### Post by raghav6 on 2014-10-09
Bump!

---

### Post by kurja on 2014-10-09
He =) 

I never found a working gui for setting up my wacom bamboo pen and touch; I presume the gui works just for some specific models, didn't look so deeply in that. Instead, I set things up with a script, here are some helpful commands you can use: [http://linuxwacom.sourceforge.net/index_old.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index_old.php/howto/xsetwacom), also look here [https://wiki.archlinux.org/index.php/Wacom_Tablet#Remapping_Buttons](https://wiki.archlinux.org/index.php/Wacom_Tablet#Remapping_Buttons)

Hm now that I think of it, I recall the pressure settings do work from the default gui, I just set up the buttons from cli (I'm not at home now so can't check).

Are you setting it up for use with some specific software? Gimp? You might need to set it up in there as well.

Do post here if you succeed and / or have further questions =)

---

### Post by gordintoronto on 2014-10-09
This might help:
[http://linuxwacom.sourceforge.net/wiki/index.php/External_applications](http://linuxwacom.sourceforge.net/wiki/index.php/External_applications) 

or maybe:
[http://ragnarb.com/configuring-wacom-cintiq-13hd-with-ubuntu-14-04/](http://ragnarb.com/configuring-wacom-cintiq-13hd-with-ubuntu-14-04/)
(this was in one of the comments on the youtube video you pointed to.)

That one says you should look in system settings, where Wacom is an entry.

It's generally useful to provide as much relevant information as you can. For example, which version of Lubuntu are you using, and what model of Wacom tablet?

---

### Post by raghav6 on 2014-10-11
@kurja sure , i will go through those scripts,being a windows user really make me a sucker for GUI :)

@gordintoronto
[COLOR=#333333][FONT=arial]I've already[/FONT][/COLOR][COLOR=#333333][FONT=arial] gone through that post but there isn't any such option in lubuntu as matter of fact there is no 'system setting' in lubuntu instead we have 'preferences' and 'system tools' and none of them contains any option[/FONT][/COLOR][FONT=arial, tahoma, verdana, sans-serif][COLOR=#333333] for tablets and yes I've gone through all the Wikipedia suroceforge etc and that's what frustrates me you stumble across this links rich with info and files but, there is no clear info how exactly make it work [/COLOR][/FONT]
this is what my 'system profiler and benchmark' says 
ubuntu 14.04.1 LTS (is there any script that gives out any more info that you need about os?)
and my wacom tablet model ID is [FONT=arial, tahoma, verdana, sans-serif][COLOR=#333333]CTL-471/K0-C[/COLOR][/FONT]

---

### Post by kurja on 2014-10-11
raghav6, it's a little unclear to me exactly what you want to configure. Is your pad automatically recognized and working when you just plug it in, and now you'd like to reconfigure the stylus buttons? Something else? Are you able to adjust pressure sensitivity from within default GUI? Please describe your problem in as much detail as possible.

open terminal, enter ```
xsetwacom --list devices
``` copy paste here what your system returns.

---

### Post by kurja on 2014-10-11
> **raghav6 said:**
> [COLOR=#333333][FONT=arial]there isn't any such option in lubuntu as matter of fact there is no 'system setting' in lubuntu instead we have 'preferences' and 'system tools' and none of them contains any option[/FONT][/COLOR][FONT=arial][COLOR=#333333] for tablets[/COLOR][/FONT]

Ah! I see that you can't find the 'stock' gui for setting up anything about your pad, is that it? In 'vanilla' ubuntu it's under system settings or launches with ```
unity-control-center wacom
``` but I don't know about lubuntu, I've never used that. :-(

edit - found this [http://madebits.com/blog/?entry=entry130504-143320](http://madebits.com/blog/?entry=entry130504-143320)

---

### Post by raghav6 on 2014-10-14
> **kurja said:**
> edit - found this [http://madebits.com/blog/?entry=entry130504-143320](http://madebits.com/blog/?entry=entry130504-143320)
I've gone through that also.after scavenging around the web via Google for several hours I'm pretty sure I've came across every piece of information on this topic till this date :D 


> **kurja said:**
> Ah! I see that you can't find the 'stock' gui for setting up anything about your pad, is that it?

YES! YES! yes! exactly,I'm looking for such an application so that I can setup any thing about my pad. but so far no luck :(

---

### Post by kurja on 2014-10-14
well... I'm no expert on Lubuntu but doesn't look like there would be a gui available there. :(

But, despair not, setting stuff up with a script isn't *that *difficult, I mean, if I could do it... ;) And we can help you do it, too ;)

So, maybe you missed it above, what is the output of ```
[COLOR=#000000][FONT=Ubuntu Mono]xsetwacom --list devices[/FONT][/COLOR]
```

---

### Post by raghav6 on 2014-10-17
```
Wacom Bamboo One S Pen stylus       id: 10    type: STYLUS    
Wacom Bamboo One S Pen eraser       id: 17    type: ERASER    
Wacom Bamboo One S Pen stylus       id: 18    type: STYLUS    
Wacom Bamboo One S Pen eraser       id: 19    type: ERASER    

```

well I want control everything just like how it was in windows OS but, in particularly I'm looking for a way to swap x to -x and y to -y axis you see I'm s left hand operator so I need this kind of control :)

---

### Post by kurja on 2014-10-17
to change orientation 180 degrees on all devices for left handed use, run ```
for i in 10 17 18 19; do xsetwacom --set $i Rotate half; done
```

10 17 18 19 are of course your device id's, which might change if you hot plug or boot.

"Controlling everything just like how it was in windows" sadly isn't going to happen any minute now, without any gui at all you're left with command line and xsetwacom. Configuring the buttons should be easy enough, refer to the wiki pages linked to earlier in this thread. Go ahead and post back if there are any further problems with it.

---

### Post by raghav6 on 2014-10-26
OK that's it for now ha thank you so much for helping me out :)

---

### Post by kurja on 2014-10-27
do note that xsetwacom needs to be run after each boot or hot plug - you can set the script to run automatically though.

---

