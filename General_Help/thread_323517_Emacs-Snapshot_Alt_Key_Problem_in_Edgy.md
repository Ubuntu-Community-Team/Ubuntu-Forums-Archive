---
title: "Emacs-Snapshot Alt Key Problem in Edgy"
date: 2006-12-22
forum: General Help
---

### Post by scojo on 2006-12-22
My right alt key is not responsive in edgy emacs-snapshot (emacs 22.0.50.1).  This is emacs using X.  I never had this problem in Dapper using (I think) the same emacs-snapshot.  My suspicion is that there's some kind of problem between emacs and X window.  I posted this issue to the ubuntu-users mailing list w/ no response.

Anbody have this issue and get it fixed?  It's kind of annoying because the right Alt key is convenient for M-x commands.  Thanks in advance for any help offered.

update===================

xev shows the following for the right alt key...

KeyPress event, serial 29, synthetic NO, window 0x3200001,
    root 0x4d, subw 0x0, time 2996778565, (342,159), root:(354,258),
    state 0x0, keycode 113 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x3200001,
    root 0x4d, subw 0x0, time 2996778673, (342,159), root:(354,258),
    state 0x80, keycode 113 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

---

### Post by scojo on 2006-12-26
With help from Stephen Ryan in the ubuntu-users mailing list.  The solution was go to System -> Preferences -> Keyboard -> Layout Options -> Third Level Choosers and uncheck the "right alt key to choose 3rd level" preselect.  Now the right alt key works like a charm!

---

### Post by jgubes on 2006-12-30
That works great for gnome...anybody solve this problem for kde?

---

### Post by gordonsowner on 2007-09-12
Hi!

I had a similar post here a while ago [here,]("http://ubuntuforums.org/showthread.php?t=366556") and it broke again.  Searching the forum led me here to a solution.  Don't know if you can make favorite posts for reference, so I am posting with a 'it worked for me' so i can at least look at my posts to revisit this if i forget what happened.

---

