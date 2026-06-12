---
title: "desktop disappeared and nuatilus not working"
date: 2007-02-20
forum: General Help
---

### Post by Jason Weiss on 2007-02-20
Hi Guys and Gals 

This is weird, I know that my HDD is a bit full, very full. 

why I came to my computer this afternoon my desktop icons...gone   My wall paper......gone

I tried to open my home directory......not working i tried opening nautilus from terminal......nothing

Everything else ie firefox and application........working perfectly

I have tried a cntrl + alt + backspace no improvement. 

any ideas?

---

### Post by Jason Weiss on 2007-02-20
please help 
I know someone has the answer

---

### Post by David Marrs on 2007-02-20
All those things you mention are run by nautilus, so it must have crashed. Are you saying that nautilus doesn't run every time you log in or is this just a one off? Either way, if your hdd is very full then freeing up some space would be a good first step. If you can't browse your files anymore, you'll  have to open a terminal and use shell commands to copy (cp), move (mv) or remove (rm) files.

If it crashes again the best thing to do is make a note of what happened, find any error messages generated and contribute a bug report to launch pad. Best to search launch pad first to check if the bug has already been reported by someone else and contribute to that rather than duplicate it.

---

### Post by cdrappier on 2007-09-10
I'm having the same problem

---

### Post by cdrappier on 2007-09-10
I fixed it, this is what i did: ```

sudo apt-get install nautilus desktop-base nautilus-cd-burner gnome-app-install
```
nautilus-cd-burner is of course, optional.  hope this works for you!

---

