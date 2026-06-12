---
title: "[SOLVED] Firefox toolbars are too large and take up too much space"
date: 2008-07-01
forum: General Help
---

### Post by rhm on 2008-07-01
My screen resolution is 1280 x 768 and Firefox is taking up about a fifth of my screen. The font sizes seem more or less reasonable, but the toolbars are huge, both horizontally and vertically. I've browsed through the forums looking for help and I've found some people with the same problem/complaint yet no answers on how to solve this.

I'm attaching two screenshots comparing how Firefox looks in Ubuntu and in Windows XP on the same machine. I'm running Hardy 8.04 on an hp dv1000 series, Firefox/3.0 on both OS's.

Can anyone point me in the right direction with this? How can I make Firefox more similar to my XP configuration?

---

### Post by Vivaldi Gloria on 2008-07-01
> **rhm said:**
> My screen resolution is 1280 x 768 and Firefox is taking up about a fifth of my screen. 

Why don't you use small icons with no text under them? Right click on an icon an customize the icons.

---

### Post by powerpleb on 2008-07-01
You could put toolbar bookmarks into categorised folders...

Right mouse click on the toolbar > New folder

Drag them in there.

---

### Post by Harii on 2008-07-01
you could not use the toolbars at all?
That would save alot of space.
If your just surfing you could use NetSurf browser.

---

### Post by Vivaldi Gloria on 2008-07-01
Here is a snapshot of my firefox. I use the bookmarks menu rather than the toolbars.

---

### Post by soccerboy on 2008-07-01
> **rhm said:**
> My screen resolution is 1280 x 768 and Firefox is taking up about a fifth of my screen. The font sizes seem more or less reasonable, but the toolbars are huge, both horizontally and vertically. I've browsed through the forums looking for help and I've found some people with the same problem/complaint yet no answers on how to solve this.

I'm attaching two screenshots comparing how Firefox looks in Ubuntu and in Windows XP on the same machine. I'm running Hardy 8.04 on an hp dv1000 series, Firefox/3.0 on both OS's.

Can anyone point me in the right direction with this? How can I make Firefox more similar to my XP configuration?

That is the regular size for the toolbars in linux.

---

