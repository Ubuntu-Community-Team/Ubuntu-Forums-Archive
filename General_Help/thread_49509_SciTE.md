---
title: "SciTE"
date: 2005-07-16
forum: General Help
---

### Post by Billybob on 2005-07-16
I want to use SciTE, I installed it, but it isn't working correctly. First off there's two differrent entries for it in the applications menu. One starts SciTE and the other doesn't. Says "no file or directory." And besides that when I try to open a document using SciTE from the file browser it never works. The file comes up blank.

---

### Post by hetodd on 2005-08-11
I get the same thing.

I went to /usr/share/applications/ and found scite.desktop and SciTE.desktop.  The files were a little different.

Using sudo I renamed SciTE.desktop to SciTE.desktop.bad and that got rid of the SciTE entry in Applications|Other (actually it got rid of Applications|Other all together on my machine ;)

This entry generated the error.

Now I've edited my /usr/share/scite/SciTEGlobal.properties file to enable full path on the title bar.  In this mode when I open a file using double-click in nautilus OR right click "Open with...", it opens a blank file at:
     
    /home/htodd/file:/home/htodd/filename.txt

Note how "home" is prepended to the path.  I don't know if nautilus is doing this or SciTE.

It works fine from within SciTE (File|Open).

Any help would be appreciated

Thanks
Herb

---

### Post by charlieg on 2005-08-11
**hetodd:** You should probably post those changes as patches or at least post a bug on bugzilla.ubuntu.com

---

