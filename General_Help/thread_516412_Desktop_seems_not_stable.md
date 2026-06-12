---
title: "Desktop seems not stable"
date: 2007-08-03
forum: General Help
---

### Post by satimis on 2007-08-03
Hi folks,

Ubuntu 7.04 desktop
Gnome desktop

1)
Acrobat Reader fails to start on menu.  Clicking

Application -> Office -> Acrobat Reader

w/o response.

It can be started on Terminal by typing "acroread" w/o problem


2) 
Application -> System Tools -> Automatix

It starts and crashes finally.

Re-clicking it saying it is running.


3)
Firefox crashes occasionally on visiting some websites.


These only happens recently.  Please advise where shall i check for their causes.  TIA


B.R.
satimis

---

### Post by mcduck on 2007-08-03
> **satimis said:**
> Hi folks,

Ubuntu 7.04 desktop
Gnome desktop

1)
Acrobat Reader fails to start on menu.  Clicking

Application -> Office -> Acrobat Reader

w/o response.

It can be started on Terminal by typing "acroread" w/o problem


2) 
Application -> System Tools -> Automatix

It starts and crashes finally.

Re-clicking it saying it is running.


3)
Firefox crashes occasionally on visiting some websites.


These only happens recently.  Please advise where shall i check for their causes.  TIA


B.R.
satimis

1. USe Evince, the native Linux reader for PDF and PS files. It's already installed and works much better than Acroread does on any platform. If you really must use Acroread for some reason, check if the launcher in the menu is pointing to right file.

2. Use Ubuntu's own package management. You don't really need Automatix for anything, and it's known to have some problems.

3. Try disabling Java, JavaScript or Flash to find out if they are causing the problem on those sites. Remove all extensions you don't asolutely need.

---

### Post by satimis on 2007-08-03
Hi mcduck,

> 
]1. USe Evince, the native Linux reader for PDF and PS files. It's already installed and works much better than Acroread does on any platform. If you really must use Acroread for some reason, check if the launcher in the menu is pointing to right file.

I have Evince and Xpdf f
running on this box.  But I still need Acrobat Reader.  It has more features.

$ ls -al /usr/bin/acroread```
 
lrwxrwxrwx 1 root root 40 2007-07-09 13:11 /usr/bin/acroread -> /usr/local/Adobe/Acrobat7.0/bin/acroread

```
Previous it worked on the menu.  It can't be started on menu now and I don't know the cause.  However it still can be started on Terminal.  The properties of its icon are correct.


> 
2. Use Ubuntu's own package management. You don't really need Automatix for anything, and it's known to have some problems.

Same situation as Acrobat Reader.  But it still can be started on Terminal w/o problem.


> 
3. Try disabling Java, JavaScript or Flash to find out if they are causing the problem on those sites. Remove all extensions you don't asolutely need.
After disenabling JavaScript and Java on Content of Preference, the problme gone.  But the webpages can't be displayed correctly.  Those sites need MS Java and MS VM.  


satimis

---

### Post by mcduck on 2007-08-03
> **satimis said:**
> 
After disenabling JavaScript and Java on Content of Preference, the problme gone.  But the webpages can't be displayed correctly.  Those sites need MS Java and MS VM.  

The problem could be that they use MS Java instead of the standard Sun Java. Microsoft isn't really known for working well with standards other than their own..

But if you can give me a link to one of the sites that crashes your Firefox I can try if it does the same for me as well.

I don't know how to solve the problem with Acroread, but I remember seeing some threads about same kind of problems before. Have you tried searching old forum threads?

---

### Post by Seisen on 2007-08-03
The best way to see what is causing the problem in Firefox is to start it in safe-mode and see if it crashes. If it doesn't enable one extension at a time until it crashes again if it does. Sometimes when firefox crashes its due to the extensions.

---

### Post by stchman on 2007-08-03
> **satimis said:**
> Hi folks,

Ubuntu 7.04 desktop
Gnome desktop

1)
Acrobat Reader fails to start on menu.  Clicking

Application -> Office -> Acrobat Reader

w/o response.

It can be started on Terminal by typing "acroread" w/o problem


2) 
Application -> System Tools -> Automatix

It starts and crashes finally.

Re-clicking it saying it is running.


3)
Firefox crashes occasionally on visiting some websites.


These only happens recently.  Please advise where shall i check for their causes.  TIA


B.R.
satimis

1.  Uninstall Acrobat reader and install the one from Medibuntu.

[http://www.stchman.com/install_adobe.html](http://www.stchman.com/install_adobe.html)

2.  Automatix is problematic for a lot of people.  I recommend not using it.

3.  Are the websites using Flash like Youtube?  If so, follow this:

[http://www.stchman.com/flash_firefox.html](http://www.stchman.com/flash_firefox.html)

Hope this helps.

---

### Post by satimis on 2007-08-03
Hi folks,


Tks for your advice.


I think my problems are largely caused by my recenlty playing around on browsers, making them, Firefox/Opera/IEs4Linux, identifying as IE and upgrade 'wine' on repo.

1)
Previously Acrobat Reader and Automatix can start on menu w/o problem.  The former was installed on repo.  I can't recall exactly the later.  However both of them worked w/o problem.  After downgrading 'wine' to previously version and removing its latest trouble version, Automatix can start on menu leaving on Acrobat Reader still in problem.


2)
If disable Java/Javascript on Firefox, visiting those public sites won't crash but the webpages can't be displayed correctly, some icon/logo/link missing.

Some sites require MS VM


satimis

---

