---
title: "firefox 3 not showing images on multiple websites"
date: 2008-06-24
forum: General Help
---

### Post by autoreiv on 2008-06-24
Hi all,

Firefox 3.0 on an uptodate Ubuntu 8.04 does not seem to show images properly on image heavy websites such a search at images.google.com and [www.ikariam.org](www.ikariam.org)(after logging in - homepage is fine). 
It shows up a few images and then gets stuck halfway.

Tried these webpages on Konqueror 4.0.3, Firefox 2.0.0.14 on Ubuntu 8.04 and Firefox 3.0 on XP and they work just fine.

Video card is an Intel x3100 with 'Option "XAANoOffscreenPixmaps" "true"' enabled in xorg.conf

Not too sure where to go from here. Is there any logfile that could give more info?

Any advice would be much appreciated.

Attached is an example search on images.google.com using firefox 3.0 and konqueror 4.0.3 as comparison.

Thanks!

---

### Post by plucky on 2008-06-25
Google images page works fine for me.

Have you enabled image download in Firefox?

In Firefox **Edit > Preferences > Content** and make sure the boxes are ticked.

Have you installed **Ubuntu-restricted-extras** from the repositories?

That will install flash and java for you.


Good Luck

---

### Post by vishzilla on 2008-06-25
in Edit > Preferences > Content don't forget to check the Exceptions for the images

---

### Post by etnlIcarus on 2008-06-25
As well as the above advice, also keep in mind that you've just upgraded from Firefox 2.0 to 3.0 and your profile is quite possibly borked.

Open either a terminal or a run-dialog and run the following command:

firefox-3.0 -profilemanager

Create a new profile; choose that profile and see if images are loading.

---

### Post by autoreiv on 2008-06-25
I rebuilt my profile from scratch and it's working fine now! Great!
Cheers guys!

---

### Post by autoreiv on 2008-06-26
Unfortunately the problem is back again :s
I've rebuilt fresh profiles twice now and each time it works for a few hours and then reverts back to not showing images...
The addons I've got are Googlebar Lite, DownloadThemAll and Gmail Manager.

What I've noticed though is whenever Firefox gets stuck, other browsers get stuck randomly as well and have to close Firefox down for the other browsers to progress.

---

### Post by etnlIcarus on 2008-06-26
Honestly don't know. That's just odd. Have you tried uninstalling both firefox 2.0 and 3.0 and installing just one or the other?

---

### Post by autoreiv on 2008-07-01
Only had 3.0 installed.
I've now regressed to 2.0 which works great, but will keep 3.0 and try to figure out what's causing this...

Thanks for your help!

---

