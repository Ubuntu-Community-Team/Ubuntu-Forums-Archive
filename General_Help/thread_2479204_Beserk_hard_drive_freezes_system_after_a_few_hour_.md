---
title: "Beserk hard drive freezes system after a few hour use"
date: 2022-09-17
forum: General Help
---

### Post by RogerDavis on 2022-09-17
After a few hours use, this message, among several others, repeats rapidly, hard drive continually seeks, system unusable. Reboot, runs ok for a while (couple hours or so), then it starts again. Sometimes I have to use the reset button to stop it, sometimes I can get to restart.
Just a very short set of samples below - this and similar will go on forever until I shut down and restart :

Aug 31 21:24:26 roger-desktop gnome-panel[2348]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 31 21:25:03 roger-desktop rtkit-daemon[1573]: Supervising 5 threads of 2 processes of 1 users.
Aug 31 21:25:05 roger-desktop rtkit-daemon[1573]: message repeated 3 times: [ Supervising 5 threads of 2 processes of 1 users.]
Aug 31 21:25:26 roger-desktop gnome-panel[2348]: gtk_icon_info_get_filename: assertion 'icon_info != NULL' failed
Aug 31 21:25:26 roger-desktop gnome-panel[2348]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 31 21:25:26 roger-desktop gnome-panel[2348]: gtk_icon_info_get_filename: assertion 'icon_info != NULL' failed
Aug 31 21:25:26 roger-desktop gnome-panel[2348]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 31 21:25:26 roger-desktop gnome-panel[2348]: gtk_icon_info_get_filename: assertion 'icon_info != NULL' failed
Aug 31 21:25:26 roger-desktop gnome-panel[2348]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 31 21:25:50 roger-desktop PackageKit: daemon quit
Aug 31 21:25:50 roger-desktop systemd[1]: packagekit.service: Succeeded.
Aug 31 21:25:56 roger-desktop gnome-panel[2348]: gtk_icon_info_get_filename: assertion 'icon_info != NULL' failed
Aug 31 21:25:56 roger-desktop gnome-panel[2348]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 31 21:25:56 roger-desktop gnome-panel[2348]: gtk_icon_info_get_filename: assertion 'icon_info != NULL' failed
Aug 31 21:25:56 roger-desktop gnome-panel[2348]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 31 21:25:56 roger-desktop gnome-panel[2348]: gtk_icon_info_get_filename: assertion 'icon_info != NULL' failed
Aug 31 21:25:56 roger-desktop gnome-panel[2348]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 31 21:26:26 roger-desktop gnome-panel[2348]: gtk_icon_info_get_filename: assertion 'icon_info != NULL' failed
Aug 31 21:26:26 roger-desktop gnome-panel[2348]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 31 21:26:26 roger-desktop gnome-panel[2348]: gtk_icon_info_get_filename: assertion 'icon_info != NULL' failed
Aug 31 21:26:26 roger-desktop gnome-panel[2348]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 31 21:26:26 roger-desktop gnome-panel[2348]: gtk_icon_info_get_filename: assertion 'icon_info != NULL' failed
Aug 31 21:26:26 roger-desktop gnome-panel[2348]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 31 21:26:56 roger-desktop gnome-panel[2348]: gtk_icon_info_get_filename: assertion 'icon_info != NULL' failed
Aug 31 21:26:56 roger-desktop gnome-panel[2348]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 31 21:26:56 roger-desktop gnome-panel[2348]: gtk_icon_info_get_filename: assertion 'icon_info != NULL' failed
Aug 31 21:26:56 roger-desktop gnome-panel[2348]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 31 21:26:56...

---

### Post by &amp;KyT$0P# on 2022-09-18
Check if one of your enabled GNOME extensions is misbehaving?

---

### Post by TheFu on 2022-09-18
Create a new user account, login with that and see if the problem is fixed.
By doing this, you'll know if it is a system-wide issue or just settings under 1 account.

---

### Post by HermanAB on 2022-09-18
Make a backup of your data!

---

### Post by RogerDavis on 2022-09-18
-> Check if one of your enabled GNOME extensions is misbehaving? 
How do I do that?
-> Create a new user account, login with that and see if the problem is fixed. By doing this, you'll know if it is a system-wide issue or just settings under 1 account. 
Do you mean Ubuntu account, or browser account?

---

### Post by RogerDavis on 2022-09-18
How do I do that?

---

### Post by RogerDavis on 2022-09-18
Do you mean Ubuntu account, or browser (Firefox) account?

---

### Post by RogerDavis on 2022-09-18
Do you mean Ubuntu account, or browser (Firefox) account?

---

### Post by &amp;KyT$0P# on 2022-09-19
> **RogerDavis said:**
> -> Check if one of your enabled GNOME extensions is misbehaving? 
How do I do that?

You can disable the active ones in the "Extensions" app, then do Alt+F2 and enter "r" to restart GNOME shell and see if the problem persists.  If not, then enable your desired extensions back one at a time, checking after each one whether the problem has returned.

---

