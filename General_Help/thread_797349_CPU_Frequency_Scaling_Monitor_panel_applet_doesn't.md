---
title: "CPU Frequency Scaling Monitor panel applet doesn't paint itself"
date: 2008-05-17
forum: General Help
---

### Post by svaens on 2008-05-17
Hi all, 

I was wondering if anyone else has had this problem. 

I have added the CPU Frequency Scaling Monitor panel applet to my top panel. 

Most of the time now when I boot up and log in, the applet on the panel is not painting itself, in otherwords, instead of seeing the little picture of a cpu, with the bar that shows you how hard it is working, all I get is a blank white square on the Panel. 
It doesn't happen every time, but most of the time. I don't bother having it up there anymore now, but i did liked it, and if it wouldn't have this problem, i'd put it back there.

oh yeah, of course, and I am using Ubuntu Hardy, 8.04

---

### Post by alex1973 on 2008-05-19
This is happening to me as well, on Hardy. Removing the applet and adding it back fixes the problem temporary.

---

### Post by vaxman- on 2008-11-12
> **svaens said:**
> Hi all, 

I was wondering if anyone else has had this problem. 

I have added the CPU Frequency Scaling Monitor panel applet to my top panel. 

Most of the time now when I boot up and log in, the applet on the panel is not painting itself, in otherwords, instead of seeing the little picture of a cpu, with the bar that shows you how hard it is working, all I get is a blank white square on the Panel. 
It doesn't happen every time, but most of the time. I don't bother having it up there anymore now, but i did liked it, and if it wouldn't have this problem, i'd put it back there.

oh yeah, of course, and I am using Ubuntu Hardy, 8.04
If it's any consolation, it still does this on 8.10.  I really would love to see this fixed already.

---

### Post by maiden30403 on 2008-11-19
I'm having the same problem, this is really annoying. No fix yet?

---

### Post by dixon on 2008-12-07
Confirming this issue.

EDIT: Here's [bugreport](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/267047)

---

### Post by B00R4dL3y on 2009-01-02
I find that when it does this, it's easier to just to right-click on an empty spot on the panel.  Then click on Properties (to get to the Panel Properties), then check or uncheck 'Show hide buttons', then check or uncheck 'Show hide buttons' a second time to get back to your original settings.

> **alex1973 said:**
> This is happening to me as well, on Hardy. Removing the applet and adding it back fixes the problem temporary.

---

### Post by peakpc on 2009-01-07
I am having the same issue after having upgraded to 8.10, 8.04 was rock sold and never had this issue, I keep wondering if it's an ATI driver or compiz or the applet or the panel. I do agree that it is very anoying.

After doing more research it would seem that some are saying that the applet doesn't like the panel transparency. I will test this out shortly.

---

### Post by jespdj on 2009-01-07
I have the same problem on 8.04, but on my system it does paint itself most of the time, but just occasionally it doesn't.

It's not a problem with the ATI graphics driver because I don't have an ATI graphics card.

---

### Post by theozzlives on 2009-01-07
Ubuntu doesn't support scaling, and as a tech I don't recommend it.

---

### Post by peakpc on 2009-01-07
I just put my panel background back to none(use system colors) instead of my custom image and it seems to be consistently showing properly now. But I really hate the look. So it would seem that it has to do with panel transparency and the applet.:confused:

---

### Post by InuY4sha on 2009-01-07
Same issue for me...
when I get home [IN A VERY SHORT TIME hopefully] I'm gonna try something & I'll let you know
R

---

### Post by InuY4sha on 2009-01-08
Ok.. so the issue is NOT related to the underlaying wallpaper (png or tiled/zoomed images and so on) but rather to the transparency used for the bar. Removing the bar transparency from its properties solves the issue.. This is not very nice but effective...

---

### Post by sledhead45 on 2009-01-09
Same problem for me with ibex

> I find that when it does this, it's easier to just to right-click on an empty spot on the panel. Then click on Properties (to get to the Panel Properties), then check or uncheck 'Show hide buttons', then check or uncheck 'Show hide buttons' a second time to get back to your original settings.

This didnt work for me.
I'm using the "slickness' gnome theme. I played with the transparency setting for the bar and that didn't bring the applet back either. So far the only way I can get it back is to remove it from the panel and re-add it. Annoying indeed.

---

### Post by peakpc on 2009-01-09
How many of us are using the auto hide feature on the panel?  I have found for me that it paints everything right if I point the mouse at the panel first before it has a chance to fully load, the panel pops out and paints as it should.  Can anyone else verify this? I don't want to give up any features, I like my desktop, I just want to see if I can help narrow down the problem.


Have been doing this for several days now seems to be 100% as long as i remember to move the mouse down to the bottom as its starting the panel, I do not except this as even a good work around, but, it is a point of note as to what it is that is causing the problem.

---

### Post by peakpc on 2009-01-15
bump

is this a dead issue or am I the only one?

---

### Post by mdurham on 2009-01-15
I right-click on the panel, select properties and increase then decrease the size to make it show.

---

### Post by sledhead45 on 2009-01-15
if you check the [bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/267047") it appears it was fixed yesterday (14jan09).

---

### Post by mdurham on 2009-01-15
> **sledhead45 said:**
> if you check the [bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/267047") it appears it was fixed yesterday (14jan09).

Thanks sledhead45, have a 'virtual' thanks too.

---

### Post by peakpc on 2009-01-16
yes thank you sledhead45, question though how long to reach down stream (to me)?

---

### Post by sledhead45 on 2009-01-16
> yes thank you sledhead45, question though how long to reach down stream (to me)? 
I'm not sure. If you don't want to wait you could probably install the gnome-applets development version from [here]("http://www.icewalkers.com/Linux/Software/58890/gnome-applets.html"). If your not comfortable with that I'd say just wait until Jaunty Jackalope is released.

---

