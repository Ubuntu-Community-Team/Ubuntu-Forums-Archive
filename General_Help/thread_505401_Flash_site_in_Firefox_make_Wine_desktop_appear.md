---
title: "Flash site in Firefox make Wine desktop appear"
date: 2007-07-20
forum: General Help
---

### Post by Sciamano on 2007-07-20
Hi everyone.
I'm using Feisty and Firefox and everything was fine until a couple of days ago.
Now, when I open a flash site, a Wine Desktop appears!
I can't understand why,  but it prevents the use of Firefox unless I close it (and keeping it open is useless because nothing gets loaded in wine anyway).
Anyone has an idea about what happened? How can I try to solve?
Thanks, ciao!

---

### Post by ddrichardson on 2007-07-20
Check the file type associations in Firefox first (Edit/Preferences/File Types/Manage), to see if the flash mime type is allocated to wine.

Is this any flash site or one specific site?

---

### Post by Sciamano on 2007-07-20
Hi ddricharsdon, thanks for your suggestion.
Shockwave Flash files (SWF) are correctly allocated to Shockwave Flash plugin.
Which is pretty logic considering that the flash sites are correctly displayed by Firefox, although interacting with them is quite impossible.
It happens with almost every flash site (YouTube, for example, or [www.simpsonizeme.com](www.simpsonizeme.com), where the site works, but if I try to upload a picture, the wine desktop shows up!)
:(

---

### Post by ddrichardson on 2007-07-20
Well I'm stumped :-), Was worried if it had been a single site that it was a security issue. Will hunt around and see what pops up.

---

### Post by Sciamano on 2007-07-20
I google for information about this but found nothing.
I might try to reinstall flash to see what happens.

Edit: it did not work. Wine desktop still shows up

---

### Post by ddrichardson on 2007-07-20
I'm wondering if this is something to do with the flashsupport abstraction layer.

---

### Post by Sciamano on 2007-07-20
I have no idea.
This is also strange: running firefox via terminal gives this output:

```

** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Error with bookmark
TypeError: bkmk has no properties
Title: Search Engine Directory
URL: http://www.dnc.net/users/king/search.htm
Labels: Utilita' generale>Online services>Search Engines
ID: 201702545362372261
Date: Mon Jun 04 2007 08:58:23 GMT+0200 (CEST)
```

I checked the labels and in Utilita' generale>Online services>Search Engines I had that bookmark.
I've deleted it now, but still this output comes up when I launch firefox... :-/

---

### Post by ddrichardson on 2007-07-20
Further research into Wine makes it appear as though this is related to how the Wine API works rather than how Firefox handles mime types.

Has Wine recently been updated?

---

### Post by Sciamano on 2007-07-20
Well, a new version of Wine is released every two weeks, so yes. It might be a week or so since the latest version was released.
But I have the same version of Wine both on my desktop PC and on my laptop, and this "bug" only occurs on the laptop. I would guess that it would happen on both, should the problem be Wine. 
Am I wrong?

---

### Post by ddrichardson on 2007-07-20
No that makes sense (if they're both auto updating). But something must have changed.

Just for diagnostic purposes, backup the .mozilla directory then delete it or rename it, reload firefox and see if the error still occurs. Or try running it from a different account on the same machine.

---

### Post by bijwaard on 2008-04-30
This issue seems to be due to the Flashgot add-on, I noticed it first today with ubuntu hardy and firefox3-beta5. For some reason Flashgot wants to run Flashgot.exe from the .mozilla/firefox/...default folder. Don't understand why this addon doesn't use a linux native executable or something java. This executable is restored from a jar file when it is removed...

Kind regards,
             Dennis

---

### Post by Sciamano on 2008-04-30
I forgot about this issue, and in the end I did not post how I solved.
In my case, I had made a script file to launch Photoshop, which I called "ps". It must have been a bad filename choice, since this "command" was launched by firefox when it encountered a flash site.
Renaming the "ps" script to another name solved the problem for me.

---

### Post by smartoos on 2008-05-07
You have to disable the automatic detection of the download manager in the FlashGot addin. The Wine desktop will no longer appear. This worked for me on openSUSE 10.3 x86 and Firefox 2.0.0.14.

---

