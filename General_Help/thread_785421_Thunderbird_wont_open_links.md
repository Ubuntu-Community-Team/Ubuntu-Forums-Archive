---
title: "Thunderbird wont open links"
date: 2008-05-07
forum: General Help
---

### Post by Kilarin on 2008-05-07
I upgraded from 7.10 to 8.04, and now I've got an interesting glitch.
Clicking on an http:// link in a Thunderbird message will no longer open that link in firefox.  This functionality worked just fine before the upgrade.  So I'm not certain if the problem is in Hardy, Thunderbird, or Firefox.  Thunderbird updated to the newest version from the repositories yesterday, but that did not fix the links problem.

Ubuntu 8.04 up to date as of this morning.
Thunderbird 2.0.0.14 (20080505),
Firefox Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5

Any help would be much appreciated.  Thanks!

---

### Post by rothbert on 2008-05-08
In the last day or so I have come across the same issue. 

Recently upgraded from 7.10 to 8.04 (64 bit). I uninstalled the default installation of Firefox 3.0B5 as it can't run a few addons that I use regularly. Had to do a clean reinstall of Firefox 2 to get addons working again.

I'm also using Thunderbird 2.0.0.14 (20080505). Not sure exactly when the problem started but don't think it was immediately after my Ubuntu upgrade. Might have been after the recent Thunderbird upgrade. Clicking on links in an email produces no results.

I have a similar issue with html files on the desktop. Whereas previously clicking on them brought up a dialog box with options to display, run etc., now nothing. Have to right click and use 'open with...'


thanks

---

### Post by rothbert on 2008-05-09
This thread, [http://ubuntuforums.org/showthread.php?t=772112&highlight=thunderbird+links+firefox](http://ubuntuforums.org/showthread.php?t=772112&highlight=thunderbird+links+firefox)
solved the Thunderbird links issue for me. Tweaking config editor in Thunderbird as suggested (with usr/bin/firefox-2, rather than usr/bin/firefox) did the trick.

---

### Post by Kilarin on 2008-05-11
[quote="rothbert"]This thread, [http://ubuntuforums.org/showthread.p...+links+firefox](http://ubuntuforums.org/showthread.p...+links+firefox)
solved the Thunderbird links issue for me. Tweaking config editor in Thunderbird as suggested (with usr/bin/firefox-2, rather than usr/bin/firefox) did the trick. [/quote]
> in thunderbird:
    * network.protocol-handler.app.http
    * network.protocol-handler.app.https
thank you very much!, but I'm still having a problem. :(
When I go into Thunderbird/Preferences/Config Editor
I don't have an entry for network.protocol-handler.app of any kind.
Should I add them?  (By editing the config file directly I would assume)

---

### Post by rothbert on 2008-05-11
Yes, you will need to add them. Some detailed instructions here: [http://justanothertechblog.blogspot.com/2006/07/thunderbird-configured-to-open-links.html](http://justanothertechblog.blogspot.com/2006/07/thunderbird-configured-to-open-links.html) and I think you'll need to use /usr/bin/firefox-3/ as your path to FF. 

A handy test is go to terminal and type "/usr/bin/firefox-3 http://www.google.com" (without the quotes) and it should open Google in your browser if that is the correct path.

good luck

---

### Post by Kilarin on 2008-05-12
> Yes, you will need to add them. Some detailed instructions here: [http://justanothertechblog.blogspot....pen-links.html](http://justanothertechblog.blogspot....pen-links.html) 
Perfect!  that worked fine!  

BUT, at least on my computer, even though I'm running firefox 3 beta 5, the path has to be:
/usr/bin/firefox-2

Thank you VERY much!

---

### Post by Kilarin on 2008-05-13
alas, firefox-2 works, as long as I have firefox-3 open, calling /usr/bin/firefox-2 DOES open the link in the running firefox-3.  BUT, if I DON'T have firefox 3 up and running, then thunderbird opens the old firefox-2.

SO, does anyone know where the firefox-3 program resides, since when I try /usr/bin/firefox-3  I get: No such file or directory?

Thanks!

---

### Post by avtolle on 2008-05-13
Try /usr/bin/firefox-3.0.

---

### Post by Kilarin on 2008-05-13
> Try /usr/bin/firefox-3.0
Huzzah!  thank you VERY much!

I should have been able to see that when I browsed usr/bin, but somehow I missed it.  thanks!

---

