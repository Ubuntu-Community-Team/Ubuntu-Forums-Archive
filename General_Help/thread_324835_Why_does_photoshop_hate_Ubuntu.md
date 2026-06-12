---
title: "Why does photoshop hate Ubuntu?"
date: 2006-12-24
forum: General Help
---

### Post by FeraTech on 2006-12-24
_Photoshop CS2_
I have spent about 16 hours trying to install Photoshop. I first tried CS2 and went through all the tutorials but eventually gave up. I could not get past the serial number error. I went through and imported all the registry entries from windows without success.

_Photoshop 7.0_
So this installed perfectly. No problems there. However, when trying to run it, it would error out. After a couple hours of searching I finally deleted all the wacom entries from my "xorg.conf". 

Finally I got Photoshop 7.0 to work.

However, Photoshop's windows and menus are terrible. I can't minimize it because all the menus remain open! Dreamweaver in comparison is amazing. However, unlike Dreamweaver you can't seem to be able to dock the Photoshop windows.

I can't use any other programs while photoshop is open. It's terrible, anybody know a way around this? I've tried all the option in wine. I checked the photoshop options and that doesn't help eigther.

---

### Post by ChristopherMonahan on 2006-12-25
wine is generally not a perfect solution, trying to get windows programs to run on linux is like trying to run a jet engine on 95p per litre unleaded.

Or would the analogy be, running a ford escort on kerosene? you decide which way round it is, anyway...

All things considered wine does some amazing stuff, unfortunately a lot of the time, amazing stuff just isn't enough

Wine is working hard on photoshop, it's a target for version 1, if i remember correctly - anyway this is really a wine problem rather than a ubuntu problem

try at [wineHQ]("http://www.winehq.com/") ask there, and make sure to check the application database, they may have some tips on getting photoshop to work

---

### Post by letherian on 2006-12-25
Yo there!

Ever tried GIMP? I'm not so much in to photo-working, but it's worth a shot? :)

Also, if you can't use anything other than photoshop try installing Crossover Linux :)

-- Leth

---

### Post by FeraTech on 2006-12-25
Yes, however the problem with Gimp is that it does not possess the same functionality as Photoshop. I do a lot of professional graphical design and Photoshop's layer handling is unmatched.

I do have photoshop working I just have 1 issue that I need help resolved.

I need to be able to dock the main toolbar. It's free floating as a standard setting and Wine doesn't know what to do with it. The toolbar just hovers covering all my screen. I tried looking at the Wine HQ but haven't found anything specific to that issue.

---

### Post by EmmEff on 2006-12-25
In all seriousness, if you need to run Windows apps, then you must run the Windows OS.  Have you investigated using VMware for virtualizing Windows?  If you have fast hardware, it might be good enough to run PS once in a while.

---

### Post by letherian on 2006-12-26
Well then, i presume youre working with Wine?

Have you tried CXOffice Linux?


Good luck  and merry christmas :)


--Leth

As i was browsing the web today i came over a program called GimpShop, ever heard of it? :)

---

### Post by Sef on 2006-12-26
Here's Wine's take on [PhotoshopCS2]("http://appdb.winehq.org/appview.php?iVersionId=2631").

Here's Wine's take on [Photoshop 7.0]("http://appdb.winehq.org/appview.php?iVersionId=1336").

---

### Post by Shay Stephens on 2006-12-26
I am a photographer, so I understand your needs here.  Yes, the problem with running PS7 in wine is real, and as yet not solvable.  But I can still get all my work done using it, it just takes a little bit of retraining so you don't do stuff that will lock it up. 

One tip, get the windows the way you like them, then save that workspace.  When things get out of hand, just restore that workspace.  Don't resize toolbars manually.  If the little tool buttons at the bottom of the layer pallet are not showing, switch to the channels tab then switch back to the layers tab, the buttons should be back, though the pallet will auto resize.

I have PS7 working pretty good in crossover office, but usually find myself running it in wine.  I have not tried the latest version of crossover office yet, there may be better performance there.

Gimp is not currently a substitute for PS.  People who don't do a lot of graphics editing should really leave off suggesting it ;-)  I have been using it and currently am porting my actions into python-fu.  It has a lot of functionality, however, as mentioned, it's ability to work with layers is very limited, and it's text layout is horrible just to mention two deficiencies.  

Now that being said, gimp does about 80% of what PS can do, and if you don't need that last 20%, then gimp is a great tool.  I am using it for a number of things now.  I plan on eventually switching to it 100% because I am not going to use any more Photoshop versions that impose activation schemes like windows.

---

### Post by Shay Stephens on 2006-12-26
> **letherian said:**
> As i was browsing the web today i came over a program called GimpShop, ever heard of it? :)

Gimpshop is gimp with rearranged menus.  It does not solve the lack of functionality gimp has in layers, text layout, etc. compared to photoshop.  If gimp does not work for someone on a functionality aspect, gimpshop is not going to either.

---

### Post by Cows on 2006-12-27
Yes I was a photoshop CS2 , but it is to much of a hassle. Also as you all know Adobe Photoshop CS2 is about $1,200 USD.. While Gimp does 80% of the job as said above and its totally free of cost. I think people can manage with Gimp.

---

