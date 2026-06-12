---
title: "Install Mouse Cursors?"
date: 2007-01-21
forum: General Help
---

### Post by antisho on 2007-01-21
Can I install new mouse cursors? In System/Preferences/Mouse/Pointers it only lets me choose from a list of themes; I can't add any new ones. I'm using Edgy, but the same was true in Dapper.

---

### Post by mahiyar on 2007-01-25
You can go to Gnome look .org download as many mouse cursor themes you like. However do not install it using "theme install", just extract the tar file in your home folder in the .icons directory. The next time you go In System/Preferences/Mouse/Pointers you can see the new themes available.

---

### Post by dinkins on 2007-01-31
> **mahiyar said:**
> You can go to Gnome look .org download as many mouse cursor themes you like. However do not install it using "theme install", just extract the tar file in your home folder in the .icons directory. The next time you go In System/Preferences/Mouse/Pointers you can see the new themes available.

Oh crap. I did exactly this, trying to install them through the "theme install" way, and now my entire ubuntu is crashed, save for my Failsafe Gnome interface. how can I revert to what I had before in my xgl launch? I need help badly, I am only a few days old at this and it appears I have already fubar'd my system. :(

Edit: Sorry, I should give information on exactly what is Fubar.

When I load into my XGL launch for Beryl and 3ddesktop and everything, after trying to install my cursor icons through System > Preferences > Themes, it doesn't finish loading on the spash screen and hangs on a themeless, lifeless screen until I hard shutdown my computer. I can get into gnome's failsafe fine, but if I try to get into normal gnome or xgl (is it called xgl? i cant remember) i get that hang now.

Oh please help

---

### Post by mahiyar on 2007-01-31
Dont panic, what are forums for? I learnt from the mistake. When you boot in you use the recovery mode. This will take you to command line interface, there cd to ~/.icons on using the ls -al command you will see the list of directories, delete the latest theme directory which is causing the problem, log back again normally.

---

### Post by dinkins on 2007-01-31
Awesome! It worked, thank you so much for the help. I learned how to remove directories and files, now, too :) 

Thanks for the help.

---

### Post by jeyaganesh on 2007-02-01
For installing new cursors, desklets, splash screens and login screens, please visit [http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694).

For installing cursors;

This does require extra files or applications.
1. First we have to install gcursor application (cursor manager) on Ubuntu. Open the terminal and write:

[COLOR="Red"]sudo aptitude install gcursor[/COLOR]

2. Go to Gnome-look.org and pick the cursor(s) you want.
3. Go to System tab ---> Preferences ---> Cursor Selection.
4. Push the Install Theme button, browse and select the cursor. No need to unpack the cursor files. Gcursor will do that for you.
5. Now pick the cursor you want in the Xcursor menu and press the Close button. The new cursor will first appear when you log in next time.


NOTE: If the cursor you have selected in gcursor don't appear in the menu then press the Go To Theme Folder button, click the folder named after the cursor. There should be a new folder with the name of you cursor in there. Right click it and choose cut. Press the Up button in your file browser and Paste the file here. That should do the trick.

Have fun!

---

### Post by j0n3 on 2007-02-12
Try to run gcursor as "user" you want cursors for, instead of root. It worked out for me.

---

### Post by mahiyar on 2007-02-12
Nice info jeyaganesh -- Thanks.

---

### Post by rcatman on 2007-05-31
KTHANXBYE!

lol

But seriously, no more LOLCODE i promise, this was exactly what I was looking for. I wonder why these things aren't included in a default installation. I remember in dapper I could drag a tar.gz file (downloaded from gnome-look) onto the cursor-theme selection screen and it would install. Thanks!

Worked perfect! XD

---

### Post by dmber on 2007-10-27
hitting "install" in Cursor Selection does nothing.

i'd like to install some new cursors but cannot figure out how.

---

### Post by mgurquiza on 2007-10-31
> **dmber said:**
> hitting "install" in Cursor Selection does nothing.

i'd like to install some new cursors but cannot figure out how.
i have the exact same problem. i figured out how to get them to show though (by copying and pasting on the .icons folder) (thanx mahiyar) but i cant use them.

---

### Post by mahiyar on 2007-10-31
If you are using gutsy >>System>preferrences>appearence>theme>customize>pointer from there you will see all the pointers that were copied in .icons folder and select the same.

---

### Post by nym.null on 2007-11-01
> **mahiyar said:**
> If you are using gutsy >>System>preferrences>appearence>theme>customize>pointer from there you will see all the pointers that were copied in .icons folder and select the same.
The path is actually (for me):
System > Preferences > Appearance > Customize (button) > Pointer (tab)

Or you can use gcursor directly:
System > Preferences > Cursor Selection

But no matter, it doesn't work either way.

Via the first route, at least the cursor theme I copied to .icons is visible.
But no changes are possible.  The direct *gcursor* route lists only 'default' and the apparent core installed options, but nothing from the .icons folder.   None of the controls function from that app window.

Gcursor is b0rked on Gutsy for some/many, including me.

[http://ubuntuforums.org/showthread.php?t=527185&highlight=gcursor+gutsy](http://ubuntuforums.org/showthread.php?t=527185&highlight=gcursor+gutsy)
[http://ubuntuforums.org/showthread.php?t=565617&highlight=gcursor+gutsy](http://ubuntuforums.org/showthread.php?t=565617&highlight=gcursor+gutsy)
[http://ubuntuforums.org/showthread.php?t=588847&highlight=gcursor+gutsy](http://ubuntuforums.org/showthread.php?t=588847&highlight=gcursor+gutsy)

Any help out there?

---

### Post by Redenbacher on 2007-11-15
No need for gcursor, just extract themes into .icons folder and they show up in Appearance -> Theme -> Customize -> Pointer

My only problem is that when I install a custom theme, it's only visible in Firefox... when I'm milling around on the desktop it's back to default. Any reasons?

---

### Post by mahiyar on 2007-11-16
I use this behavior (different pointers) to impress my windows friends. I boasted that Ubuntu had multi-pointer theme facility. LOL. but yes even I wonder why is that.

---

### Post by mahiyar on 2007-11-16
The multi-pointer behavior has nothing to do with themes, this goes away the moment you de-select special effects.

---

