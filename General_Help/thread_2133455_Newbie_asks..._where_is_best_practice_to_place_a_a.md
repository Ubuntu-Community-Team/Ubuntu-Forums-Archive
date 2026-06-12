---
title: "Newbie asks... where is best practice to place a app?"
date: 2013-04-08
forum: General Help
---

### Post by YannosB on 2013-04-08
I have an app that is not 'install' motivated...(a archived folder structure), my question is... where should I put this, in light of 'best practices'?

On 12.04 precise...

thanks for any replies.

---

### Post by ajgreeny on 2013-04-08
I don't understand your question.

Is this application supplied as, for example, a .tar.gz archive that you now want to install, or is it more like the Firefox archive that you can download from mozilla, extract and then simply run the firefox executable file from the archive.

Tell us more and we may be able to help you further.

---

### Post by YannosB on 2013-04-08
"...(a archived folder structure)..." should have been pretty clear....
 so, uh yup.... the app is archived, instructins are to unarch it and run....
 I'm unsure of where apps should or should not be placed so I am waiting
to learn where to put it so I do not 'mess' things up... pretty simple I know, but hey gotta start somewhere.
Yannos

---

### Post by ajgreeny on 2013-04-08
If the extracted archive is sitting in your /home at present, there is no need to move it; just run the executable file in the archive from there. it really does not matter where it is.

---

### Post by cbraxton on 2013-04-08
Usually stuff you install manually would go into /usr/local. For user-oriented applications use /usr/local/bin, for system utilities /usr/local/sbin. (Most of the stuff that comes in tarballs defaults to this.)

---

### Post by 3rdalbum on 2013-04-08
> **ajgreeny said:**
> If the extracted archive is sitting in your /home at present, there is no need to move it; just run the executable file in the archive from there. it really does not matter where it is.

I posted in your other thread as well, but the above advice is exactly correct.

---

### Post by YannosB on 2013-04-08
Yes, thanks all.

 I had read in a sticky... that I should mark this as 'solved' via the thread tools in upper r-corner... but there is no such option in that drop down.

I'd mark it solved... if I could find it.....

again thanks..

Yannos

---

### Post by Bucky Ball on 2013-04-08
That function is currently broken after a forum upgrade. Use this workaround;

Edit first post
Click 'Go Advanced'
Change the prefix [ubuntu] to [Solved]

Thanks.

---

