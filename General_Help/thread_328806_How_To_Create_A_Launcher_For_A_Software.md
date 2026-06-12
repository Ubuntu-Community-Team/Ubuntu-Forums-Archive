---
title: "How To Create A Launcher For A Software"
date: 2006-12-31
forum: General Help
---

### Post by moricgaut on 2006-12-31
I installed emesene the new version that i got from the site. it is located in /usr/share/emesene
. The file that excutes is named this emesene. I would like to create a laucher on my desktop i've tried by going right click launcher but whatever i'm doing isn't right because when i click on the laucher it doesn't open anything up but if i click on the file in the folder /usr/share/emesene it will work. I'm not sure exaclty what to write in the command and what to chose as application etc. can someone please help to set up a launcher for this program

---

### Post by an.echte.trilingue on 2006-12-31
/usr/share is not in your usual path.  The best way around this is to simply put the absolute path to the executable in the "command" box when creating a launcher, ie "/usr/share/emesene/executable".

Take care
-mat

---

### Post by moricgaut on 2006-12-31
I tried what you told me to do and it didn't work. It gave me an error.

---

### Post by Raptor45 on 2006-12-31
Just to make sure, you didn't actually do "/usr/share/emesene/**executable**"... right?

The word "executable" should be replaced with whatever the name of executable for the program is.

---

### Post by moricgaut on 2006-12-31
I wrote this in the command box /usr/share/emesene/emesene
emesene is the excutable when i go in that folder and click it it opens the software.

---

### Post by moricgaut on 2006-12-31
when i put that in the command box nothing happens when i click on the laucher.

---

### Post by an.echte.trilingue on 2006-12-31
Just out of curiousity, what is the output of 
```
ls -l /usr/share/emenese/
```
?


Also, what was the error message you got?

-mat

---

