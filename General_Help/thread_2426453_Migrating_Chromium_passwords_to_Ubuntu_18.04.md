---
title: "Migrating Chromium passwords to Ubuntu 18.04"
date: 2019-09-09
forum: General Help
---

### Post by whairst on 2019-09-09
I recently tried upgrading my Ubuntu 14.04 machine to 16.04, but things went horribly pear-shaped. So, I installed 18.04. In 14.04, I was using Chromium, and had it set to store passwords in the GNOME keyring. I successfully located the keyring, copied it to my account under 18.04, unlocked it (same username and password as under 14.04), and confirmed the passwords are there using Seahorse. When I run Chromium (as a Snap, apparently) under 18.04, it doesn't have the passwords listed in the GNOME keyring. I tried "chromium --password-store=gnome", but I can't see any difference between that and "chromium --password-store=basic". Any ideas on how to complete the migration?

---

### Post by deadflowr on 2019-09-09
Restore your old chromium profile folder.
Was at ~/.config/chromium.
Assuming you had the old one backed up.

---

### Post by ajgreeny on 2019-09-09
This could be a result of using chromium as a snap package which by design, as far as I understand, does not always have access to all system files and folders.

Remove the snap and then install chromium with the normal package management system and you should find all is well.  I assume you have the ~/.config/chromium folder which will have all the saved configuration for chromium.

---

### Post by deadflowr on 2019-09-09
In cases of snaps copy the profile to the ~/snap/chromium/current/.config folder.
If using gui, it'll ask to replace existing folder and contents, just say yes/okay.

---

### Post by ajgreeny on 2019-09-09
> **deadflowr said:**
> In cases of snaps copy the profile to the ~/snap/chromium/current/.config folder.
If using gui, it'll ask to replace existing folder and contents, just say yes/okay.
Interesting!
Thanks deadflowr; I was not aware of any of that, but then I do not have any snaps on my systems.

---

### Post by whairst on 2019-09-09
Curiouser and curiouser. I uninstalled the Snap version of Chromium and installed the regular one. Verified with seahorse that the passwords were there and readable. I restored my .login/share/keyrings/login.keyring file, just to make sure, and copied the Chromium folder (including profile) from my old system. Started Chromium - no passwords. Closed Chromium and opened seahorse - all the entries were there, but the passwords looked to have been encrypted.

---

### Post by whairst on 2019-09-12
Got it! I tried again, ever so slightly differently, and it worked. Steps to reproduce:

1. Copy .login/share/keyrings/login.keyring to new computer, same location
2. Copy .config/chromium (the whole folder, NOT just the profile) to new computer, same location
3. Using command line (NOT the launcher icon!) run "chromium-browser --password-store=gnome"

That's  it. Confirmed reboot and log in again doesn't affect it - passwords  still there in Chromium. Oddly, they've disappeared from login.keyring  (according to seahorse), but are now in .config/chromium/[profile]/Login  Data in some kind of encrypted format. (Use [https://inloop.github.io/sqlite-viewer/](https://inloop.github.io/sqlite-viewer/) to view the contents of the Login Data file.)

So,  to back up my passwords for the future, I need to back up  .config/chromium, and probably .local/share/keyrings/login.keyring (just  in case). Anything else?

---

