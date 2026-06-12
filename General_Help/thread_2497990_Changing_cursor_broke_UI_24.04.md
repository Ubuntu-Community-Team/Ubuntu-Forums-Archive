---
title: "Changing cursor broke UI 24.04"
date: 2024-05-25
forum: General Help
---

### Post by CaptSammy on 2024-05-25
I made one change to the cursor, changed from Yaru to the one above, Hand hold I think.

It broke the UI. Clearing the entire screen with an error "oops something went wrong" or something similar, with a button to log out.

Now I can authentic and get in, but it immediately gives me the OOPS screen with the log out button.

Is there a way to reset to Yaru maybe from command line?

Is my UI affectingly bricked?

---

### Post by Dennis N on 2024-05-25
I had the same thing happen. I made This note in my log:
> "Apr 18, 2024 - DMZ White cursor crashed the system using Xorg right after selection, even though this is one of the default cursors. This cursor was OK in Wayland."
I probably logged into the Wayland session and changed to a different cursor there.

I understand cursor themes now should define a "default" cursor. Not having one was probably the cause.

---

### Post by CaptSammy on 2024-05-25
What is the best way to fix the issue? Did you log in without UI and use a command line solution?

---

### Post by CaptSammy on 2024-05-25
Found a solution

gsettings reset org.gnome.desktop.interface cursor-theme

Returned me to a working default

---

### Post by Dennis N on 2024-05-25
There's bug report on the DMZ cursor. A fix is in progress. Meanwhile use something else.

---

### Post by darmaza on 2024-07-27
Thanks for sharing, using this command I was also able to solve my mouse pointer issue.

---

