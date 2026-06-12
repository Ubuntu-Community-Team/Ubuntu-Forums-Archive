---
title: "GIMP problems"
date: 2005-08-22
forum: General Help
---

### Post by MBro on 2005-08-22
Lately whenever I try to save while using the gimp it will close out as soon as I click on the save button even before the dialog opens.  I tried reinstallation but it didn't help, any suggestions?

---

### Post by Sai on 2005-08-22
[QUOTE=MBro]Lately whenever I try to save while using the gimp it will close out as soon as I click on the save button even before the dialog opens.  I tried reinstallation but it didn't help, any suggestions?[/QUOTE]
 Maybe you should try to delete .gimp (or something like this) catalog in your /home/user?

---

### Post by MBro on 2005-08-22
Sadly that didn't work either

---

### Post by skoal on 2005-08-22
Ahh...

I had the same problem many moons ago on a different Gimp revision on another distro.  It was a library issue if I remember correctly.  You may want to update your libgtk-x versions and see if that fixes it.  Until then, I'll try and remember what (or who) exactly was the offender.

Have you done any lib updates or distro upgrades recently?  If not, post back your Gimp and libgtk2 versions.  Mine: 2.2.2-1ubuntu5 and 2.6.4-0ubuntu3, respectively.  No such related issues as yours.

\\//_

---

### Post by MBro on 2005-08-22
libgtk2.0-0 2.6.4-0ubuntu3
gimp 2.28-1ubuntu1~5.04ubp1

---

### Post by coolclassic on 2005-08-22
I was working on a file yesterday that caused gimp to crash whilst saving but this was caused by working with a very large file. The cure was to increase the default 64mb of cashed ram to 256mb this was done using the preference option in gimp.

---

### Post by skoal on 2005-08-22
I think I remember some such similiar problem when using a newer (most recent) version of Gimp with an _older_ version of glib and/or gtk2 which worked fine on just one Gimp minor release down.  I think that's the case here.

Any of the following libraries could be the problem here:

GTK+(gtk2), GLib, Pango, ATK, FreeType2, and Fontconfig

I'm pretty sure that's whats causing your issue, since I had the _exact_ problem as you described it.  Anything else I was doing in Gimp at the time was _irrelevant_.  Hell, I could just fire up Gimp and immediately try to use the save dialog and it would crash.  For some reason, glib seems to come to mind as the offender...

That will happen on occasion with any application using Gtk+/Glib libraries.  I've seen it happen many times that version 2.6.7 of foo gets updated to 2.6.12 and the developers will use some simple widget change in latter versions of glib which breaks a whole suite of other apps.

I may be wrong here, and it may be something as simple as a recent font addition, "RenderAccel" option in Xorg, or other system library, but I'm pretty sure it's a recent glib use in 2.2.8 which the Gimp developer didn't take into account and update their requirements in their docs.

Let me know what you find out.  If available somewhere, you could try to update any one of those libraries listed above to minor or major release just above your current one, or downgrade back to 2.2.2.

\\//_

---

### Post by MBro on 2005-08-23
What would be the easiest way to downgrade to 2.2.2?

---

### Post by skoal on 2005-08-23
[QUOTE=MBro]What would be the easiest way to downgrade to 2.2.2?[/QUOTE]
oops! Must have missed your follow up...

There are two ways I suppose, and I'm providing these instructions all from rote memory (so there may be some syntax errors in the CLI version);

CLI:
sudo apt-get remove gimp
sudo apt-get install gimp=2.2.2-1ubuntu5

Synaptic:
hilight gimp package > Package > Mark for complete removal
hilight gimp package > Package > Force Version > select particular one

\\//_

---

### Post by drummer on 2005-08-23
[QUOTE=skoal]oops! Must have missed your follow up...

There are two ways I suppose, and I'm providing these instructions all from rote memory (so there may be some syntax errors in the CLI version);

CLI:
sudo apt-get remove gimp
sudo apt-get install gimp=2.2.2-1ubuntu5

Synaptic:
hilight gimp package > Package > Mark for complete removal
hilight gimp package > Package > Force Version > select particular one

\\//_[/QUOTE]
 I don't think you need to remove first to downgrade, forcing the version makes the package d/g on its own (but i guess you might still have olg config files, etc). Also, is the random crashing strictly gimp related? i've had the same problem now and then but also in FF. Not sure if the cause is the same as i haven't been able to catch any errors from either program.

---

### Post by MBro on 2005-08-24
Strictly gimp as of now.  Although I don't really save with anything else.  Although amaroK has been acting a little weird the past few days.  Every day at around 7am it makes my speakers start clicking and then won't play anything.  It's quite annoying seeing as it wakes me up but I doubt that's the same issue seeing as it deals with sound as is qt based.

---

