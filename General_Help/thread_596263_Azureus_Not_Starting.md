---
title: "Azureus Not Starting"
date: 2007-10-29
forum: General Help
---

### Post by Merrigan on 2007-10-29
Hi There,

I Have just upgraded my Computer, and with that also Installed Gutsy with it. I have not been having any issues, until I installed Azureus. No problems during the installation and all went smoothly.

When I tried starting azureus from the menu nothing happened. I couldn't figure it out, so naturally I tried it from the terminal, both as my user, as well as root, but to no avail. It pops out a few messages that I REALLY do not understand.

I uninstalled it, checked my Java settings tried everything I could find on the forum, but to no avail.

```

root@merrigansnest:/home/merrigan# azureus
changeLocale: *Default Language* != English (South Africa). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (South Africa)' (en_ZA), using 'English (default)'
Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-gtk-3346 or swt-gtk in swt.library.path, java.library.path or the jar file
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:219)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:151)
        at org.eclipse.swt.internal.C.<clinit>(C.java:21)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:128)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:80)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:61)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:110)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)
root@merrigansnest:/home/merrigan#

```

Any help will be greatly appreciated, as this issue is causing me to have to keep windows on my other pc for the moment. I need to keep my Azu running (don't want to miss anything you know :P) but I also want to slap ubuntu on there, and it's not happening without Azureus.

Thanks a lot!

[COLOR="Green"][B] -- Merrigan
 *The Silent Observer*[/B][/COLOR]

---

### Post by Kymus on 2007-10-29
I don't know if this will help any, but I've had similar issues with other programs. What seems to always work for me is to install them from the terminal.

try:
> sudo apt-get install azureus

good luck ;)

---

### Post by ferronica on 2007-10-29
same problem here, azureus not opening this is my fresh install gusty gibbon :( please help me please:(:(:(:(:(

---

### Post by pylon42 on 2007-10-29
Hello,

Not sure if this is the same problem you're having, but when I upgraded to 7.1 and installed Azureus it would load for a split second then vanish.

I upgraded from 2.5 -> 3 and the problem went away.

This isn't the link I used but, just in case it helps:
[http://www.getdeb.net/release.php?id=1699](http://www.getdeb.net/release.php?id=1699)

---

### Post by pylon42 on 2007-10-29
I should also mention that I later switched to Deluge and haven't looked back.

sudo apt-get install deluge-torrent

---

### Post by ferronica on 2007-10-29
can you please pm me on yahoo my Id ---> [email]ferronicao5@yahoo.com[/email]


i am online right now:):):):)

---

### Post by prshah on 2007-10-29
before you load azureus, delete its log files from the ".azureus" folder in your home directory. 

In a pinch, you can delete the entire folder, but then you will have to reconfigure azureus when it starts up.

Cheers,
Priyasen

---

### Post by Merrigan on 2007-10-29
> 
I don't know if this will help any, but I've had similar issues with other programs. What seems to always work for me is to install them from the terminal.


I Tried this, but no difference. I always try and install all software from the terminal, but yeah, this has made no difference.

> 
Hello,

Not sure if this is the same problem you're having, but when I upgraded to 7.1 and installed Azureus it would load for a split second then vanish.

I upgraded from 2.5 -> 3 and the problem went away.

This isn't the link I used but, just in case it helps:
[http://www.getdeb.net/release.php?id=1699](http://www.getdeb.net/release.php?id=1699)


Thanks a lot, but this happened to me when I used it on my 7.04 Installation. No Matter what I couldn't fix it, so out of desperation I tried installing it from automatix...and that seemed to do the trick.

I have upgraded to Version 3 as well, but to no avail.

> 
before you load azureus, delete its log files from the ".azureus" folder in your home directory.

In a pinch, you can delete the entire folder, but then you will have to reconfigure azureus when it starts up.

Cheers,
Priyasen


I tried this, just when I read it, and it also made no difference.

Upon looking at the error log I see the eclipse file mentioned a lot, is it not something to do with that? Is there any way I can test this theory of mine?

Thanx for the help so far guys, it's really appreciated!

UPDATE:
I have since recovered a backup of the file : **"org.eclipse.swt.gtk.linux.x86_64_3.2.2.v3236.jar"**. This has caused Azureus to now start up, but Just as the logo and loading progress bar finishes it dies again.

I Don't know what is causing this, but I know some progress has been made. I think I shall now reinstall the thing again and see what happens.

Thanx so far guys!

[B][COLOR='Green'] -- Merrigan
* The Silent Observer*[/B][/COLOR]

---

### Post by TokyoYank on 2007-10-29
I get the exact same error as OP.  I followed the instructions for manually updating & copying files as here:

[http://ubuntuforums.org/showthread.php?t=529431\](http://ubuntuforums.org/showthread.php?t=529431\)

Didn't work.  I even added . to $PATH

...  Can anyone who knows more than us reassemble the azureus package?  it seems very broken the past couple weeks

---

