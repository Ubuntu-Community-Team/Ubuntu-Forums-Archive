---
title: "where are the program files located"
date: 2013-12-13
forum: General Help
---

### Post by rajpier on 2013-12-13
When looking at the file directory where are the programs located .  I have to find Chrome for instance now to set it as a default for something.

---

### Post by philinux on 2013-12-13
If you're using ubuntu then top right gear on desktop gets you system setting. You can set default apps from there.

---

### Post by andyfied on 2013-12-13
Well /usr/bin has most of them in, but I'm not sure that will help you. Try right clicking the file and go to properties. This thread goes into a bit more details about doing it from the command line: [http://ubuntuforums.org/showthread.php?t=2001865](http://ubuntuforums.org/showthread.php?t=2001865)

---

### Post by Impavidus on 2013-12-13
To find chrome, try```
whereis chrome
```I think it will be in /usr/bin, maybe in /opt/something.

---

### Post by codemaniac on 2013-12-13
you can use ***which*** command which simply locates a command or installed binary. :)

***whereis*** a bit verbose on the other hand, it locates the binary, source, and manual page files for a command

```

fego@production:~$ which chromium-browser
/usr/bin/chromium-browser
fego@production:~$ whereis chromium-browser
chromium-browser: /usr/bin/chromium-browser /etc/chromium-browser /usr/lib/chromium-browser /usr/bin/X11/chromium-browser /usr/share/chromium-browser /usr/share/man/man1/chromium-browser.1.gz

```

---

### Post by rajpier on 2013-12-13
Well it's complicated. I need to be able to click on the file location. My stock  market site has a streaming quote ap that use Java jnlp , whatever that is. I use Chrome for places where I must use Java because I have figured out how to select sites to allow it. For whatever reason when I click on this jnlp file it asks to open it with Firefox or Other,, even though I have Chrome as my default browser.  The thing is I can't find the location of the Chrome program files.

Well I found it there but it doesn't work.

---

### Post by jimmyh1972 on 2013-12-17
you can go to system settings > details and config your default apps

you can always search with terminal

locate what_so_ever_app | grep bin

you'll get a list of paths to choosen app

---

### Post by deadflowr on 2013-12-17
> **rajpier said:**
> Well it's complicated. I need to be able to click on the file location. My stock  market site has a streaming quote ap that use Java jnlp , whatever that is. I use Chrome for places where I must use Java because I have figured out how to select sites to allow it. For whatever reason when I click on this jnlp file it asks to open it with Firefox or Other,, even though I have Chrome as my default browser.  The thing is I can't find the location of the Chrome program files.

Well I found it there but it doesn't work.

Right click on the file and go to properties
and go to the tab "open with"
Then see if chrome is listed in other applications.
Older version will have a button marked something like "other applications"
Once you've set chrome, that file type will always open with chrome.

---

