---
title: "Opera fonts are small , not good"
date: 2008-06-22
forum: General Help
---

### Post by sunshine12 on 2008-06-22
Opera is not rendering my fonts well and It seems the text is small, firefox do it well and fonts are good!!
Done some twicking with "enable x core " sth, but nothing happened...

This is the screenshot from the opera and firefox...

1st image is from opera and 2nd from Firefox..

---

### Post by TeoBigusGeekus on 2008-06-22
Opera looks much nicer...
Anyway, you can go to tools->preferences->advanced->fonts and do all your adjustments from there.

---

### Post by sunshine12 on 2008-06-22
It is good but the words look somewhat smaller and congested to me..

I tried everything, but it doen't change. Should I use shared version of opera. Right now I am using the version that is provided in main site. Don't know if it is "shared or static" and what difference it make, just a thought.

Here is the screenshot of how OPERA looks in XP..

---

### Post by sunshine12 on 2008-06-23
I am not using OPERA because of this font rendering problem.. Fonts are smaller than normal and I can't change it, nomatter how I tweak the fonts settings..

Like in Firefox I disabled "Allow pages to choose the fonts over my selected fonts" and everything is normal.. Is there such setting in OPERA??

Thanks

---

### Post by dracayr on 2008-06-23
you can always zoom in/out with Ctrl++ and Ctrl+- press * on the numpad for the actual page zoom

dracayr

---

### Post by juamez. on 2008-06-27
Fonts are not just smaller in Opera, they are broader but lower. The proportions are just wrong. If you try to enlarge them with zoom, they get higher but will still be to wide or broad. This f*ckedupness of font size and proportions is indeed very annoying.

If only someone knows what the origin is of this problem, and more importantly: how it can be fixed!

I was disappointed in the latest version of Ubuntu just because of this problem. Just like someone already said: fonts are like the most important aspect of an OS, ever! If fonts are bad, ugly or non-ergonomic, too bad but the OS has to go.

As an example: when you install msttcorefonts and run Opera in ubuntu 8.04, the font Arial will look essentially as broad as the linux font "sans", which isn't supposed to look like Arial AT ALL! What gives?

