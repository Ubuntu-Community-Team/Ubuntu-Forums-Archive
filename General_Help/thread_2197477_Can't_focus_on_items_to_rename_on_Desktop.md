---
title: "Can't focus on items to rename on Desktop"
date: 2014-01-03
forum: General Help
---

### Post by jamesisin on 2014-01-03
I don't seem to be able to focus on desktop items when I am attempting to rename them.  Let me explain.

Say you have a file on the Desktop called file.txt and you'd like to rename it something like myfile instead.  So you right-click on it there on your Desktop and choose Rename.  The text (though not the extension) becomes highlighted and you attempt to type something.

However, in my case the text is highlighted gray (not orange) suggesting focus is elsewhere.  I am not able to type or delete any of that text.  This occurs if there are any windows on that workspace which might take focus.  An empty workspace will present me with orange highlighted and manipulable text.

I can work around this by either attempting to change the name on an empty workspace or by opening the Desktop folder itself and making the change within that window.

Initially I suspected Unity Tweek's mouse focus might be to blame, but I can change it back to Click (the usual Ubuntu behavior) or any of the other two (Sloppy or Mouse) and the problem remains.

Any suggestions?

---

### Post by efflandt on 2014-01-04
Are you still running 10.04 (per your profile) or some other Ubuntu version? I am not familiar with Unity Tweek, but 10.04 did not use Unity. I cannot produce the behaviour you describe in 10.04 (where highlight is always gray, but works) or 12.04 (where it is always orange and works) regardless of whether other windows are open or not. Both are the usual click to focus.

---

### Post by coldraven on 2014-01-04
I usually just press F2 to rename a file.

---

### Post by jamesisin on 2014-01-05
efflandt - The system in question is running 13.10 but this may have been happening on other Unity/Ubuntu versions.  (No, 10.04 does not have Unity.)

coldraven - Not sure how to use F2 to change a file name.

---

### Post by jamesisin on 2014-01-05
After some testing, F2 only works within folders and not on the Desktop itself.  (If you are in the Desktop folder, of course, F2 will work.)  I'm not clear if that is by design or as a result of the same thing which is preventing focus.  Regardless, using F2 merely does what I can already do which is highlight the file name for renaming (by right-clicking).  It would be the typing after said highlighting I cannot do.

---

### Post by mc4man on 2014-01-05
What version of nautilus do you have, should be at least 1:3.8.2-0ubuntu2.1
If you log in to a guest session can you rename a file on the Desktop?

---

### Post by jamesisin on 2014-01-05
Here is Nautilus:

```
nautilus --version
GNOME nautilus 3.8.2
```

I have guest sessions disabled.  I could log in as a different user if you'd like?

---

### Post by mc4man on 2014-01-05
First try upgrading nautilus, current is 3.8.2-0ubuntu2.1 from -updates. 3.8.2-0ubuntu2.2 is available from -proposed & would be fine to upgrade to if desired.
After upgrade kill nautilus (nautilus -q), the restart by clicking on Files in launcher or any other means of your choice.

---

### Post by jamesisin on 2014-01-05
I have enabled the Proposed repo and upgraded the three Nautilus items (and rebooted).  No change in behavior.

---

### Post by mc4man on 2014-01-05
> **jamesisin said:**
> I have enabled the Proposed repo and upgraded the three Nautilus items (and rebooted).  No change in behavior.
Then maybe try in a guest session or tmp create a new user, log out/in to  & try there.
If it works in the guest/new user session then it's some local config to your user, if it doesn't then some system wide issue.

The nautilus upgrade fixed in issue in 13.10 where renames on the Desktop presented a rename widget where the  background was transparent where it may  be impossible to see what one was typing. ( though blindly typing was possible

apparently you have some other issue..

---

### Post by jamesisin on 2014-01-05
Ok, so I did some more testing.  Looks like my initial intuition that it was due to mouse-captured focus was correct.  I had to reboot after changing back to Click (log out/in may have done it as well).  Originally I just tested by switching without a reboot.  Both Sloppy and Mouse cause this focus issue.

Shall I file a bug report?  With whom?

Nonetheless, if anyone has a fix...

---

### Post by mc4man on 2014-01-05
> **jamesisin said:**
> Ok, so I did some more testing.  Looks like my initial intuition that it was due to mouse-captured focus was correct.  I had to reboot after changing back to Click (log out/in may have done it as well).  Originally I just tested by switching without a reboot.  Both Sloppy and Mouse cause this focus issue.

Shall I file a bug report?  With whom?
.
If you're using a ubuntu session (unity/compiz) then I'd start with a bug on compiz.
Have you tried any other sessions to see if it occurs there? (gnome/gnome-shell or gnome-flashback (metacity)

Edit: at least here in an ubuntu session 'click' is always set on login, if changed it always reverts back on either log out or in

---

### Post by mc4man on 2014-01-05
Now I see what you mean - 
trying 'sloppy', the Desktop can't receive focus so obviously rename won't work *if* there are any windows open while trying to rename something on the Desktop
I'll assume 'mouse' is the same

If **no windows are open** then renaming a file on the Desktop works fine here..

---

### Post by jamesisin on 2014-01-05
Exactly.

---

### Post by mc4man on 2014-01-05
It's almost assured this is already a reported bug & I'd say the likelihood of being fixed in 14.04 are slim to none.

Probably an offshoot of Gnome dropping support for the Desktop which Ubuntu has re-enabled to the extent that an ubuntu session needs.
Apparently  the only way to move/have focus to the Desktop is to either click on or have nothing open on  so hence your issues with other mouse/cursor modes

---

### Post by jamesisin on 2014-01-05
Can you link me to something which discusses "Gnome dropping support for the Desktop"?  I would like to learn more.

---

