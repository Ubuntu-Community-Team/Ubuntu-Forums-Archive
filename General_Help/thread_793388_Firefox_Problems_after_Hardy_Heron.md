---
title: "Firefox Problems after Hardy Heron"
date: 2008-05-13
forum: General Help
---

### Post by Beloch on 2008-05-13
I am experiencing some strangeness with Firefox 3 beta 5 under Hardy Heron.  It appears to have no file associations whatsoever.  i.e. If I go into Edit/Preferences/Applications, there are no entries at all.  If I try to open files, such as pdf's, it offers to open them with firefox, which obviously fails.  I could manually set up associations for everything, but I'd rather not.  Other than not knowing it's buttocks from it's nose in terms of how to open files, Firefox 3 seems to work like a champ.

---

### Post by joshsmith on 2008-05-14
deleting your old ~/.mozilla directory and making a new profile would probably give you an instant fix,  with the small inconvenience of having to re set you home page etc

---

### Post by Beloch on 2008-05-14
Thanks for your reply joshsmith.  This actually occurred both after doing an upgrade to Hardy and after doing a completely fresh install of Hardy, so the old .mozilla directory could only have been a problem when I upgraded.  Since I hadn't really done much with the fresh install yet, I thought I'd try deleting the .mozilla directory anyways.  That  didn't help, although I've noticed some other things about the weird behavior since my last post.  The Preferences/Applications list is still empty.  Let me map out exactly what happens if I try to open a pdf.  

1. Deleted .mozilla  directory (rm -Rf ~/.mozilla)
2. Tried to open a link to a PDF file.  (I also tried postscript files.)
3. "Open With" field was initially blank and Save File was selected by default.  I clicked on the radio button next to "Open With", clicked OK, and got the following message:  

```
"The application you chose ("(null)") could not be found.  Check the file name or choose another application."
```

4. Tried to open the same link to a PDF file again.  Again, the "open with" field was blank and save was the default.  I chose save.
5. Tried to open the same link to a PDF file a third time.  This time, the "open with" field was "firefox-3.0b5".  I then selected the "open with" radio button,  hit OK, and got the following error message:

```
/tmp/0502021.pdf could not be opened, because an unknown error occurred.

Try saving to disk first and then opening the file.
```

6. Tried to open the same link to a PDF a fourth time.  This time I clicked on the down arrow of the "Open with" listbox and chose "Other".  Then, on the file chooser that popped I did nothing other than to hit cancel.  The correct application for opening the file (e.g kpdf) was then in the "open with" box.  I clicked OK and it opened successfully!  

Note that after step 5, the default "open with" value will always be "firefox-3.0b5" unless I delete the .mozilla directory.  Step 6 can be performed at any time in this sequence and allow the file to be opened, but the correct application will not be stored as the default.  The box will revert to blank or "firefox-3.0b5" the next time I try to open a file.


I also tried this with postscript files, and again a different but proper application was chosen automatically the same as in step 6.  

Basically, this looks like a firefox bug to me.  Given that this happens on a fresh install of Hardy, I'd be surprised if this wasn't happening to other people.  Am I in the right forum for this kind of bug?

---

### Post by mordanda on 2008-05-15
I also have this issue in 8.04 Kubuntu.  Deleting the local mozilla directory also does not fix.  I too would be curious as to what the fix might be.

Dan

---

### Post by mordanda on 2008-05-15
I found this bug in launchpad which reports the issue.

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/220798/](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/220798/)

The triage is to install firefox-gnome-support while they work on a KDE fix.

I can verify this works.  Hope this helps out.

Dan

---

### Post by mgazb on 2008-05-15
I have found that I have lost all my bookmarks as part of the upgrade. Also the new version of Firefox doesn't maintain any history - very annoying when trying to search for fixes as I have to remember to copy the new address into a different tab to avoid having to repeat the search.

When I first upgraded 7.10 to 8.04 it seemed to work fine . 

When I logged out, I was asked whether I wanted to save the current tabs.

When I logged in again, and started Firefox, I was initially presented with the "Firefox is already running" dialogue. 

I deleted the .mozilla/firefoz/<profile>/lock and .parentlock files and then I was presented with a blank page and none of my bookmarks were remembered.

If I click home, I was taken to google, which is not my home page.

If I look at Edit|Preferences, my old homepage is listed on the Main tab.

I've tried restoring the bookmarks using Bookmarks|Organise Bookmarks and although there are backups for the last week, and they seem to contain what I remember of the old bookmarks, I can't read them into Firefox.

How can I get my old settings back?

thanks

dan

---

### Post by Beloch on 2008-05-15
> **mordanda said:**
> I found this bug in launchpad which reports the issue.

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/220798/](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/220798/)

The triage is to install firefox-gnome-support while they work on a KDE fix.

I can verify this works.  Hope this helps out.

Dan


Thanks for your reply mordanda.  I'm glad that the Mozilla people are aware of this problem even if they don't seem to be anywhere near fixing it.  The "triage" suggested in that thread does not work for me, so perhaps I will go back to Firefox 2 until they get their act together.

---

