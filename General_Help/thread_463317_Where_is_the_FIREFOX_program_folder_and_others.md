---
title: "Where is the FIREFOX program folder and others?"
date: 2007-06-03
forum: General Help
---

### Post by fatray on 2007-06-03
I downloaded AM-Deadlink and want to download load all the icons for the bookmarks.  The program needs to know where the Firefox Bookmark.html file is and I can't find out how to find it.  Windows is so easy, just right click on the shortcut and select "Open Program Folder", or something like that.  I've been searching for an hour now and have given up.  Where is the "Program Files" folder?  The only Bookmark.html file I found is the default bookmarks when you first install Firefox.

I would really like to get the hang of this but don't know where stuff is.  I assume in Linux everything is called something different, so what I need to know is; What folders in Linux would be it's comparison to Windows?  I've been a Windows user forever:-k

Windows             Linux

Program Files       ??????
Windows             ?????
My Documents     ??????
ect......

---

### Post by pseudonym on 2007-06-03
All your Firefox settings (and most other program settings) are contained in hidden folders in your /home directory (similar to ...Documents and Settings\Application Data in Windows) . All hidden directories begin with a '.' . To view them you just need to set your file manager to 'View Hidden Files' (or similar), which should be under the 'View' menu at the top.

HTH

---

### Post by JulianRoot on 2007-06-03
Linux/Ubuntu is a completly different operating system than Windows (see [this]("http://linux.oneandoneis2.org/LNW.htm")).
The global configuration data is in /etc. Your personal settings are in your /home directory, e.g. /home/foobar or ~.
You save your files in your /home, too.

---

### Post by fatray on 2007-06-03
Well I found this **ect/firefox/profile**, but that still isn't it.

---

### Post by JulianRoot on 2007-06-03
It's /home/<user>/.mozilla/firefox/<profile name>
(You can't see .mozilla by default, so you must display hidden files)

---

### Post by American_Outcast on 2007-06-03
This is where I found mine,

I opened the home folder. Then I clicked on view, then clicked on "view hidden files"
the complete path is,

/home/<user>/.mozilla/firefox/ubuntuce.default

or if you already have the home folder open its just

.mozilla/firefox/ubuntuce.default


Edit: I am using Ubuntu 7.04

---

### Post by fatray on 2007-06-03
Excellent found it.  I didn't know how to show hidden files, thanks.

---

### Post by JulianRoot on 2007-06-03
I have got only a german version of Ubuntu, so I cant tell you the name in the english version ;) sorry

---

### Post by strabes on 2007-06-03
by the way, you can abbreviate "/home/username" with "~" so it could be "~/.mozilla/firefox"

---

### Post by JulianRoot on 2007-06-03
> **JulianRoot said:**
> [...] e.g. /home/foobar or ~.[...]
Is this a "~"?
Yes, isn't it?

---

### Post by fatray on 2007-06-06
thanks guys :p, I like the ~ it will save some typing.

---

