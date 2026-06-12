---
title: "Screensaver settings for on, put monitor to sleep and put PC to sleep"
date: 2013-01-02
forum: General Help
---

### Post by Cavsfan on 2013-01-02
Does anyone know how to configure 12.04, 12.10 13.04 screensaver to work like it did in Lucid?

In Lucid I had my screensaver (gnome-screensaver) kick in after 10 minutes. Then after 30 minutes 
the monitor would turn off and after 1 hour of inactivity the PC would go into sleep mode (suspend).

I have yet to see any possible way to get any version after Lucid to work like that.

In Lucid, I had gnome-screensaver installed and not xscreensaver but, I had many of the parts of xscreensaver installed like xscreensaver-data, xscreensaver-gl, xscreensaver-data-extra and xscreensaver-gl-extra.

Gnome-screensaver is no longer supported and  xscreensaver is the only option.

Here is what I am talking about (the way it is in Lucid):

[[IMG]http://ubuntuforums.org/picture.php?albumid=2066&pictureid=8555[/IMG]]("http://ubuntuforums.org/picture.php?albumid=2066&pictureid=8555")

Then when you clicked on Power Management you seen this:

[[IMG]http://ubuntuforums.org/picture.php?albumid=2066&pictureid=8556[/IMG]]("http://ubuntuforums.org/picture.php?albumid=2066&pictureid=8556")

Does any one know how to do this? 

I would just like to get Precise, Quantal and Raring to work that same way.

I see some settings in Power Management but, don't want the PC to turn off, just go to sleep after an hour so I am lost as to how to set it up.

Thanks! :)

Edit: In Precise I have under System Settings > Power set to Suspend when inactive for one hour but, It seems to suspend in about 30 minutes and 
I don't know where that is coming from.

---

### Post by Cavsfan on 2013-01-05
No one knows how to do this: get any version after Lucid to work as above?

---

### Post by Cavsfan on 2013-02-18
That which was easy like setting these times to suspend with Lucid cannot be done in Precise?
I can click on suspend and it works well; much faster than windows but, I want to set it up to do it automatically.

Does no one know how to do this?

---

### Post by sudodus on 2013-02-18
> **Cavsfan said:**
> Does anyone know how to configure 12.04, 12.10 13.04 screensaver to work like it did in Lucid?

In Lucid I had my screensaver (gnome-screensaver) kick in after 10 minutes. Then after 30 minutes 
the monitor would turn off and after 1 hour of inactivity the PC would go into sleep mode (suspend).

...

I run Lubuntu 12.04 and I have not tried suspend, but I know about the first two settings.

The first one (screen-saver kick-in) is straight-forward

The second one is incremental, so you should enter 20 to turn off the monitor after 30 min (took me some time to find out).

---

### Post by Cavsfan on 2013-02-18
> **sudodus said:**
> I run Lubuntu 12.04 and I have not tried suspend, but I know about the first two settings.

The first one (screen-saver kick-in) is straight-forward

The second one is incremental, so you should enter 20 to turn off the monitor after 30 min (took me some time to find out).

Thanks for that, I think I have figured it out finally. I tried setting up the monitor in xscreensaver power management but, that did not work.

The first part is easy like you stated. I purged gnome-screensaver and installed xscreensaver and have it set to kick in after 10 minutes.

The 2nd part - turning the monitor off after 30 minutes can be achieved via System Settings - Brightness and Lock as shown:

[[IMG]http://ompldr.org/taGljcg[/IMG]]("http://ompldr.org/vaGljcg/turn screen off after 30 minutes.png")

Then the 3rd part of suspending the PC after one hour can be achieved via System Settings - Power as shown:

[[img]http://ompldr.org/taGljdQ[/img]](http://ompldr.org/vaGljdQ/suspend after 1 hour.png)

I have not let it happen but, it seems like this will work.

Thanks for the post :)

I'll resolve this after I see if it works as expected.

---

### Post by sudodus on 2013-02-18
It's easy to test it with one or two minutes instead of waiting for long times. And when you know how it works, you can set the long times you want for real usage.

---

### Post by Cavsfan on 2013-02-18
> **sudodus said:**
> It's easy to test it with one or two minutes instead of waiting for long times. And when you know how it works, you can set the long times you want for real usage.

Excellent idea! I'll do that.
Thanks! :)

---

### Post by sudodus on 2013-02-18
You are welcome :-)

---

### Post by Cavsfan on 2013-02-18
Well, on Raring the screensaver kicked in and it went into suspend mode but, the monitor did not turn off as expected.

I'll boot into Precise and try it there which is basically what my question was about.

---

### Post by Cavsfan on 2013-02-18
Same thing on Precise:

[[IMG]http://ompldr.org/taGljcg[/IMG]]("http://ompldr.org/vaGljcg/turn screen off after 30 minutes.png")

This setting had no effect at all. I had screensaver set to 2 minutes, put monitor to sleep after 3 minutes and suspend system after 5 minutes.
Again the monitor did not go to sleep although the other 2 worked well.

Am I interpreting that Brightness and Lock settings wrong? Everything was exactly as the picture looks but, the time at the top was 3 minutes.

I watched the 3 minute mark go by and at 5 minutes it suspended.

---

### Post by sudodus on 2013-02-18
It is hard for me to give exact answers, because I don't have English text in the screensaver settings windows, and I'm not sure how they should translate.

What I use is 'only blank screen' (with back-ground illumination on), then black screen (and lock screen), and it works as I described in my first post.

---

### Post by Cavsfan on 2013-02-18
> **sudodus said:**
> It is hard for me to give exact answers, because I don't have English text in the screensaver settings windows, and I'm not sure how they should translate.

What I use is 'only blank screen' (with back-ground illumination on), then black screen (and lock screen), and it works as I described in my first post.

OK Thanks! :)

---