edit: proof for the Arial screw-up: [http://ubuntuforums.org/showpost.php?p=5169174&postcount=16](http://ubuntuforums.org/showpost.php?p=5169174&postcount=16)
Look at the screenshots from tweakers.net, they show off the Arial font really good. FF3 is fixed/fine, Opera in windows is fine too, but Opera in Ubuntu 8.04 is really messed up.

---

### Post by sunshine12 on 2008-06-27
> **juamez. said:**
> Fonts are not just smaller in Opera, they are broader but lower. The proportions are just wrong. If you try to enlarge them with zoom, they get higher but will still be to wide or broad. This f*ckedupness of font size and proportions is indeed very annoying.

If only someone knows what the origin is of this problem, and more importantly: how it can be fixed!

I was disappointed in the latest version of Ubuntu just because of this problem. Just like someone already said: fonts are like the most important aspect of an OS, ever! If fonts are bad, ugly or non-ergonomic, too bad but the OS has to go.

As an example: when you install msttcorefonts and run Opera in ubuntu 8.04, the font Arial will look essentially as broad as the linux font "sans", which isn't supposed to look like Arial AT ALL! What gives?

edit: proof for the Arial screw-up: [http://ubuntuforums.org/showpost.php?p=5169174&postcount=16](http://ubuntuforums.org/showpost.php?p=5169174&postcount=16)
Look at the screenshots from tweakers.net, they show off the Arial font really good. FF3 is fixed/fine, Opera in windows is fine too, but Opera in Ubuntu 8.04 is really messed up.

Anybody having the read solution to this problem?
Please suggest if one have, I use firefox and opera both.. so don't want to quit opera just because of this font problem!!

Thanks..

---

### Post by gladstone on 2008-07-16
There have been a few threads about this, it is something to do with QT3(4) apps hinting/antialiasing user preferences being ignored and are set based upon symlinks located at /etc/fonts/conf.d (i.e. defaulted at medium font hinting, no subpixel hinting).

There is a link on here: [http://ubuntuforums.org/showthread.php?t=814568](http://ubuntuforums.org/showthread.php?t=814568) which is how I'm running it atm, but it still isn't perfect.

Opera 9.52 (beta) unfortunately [hasn't fixed this]("http://ubuntuforums.org/showthread.php?t=805851"), though you might want to try, as per that thread, unchecking "**Enable Core X Fonts**" in opera:config > User Prefs.

---

### Post by juamez. on 2008-07-23
Have not yet tested the Disabling of Core X Fonts, but what about the total wreckaging of the msttcorefonts? It's not just the subpixel hinting that goes wrong, but the whole shape of the font. It's like you're looking at different fonts.

---

### Post by feffo on 2009-02-02
I also use opera and I was dissappointed how bad were the fonts with ubuntu... I've installed msstcorefonts but this didn't improve the situation.
Then I found a blog that said to write in terminal:
cd /etc/fonts/conf.d
sudo rm 10-hinting-medium.conf
sudo rm 10-no-sub-pixel.conf
sudo ln -s ../conf.avail/10-hinting-full.conf
I did this and opera has really god font now! Better than firefox 3 in my opinion... With this tweak if you enable x fonts is a little nicer. Give it I try for me is the only think that worked!

---

### Post by Lunx on 2009-02-02
> **feffo said:**
> I also use opera and I was dissappointed how bad were the fonts with ubuntu... I've installed msstcorefonts but this didn't improve the situation.
Then I found a blog that said to write in terminal:
cd /etc/fonts/conf.d
sudo rm 10-hinting-medium.conf
sudo rm 10-no-sub-pixel.conf
sudo ln -s ../conf.avail/10-hinting-full.conf
I did this and opera has really god font now! Better than firefox 3 in my opinion... With this tweak if you enable x fonts is a little nicer. Give it I try for me is the only think that worked!

Thanks for that, been messing about with settings and had things looking okay, but not quite right. Just ran those commands and it seems to have done the trick (but now I have to change fonts again in Opera, this text box looks rather weird with the setting I've got.

---

### Post by hugmenot on 2009-02-03
Increase [this value]("opera:config#UserPrefs|ForceDPI") to the point where the fonts look big enough for you.

---

### Post by cl333r on 2009-02-15
I remember Forefox 2.x used to have this (very important  usability) issue - because of that I was still using windows XP. That's why I've been waiting for Firefox 3 and now I'm almost OK with both Linux and Firefox (although the xp version is faster, I tested, most likely has nothing to do with Linux but rather with Firefox's code for Linux).
It really doesn't matter that Opera completes the acid 3 test better than Firefox, it stands no chance to win Linux users as long as it doesn't fix the fonts issue and doesn't come up with an adblock like extension.
The only thing I care about Opera is that unlike Firefox it has a good (cold) startup time and if Firefox did this enhancement it would be more important to me than faster JavaScript engine or better acid 3 test results.

---

### Post by Vines on 2009-03-16
Thanks feffo, this does the trick. Moreover, it has fixed the same font trouble in Amarok too. Guess that is true for any Qt3 application.

---

### Post by felipero on 2009-04-29
Look for the file ~/.opera/opera6.ini and add "Enable Core X Fonts=0" to the User Prefs section.

Worked pretty well for me.

---

### Post by Chris Musampa on 2009-04-29
> **cl333r said:**
> I remember Forefox 2.x used to have this (very important  usability) issue - because of that I was still using windows XP. That's why I've been waiting for Firefox 3 and now I'm almost OK with both Linux and Firefox (although the xp version is faster, I tested, most likely has nothing to do with Linux but rather with Firefox's code for Linux).
It really doesn't matter that Opera completes the acid 3 test better than Firefox, it stands no chance to win Linux users as long as it doesn't fix the fonts issue and doesn't come up with an adblock like extension.
The only thing I care about Opera is that unlike Firefox it has a good (cold) startup time and if Firefox did this enhancement it would be more important to me than faster JavaScript engine or better acid 3 test results.

I suspect you mean it won't win Gnome users rather than Linux users, no issues with Opera in KDE.  Opera doesn't need an extension for adblocking, this is built in, simply right click on a web page and select 'Block Content'.

---

### Post by Drakeo on 2010-01-19
> **felipero said:**
> Look for the file ~/.opera/opera6.ini and add "Enable Core X Fonts=0" to the User Prefs section.

Worked pretty well for me. Well the problem was solved on the third post. click Tools->Preferences->Advance->Fonts 
Now set to minimum font size. now tab over to Web pages and set up your fonts and header sizes.
 Gould luck all. Microsoft pays millions to make it hard on opera. If your opera does not render right complain to the wbmaster to get it working with opera.

---

### Post by lyall on 2010-01-19
in Opera click on View > Style > User mode

I also set the fonts to all Arial 12 in Appearance Preferences

It does not look to bad

good luck and have fun learning

---

### Post by craetech on 2010-03-15
Installing msttcorefonts worked for me. I'm currently using Opera 10.10 on Kubuntu Karmic.

Deleting the .conf files looked scary to me. If you need to increase font size, I suggest to goto 'Tools > Preferences... > Advanced > Fonts' and increasing Minimum font size (pixels) to something like 13. Only tricky part is getting it just right for your system as setting too high values tend to cause mis-alignment in pages.

Don't forget to restart Opera for the changes to take effect.

---

