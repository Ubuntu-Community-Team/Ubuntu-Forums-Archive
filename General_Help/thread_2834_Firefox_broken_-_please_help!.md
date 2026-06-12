---
title: "Firefox broken - please help!"
date: 2004-11-01
forum: General Help
---

### Post by noelferg on 2004-11-01
After trying to upgrade firefox to 1.0 (D'oh I did it through  irefox itself.) it would not run.

I have upgraded back to 0.99 Ubuntu, uninstalled, re-installed, done a complete un-install (all using Synaptic) & still no joy. 

I get this error message when I click the Firefox icon:

> XML Parsing Error: undefined entity
Location: chrome://browser/content/browser.xul
Line Number 19, Column 1:

<window id="main-window"
^

  ](*,)

Any help greatly appreciated

---

### Post by plasmo on 2004-11-01
[QUOTE=noelferg]After trying to upgrade firefox to 1.0 (D'oh I did it through  irefox itself.) it would not run.

I have upgraded back to 0.99 Ubuntu, uninstalled, re-installed, done a complete un-install (all using Synaptic) & still no joy. 

I get this error message when I click the Firefox icon:



  ](*,)

Any help greatly appreciated[/QUOTE]
 just a guess. lol
try rename /usr/lib/mozilla-firefox to something like /usr/lib/mozilla-firefox1
and reinstall

---

### Post by noelferg on 2004-11-01
Thanks plasmo

But still get same error message (still won't start from icon)

It will at least now start if I use sudo. Although that still throws this:
> 
Error: No running window found
auto selected locale: en-US

 :confused:

---

### Post by ynef on 2004-11-01
My hunch tells me that what's fucked up is that your profile was converted by 1.0 from its 0.9.x format and is now broken. Either the profile itself or just the extensions you possibly had installed. Try renaming the .mozilla folder in your home directory by starting a new terminal and issuing this command:

mv .mozilla .mozilla-old

Now run firefox again and it will make a new profile for you.

Exit firefox and overwrite the new bookmarks.html file in your profile directory with the old one.

Now all you need to do is put all your extensions back.

---

### Post by noelferg on 2004-11-01
Thanks ynef

Problem solved

---

