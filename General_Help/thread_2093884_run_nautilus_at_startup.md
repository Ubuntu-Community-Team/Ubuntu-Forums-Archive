---
title: "run nautilus at startup"
date: 2012-12-12
forum: General Help
---

### Post by ororo on 2012-12-12
I am using gnome-session-properties to launch a number of applications at startup.

Now, I cannot open a Nautilus window.

I have tried "nautilus", "nautilus -n", "nautilus --no-desktop" (as in attachment) but none of them works.

Ideas? Thank you.

---

### Post by CaptainMark on 2012-12-12
firstly try to add where you would like nautilus to open, so "nautilus /home/mark" to be honest I don't expect this to work but its worth a shot, I've had problems in the past where using startup applications to open certain programs will fail because the applications not ready to be opened yet,it shouldn't happen but it does, if this is the case make a short bash script (post back if you need help with this) that sleeps for say 10 seconds and opens nautilus, then add the script to startup applications instead, works for me

---

### Post by ororo on 2012-12-12
> **CaptainMark said:**
> firstly try to add where you would like nautilus to open, so "nautilus /home/mark"

great! It works! Thank you.

---

### Post by dcstar on 2012-12-13
> **ororo said:**
> great! It works! Thank you.

Then MARK the thread.

---

