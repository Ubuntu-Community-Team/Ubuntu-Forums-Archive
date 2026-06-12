---
title: "Ubuntu keeps asking me for my keyring password, I enter my loging password, no go"
date: 2014-10-23
forum: General Help
---

### Post by MechaMechanism on 2014-10-23
The keyring password box pops up asking me for the password.  I enter my password that I use to log in, but nothing happens.  I followed advice elsewhere to reset keyring password.  But when I do so it ask for old password and I don't know that.  I only know my log in password.  Nothing bad happens, I can still use my computer.  But the keyring box keeps poping up, very annoying.

---

### Post by nerdtron on 2014-10-23
You are using chrome browser? Maybe the password for your google chrome account.

---

### Post by MechaMechanism on 2014-10-23
> **nerdtron said:**
> You are using chrome browser? Maybe the password for your google chrome account.

Yep.  Every time I open Chromium that box pops up.  I tried my Google password and no go.  I must have used a different password for sync other than my Google password.  I reset my sync and chose to use my Google password this time.  The box still pops up.  Let me look for the old password and I will get back to you.  I might have it written down somewhere.

---

### Post by ajgreeny on 2014-10-23
I am fairly sure you can try renaming (or sending to trash) the files in **~/.gnome2/keyrings** which are probably **login.keyring** and **user.keystore** then next time the password request pops up you should be able to either just hit enter to leave it blank, ignoring the warning about unsafe storage if you are happy with that, or you can set a password you will remember.

If that is not successful just restore the old files.

---

### Post by MechaMechanism on 2014-10-23
I append the key files in /home/nate/.gnome2/keyrings to .backup.  I also had to rename the files in /home/nate/.local/share/keyrings.  Once I did that I logged out and back in and the key files were automatically recreated.  Everything works now.

Thank you everybody.

---

### Post by CantankRus on 2014-10-23
See [**_[COLOR="#B22222"]How to recover/reset forgotten Gnome Keyring Password?[/COLOR]_**]("http://askubuntu.com/questions/65281/how-to-recover-reset-forgotten-gnome-keyring-password")
Follow the directions with the heading "**Using the same keyring (resetting keyring password but keeping old passwords in keyring):**"

---

