---
title: "Which music player provides &quot;Enque&quot; on right-click context menu?"
date: 2012-12-21
forum: General Help
---

### Post by Holmes.Sherlock on 2012-12-21
Presently I am using Rhythmbox and VLC to play songs. Both of them require songs to be browsed and added to the queue. Is there amy player which provides this option on the song files right-click context menu?

---

### Post by Rexilion on 2012-12-21
Qmmp provides this functionality as a seperate .desktop. I can confirm this on Gentoo, so Ubuntu should have this as well.

---

### Post by mc4man on 2012-12-21
smplayer has a built-in, though it shows in the 'open with' context menu
plus possibly smplayer only has a detached playlist?

vlc has an enqueue option for d. left click if mimetype is set with vlc as default.

Any player that has commands for such can be set in nautilus-actions, audacious works quite well.
The are 3 common command sets for audacious - show all 3 here in post 8, tool tips describe.
[http://ubuntuforums.org/showpost.php?p=5287811&postcount=8](http://ubuntuforums.org/showpost.php?p=5287811&postcount=8)

That post is 4 years old so while the options remain nautilus-actions has changed a bit.
Screens 1 thru 3 show the 3rd option from above post (queue in aud, - adds to current playlist), as done in current n-a
screen 4 shows ex.
 
There is this set of nautilus python-extensions that includes an enqueue in audacious it may be  more like 1st. option in above link - (new in aud, adds to a temp playlist
Anyway it's a little aged & may need some editing to work in 12.04 or 12.10 (never tried, use 13.04 here where it doesn't work at all
[http://www.giuspen.com/nautilus-pyextensions/](http://www.giuspen.com/nautilus-pyextensions/)

---

### Post by Rexilion on 2012-12-22
Yes, mc4man has good examples. You can also create your own. Some multimedia players provide the functionality, but don't provide this on every DE through .desktop files or right click menu actions (which are also standardised menu files).

---

### Post by Holmes.Sherlock on 2012-12-22
> **mc4man said:**
> 
vlc has an enqueue option for d. left click if mimetype is set with vlc as default.[]("http://www.giuspen.com/nautilus-pyextensions/")
I can't find such option with VLC even after I set it as the default app for a specific file type.

---

### Post by Holmes.Sherlock on 2012-12-22
With VLC 2.0.3, it's damn easy.

Check both Tools-->Preferences-->Interface-->Allow only one instance & Enque file when in one instance mode.

---