### Post by ad_267 on 2008-07-01
You could try using different gtk themes by going to System - Preferences - Appearance. Click on customize and change the controls used to something more compact. You can also download new gtk themes from [http://gnome-look.org](http://gnome-look.org).

---

### Post by powerpleb on 2008-07-01
Another thing you could do is install a compact firefox theme like this:
[https://addons.mozilla.org/en-US/firefox/addon/3699](https://addons.mozilla.org/en-US/firefox/addon/3699)

---

### Post by rhm on 2008-07-02
I have a feeling this has more to do with the screen resolution that I'm using than with Firefox. Your screenshots show a more or less "normal" toolbar size, proportional to your screens. Is anyone out there running a 1280 x 768 resolution experiencing the ugly, bulky Firefox?


> **Vivaldi Gloria said:**
> Why don't you use small icons with no text under them? Right click on an icon an customize the icons.

On principle, I feel Firefox should look more or less the same regardless of the OS. I'm slowly transitioning from Windows so that's my benchmark: it has to be at least that good (not that it would be a difficult task...)

In practice and thanks to your suggestion I am now using only icons. The small icons just don't do it for me yet. The space saved is enough to not make my eyes bleed, though I'm sure it could be made to look as small as the Windows one. This will do for now.



> **powerpleb said:**
> You could put toolbar bookmarks into categorised folders...

Right mouse click on the toolbar > New folder

Drag them in there.

I could and I'm using one folder. However, the bookmarks that are out there I access very frequently (compulsively frequently) and it only takes one mouse click as opposed to the two it would take in the folder. It may sound trivial but it gets old quickly. Besides, the point is to reduce the size of the toolbars to make it proportional to Windows


> **Harii said:**
> you could not use the toolbars at all?
That would save alot of space.
If your just surfing you could use NetSurf browser.

I can't begin to imagine life without toolbars... though it sounds like an interesting experiment. How would you go about that?

I'll look into NetSurf. Don't know what to expect yet.



> **Vivaldi Gloria said:**
> Here is a snapshot of my Firefox. I use the bookmarks menu rather than the toolbars.

I like how compact your Navigation toolbar looks. I use the bookmark menu a lot too, but the bookmarks on the toolbars are there because I want them to be a one-click easy access. At the risk of sounding stubborn, I would hope that there's a way to make it proportional to the size Windows has. After all, same browser, same computer, same resolution... 




> **soccerboy said:**
> That is the regular size for the toolbars in linux.

Well, this just sucks then =(.

Seriously though, can you point me to a reference where this is stated? It's ugly and I'm sure more than one Linux developer works on 1280 x 768 resolution, so they wouldn't do this to us newbies, would they?



> **ad_267 said:**
> You could try using different gtk themes by going to System - Preferences - Appearance. Click on customize and change the controls used to something more compact. You can also download new gtk themes from [http://gnome-look.org](http://gnome-look.org).

I'll definitely take a look at that link. I played around with the default gtk themes and none made it better (some made it worse). Thanks for the tip though.

> **powerpleb said:**
> Another thing you could do is install a compact firefox theme like this:
[https://addons.mozilla.org/en-US/firefox/addon/3699](https://addons.mozilla.org/en-US/firefox/addon/3699)

I've considered this, but before I cave, I want to make sure that there is absolutely, positively no way to reduce the size of those toolbars to something proportional to the ones in Windows. Thanks for the suggestion though.

---

### Post by s0l3x on 2008-07-13
You can also dive into userChrome.css and manually shrink down some elements:
[http://ubuntuforums.org/showthread.php?p=5380788#post5380788](http://ubuntuforums.org/showthread.php?p=5380788#post5380788)

---

### Post by SlalomMan on 2008-07-14
I've got the same problem on 1280x800; the stumbleupon/default toolbars seem to have a little bit of extra room around the buttons that could be saved. I dno't use the bookmark toolbar, so it's not as much of a problem. If you want to save space, might I recommend that you enable stumbleupon shortcuts and get rid of the toolbar alltogether? that way you can just press something like Alt + ` or another key combination and it will stumble, and you save that valuable real estate.

---

### Post by rhm on 2008-07-14
> **s0l3x said:**
> You can also dive into userChrome.css and manually shrink down some elements:
[http://ubuntuforums.org/showthread.php?p=5380788#post5380788](http://ubuntuforums.org/showthread.php?p=5380788#post5380788)

Thanks! this is what I was looking for. I tried your settings and they work awesomely. I'm sure that with a little more tweaking I'll get them up to where I want my FF to be. Thank you so much for this tip.

---

### Post by s0l3x on 2008-07-16
Glad that helped!

There's two more tweaks I found recently:

```

/* Merge Stop and Reload (make sure Stop is placed before Reload)*/
#stop-button[disabled] {
	display: none;
	}
	#stop-button:not([disabled]) + #reload-button {
		display: none;
		}

/* Remove Arrows on Toolbar Folders */
	#PersonalToolbar .toolbarbutton-menu-dropmarker {
		display: none !important;
		}

```

Also, what I found useful was decreasing the dpi setting (under System > Appearance > Fonts > Details) Previously, I had it set to 96, but now I'm at 84. (if you do decrease the dpi, you'll have to play around with userChrome again, so I've attached my latest file if you want it [remove .txt from the extension])

---

### Post by dannymichel on 2009-08-03
> **powerpleb said:**
> Another thing you could do is install a compact firefox theme like this:
[https://addons.mozilla.org/en-US/firefox/addon/3699](https://addons.mozilla.org/en-US/firefox/addon/3699)would be great. is a little too compact

---

### Post by mikewhatever on 2009-08-03
Can you also apply something like that to the status bar, the one at the bottom, in Firefox?

---

### Post by dannymichel on 2009-08-04
> **s0l3x said:**
> Glad that helped!

There's two more tweaks I found recently:

```

/* Merge Stop and Reload (make sure Stop is placed before Reload)*/
#stop-button[disabled] {
	display: none;
	}
	#stop-button:not([disabled]) + #reload-button {
		display: none;
		}

/* Remove Arrows on Toolbar Folders */
	#PersonalToolbar .toolbarbutton-menu-dropmarker {
		display: none !important;
		}

```

Also, what I found useful was decreasing the dpi setting (under System > Appearance > Fonts > Details) Previously, I had it set to 96, but now I'm at 84. (if you do decrease the dpi, you'll have to play around with userChrome again, so I've attached my latest file if you want it [remove .txt from the extension])
tried it. everything was way too small. tried messing with the css file but it didnt really effect spacing but rather shrunk things which is not what i'm looking for.
can we all find and inbetween classic compact and the regular large ubuntu firefox?

---

### Post by valmorel on 2009-08-04
Try this for an inbetween [https://addons.mozilla.org/en-US/firefox/addon/6174](https://addons.mozilla.org/en-US/firefox/addon/6174)

It is actually a Foxdie theme variant, of which there are several, but the Mozilla site seems a bit screwed up, so the one you download may not be the one in the photo LOL, but the creators web site explains how to get what you want. I 'downloaded' Foxdie Graphite, but got one of the sub themes. No matter............. it makes Firefox interface small, functional and gorgeous!

---

### Post by dannymichel on 2009-08-04
> **valmorel said:**
> Try this for an inbetween [https://addons.mozilla.org/en-US/firefox/addon/6174](https://addons.mozilla.org/en-US/firefox/addon/6174)

It is actually a Foxdie theme variant, of which there are several, but the Mozilla site seems a bit screwed up, so the one you download may not be the one in the photo LOL, but the creators web site explains how to get what you want. I 'downloaded' Foxdie Graphite, but got one of the sub themes. No matter............. it makes Firefox interface small, functional and gorgeous!
hmmm doesnt look like i can install it on 3.5
i remember installing it on 3.0 but the menues were white

---

### Post by os2 on 2013-01-09
> **valmorel said:**
> Try this for an inbetween [https://addons.mozilla.org/en-US/firefox/addon/6174](https://addons.mozilla.org/en-US/firefox/addon/6174)

It is actually a Foxdie theme variant, of which there are several, but the Mozilla site seems a bit screwed up, so the one you download may not be the one in the photo LOL, but the creators web site explains how to get what you want. I 'downloaded' Foxdie Graphite, but got one of the sub themes. No matter............. it makes Firefox interface small, functional and gorgeous!

Yes almost as nice as dannymichel..

---

