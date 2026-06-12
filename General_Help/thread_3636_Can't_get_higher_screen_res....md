---
title: "Can't get higher screen res..."
date: 2004-11-08
forum: General Help
---

### Post by Mike Finn on 2004-11-08
Hello ..

I have a laptop that includes a Intel 82852/855GM graphic card. It's onboard and the ram is taken from system ram via a setting in the BIOS. From reading various docs it seems that Ubuntu is seeing the ram which is on the device and not including the ram allocated from system ram, therefore only allowing a max res of 1024x768.

Any clues about how I might fix this situation..??

I am Linux challenged ...for now :) 

Mike

---

### Post by Burgundavia on 2004-11-08
You can try and run XF86Config-4 as root from the command line, as it will walk you through resetting up your X config file. Be careful, as you can really (mess) up your config and render your X unbootable (but you can still but to text only). If you really malf your setup you can reinstall. 

Corey

Mod note: Let's keep the language clean please, thanks.

---

### Post by Mike Finn on 2004-11-08
Hi Corey...

Yep.... did that twice looking for a section to allocate ram... not there. I did manage to set it higher in one of the menus but alas it made no difference. I am pretty sure those settings only effect detected hardware and as mine is not being detected correctly all is in vain..... I could be wrong....I was once :)

Mike

---

### Post by ulrich on 2004-11-08
are you sure its the video-ram?
cause if x doesent fill in the right specs for your display it wont let you set up higher resolutions either.
have you checked 
     ```
Section Monitor
```
for the appropriate settings in your XF86Config-4-file?

---

### Post by Rancoras on 2004-11-08
[QUOTE=ulrich]are you sure its the video-ram?
cause if x doesent fill in the right specs for your display it wont let you set up higher resolutions either.
have you checked 
     ```
Section Monitor
```
for the appropriate settings in your XF86Config-4-file?[/QUOTE]

Make sure they match the specs listed in your monitor manual.  If you don't have the manual, try the manufacturer web site.

---

### Post by mattyh on 2004-11-08
I've look around the net for Intel 82852/855GM XF86Config files and here is a link to one: [http://people.easter-eggs.org/~valos/Asus_M2400N/XF86Config-4](http://people.easter-eggs.org/~valos/Asus_M2400N/XF86Config-4).
 
 If you could tell us what brand/model your laptop is I could probably find a better solution.  Hope this points you in the right direction.

---

### Post by wallijonn on 2004-11-08
#
```
/usr/X11R6/bin/xf86cfg
```

---

### Post by Mike Finn on 2004-11-08
Thanks all... So far I cannot find a manual with a cfg file for my exact model... the link given by Mattyh (thanks) is for a GME model and mine is only a GM and the settings seem to be quite different.

Using /usr/X11R6/bin/xf86cfg shows this [http://homepages.slingshot.co.nz/~mikefinn/123/Screenshot.png](http://homepages.slingshot.co.nz/~mikefinn/123/Screenshot.png)
[IMG]homepages.slingshot.co.nz/~mikefinn/123/Screenshot.png[/IMG] 
Which says it can do 1280...but I run it at 1400x1050 in windows and Ubuntu only allows 1024.

Ok the questions are..
If I click that 1280 setting and say OK., will it work? 
and
Is there a graceful way to recover if it screws things :)

Mike

---

### Post by adbak on 2004-11-08
[QUOTE=Mike Finn]
Is there a graceful way to recover if it screws things :)
Mike[/QUOTE]

I don't know if there's a graceful way to recover things for sure, but you could always try the recovery mode on GRUB.  Either that or you could use Knoppix, for example, to recover it.  You'd have to unmount and then remount (with read/write privileges to boot) your linux partition.

---

### Post by mattyh on 2004-11-08
If you change the resolution under Gnome using Computer->System Configuration->Screen Resolution, if things go badly it will default back to your previous settings.  The problem is getting Gnome to let you change it to that higher resolution.  I can't say that I'm too comfortable trying to explain how to do that.  Hopefully, someone with a little more experience in that field will be able to explain how to do it.

---

