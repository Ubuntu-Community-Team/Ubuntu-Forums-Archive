---
title: "Weird display issues with Live CD 12.04"
date: 2013-12-11
forum: General Help
---

### Post by goemonburo on 2013-12-11
I just downloaded a Live CD of Ubuntu, 12.04, the one that's supposed to last until 2017.  It boots fine, I see a maroon screen, but the moment I click the mouse or try to do anything the screen goes totally psychedelic: bizarre colors, flashing squares, odd stripes.  Cntl-Alt-Delete brings up a window that has the buttons not visible because they are pushed off below the bottom of the screen and I can seem to resize the window to make them visible...but hitting Enter brings me to a very stable maroon login screen.  Since it's a Live CD I haven't created any user account and can't log in.  But everything works fine, no visual weirdness at all.  (Except the "Shutdown" or "Restart" button doesn't seem to do anything.)

None of this is inspiring confidence...but the fact that I can arrive at a stable screen eventually gives me some hope.  Does anyone know what's causing this, what I might do to fix it, or what options I have?  I am a bit scared to do an actual install before I've played around and know Ubuntu's right for me...but I can't seem to get any kind of usable screen until I'm in that login window.

I'm using a fairly old Dell Inspiron 531 desktop.  Could this be a graphics card issue?  

Any ideas or help would be great.  Thank you!

---

### Post by sammiev on 2013-12-11
Go into boot options and select Nomodeset.

---

### Post by goemonburo on 2013-12-11
Okay, great.  I'll try that!!  Thank you!  :-)

---

### Post by mörgæs on 2013-12-11
Nomodeset is a classical solution for Nvidia screen cards, so the first question would logically be: Which card do you have?

---

