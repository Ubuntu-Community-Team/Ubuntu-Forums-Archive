---
title: "xubuntu 20.04 - not able to configure to bypass log-in (start-up, sleep recovery)"
date: 2023-09-28
forum: General Help
---

### Post by wb0gaz on 2023-09-28
Installed xubuntu 20.04 and unable to configure for auto log-in (that is, bypass the log-in screen, go directly to desktop.)

The machine is personal use only, so log-in screens are redundant impediment (hence, replies to this inquiry admonishing use of log-in dialog is not helpful.)

What I've tried:

system > user settings > password = not asked at log-in
  (what this accomplishes - the unwanted log-in dialog box still appears, but there is no longer a password input request.)

edit /etc/lightdm/lightdm.conf to include autologin-session=xubuntu
  (what this accomplishes - nothing, unlike xubuntu 18.04 where this provided the desired behavior)

copy /etc/lightdm/lightdm.conf to /etc/lightdm/lightdm.conf.d/
  (what this accomplishes - nothing)

As this is the only "barrier of entry" to migration to xubunu 20.04 (from 18.04), assistance would be appreciated.

Side note - attempted migration to xubuntu 22.04, however, video driver does not properly support the machine and boot-up time is several seconds slower, so focusing on 20.04)

---

### Post by MAFoElffen on 2023-09-28
Look at the attached screenshot. 

In Xubuntu, open Users and Groups. At Password, select changes. At the bootem of the dialog that opens, setelct the checkbox that says: Do Not Ask. Will auto-login that user.

As for the screen-lock, it does exactly as what the name implies, and asks for the password of the User. The only way to disable that is to Open Power Management. Select the Display Tab. Slide all three controls to the left to select "Never". Toggle Power management off.

If you want something to replace the Lock-Screen, then install a screen saver.

---

