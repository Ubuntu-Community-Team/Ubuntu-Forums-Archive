---
title: "Login help!!!"
date: 2008-02-07
forum: General Help
---

### Post by Clayton South on 2008-02-07
Hi All,

Im running Gutsy, and heres the problem:

I make changes to the Login Window menu (System, Administration, Login Window) and the changes are never saved - ever.  I tried to select Gnome as the default login manager but it keeps going back to Run Xclient script. I tried to disable the login sound, but it went back to the default.

What can I do to fix this? Please help!

Thanks!

-Clayton South

---

### Post by bodhi.zazen on 2008-02-07
did you run as root ?

```
gksu gdmsetup
```

---

### Post by Clayton South on 2008-02-07
Hi! Thanks for this. 

I am the root user, and I typed this in and this is the resulting text (about 30 times of this line)

gdmsetup[7099]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed


I have no idea what this means...ive never seen this before..please help.

-Clayton South

---

### Post by bodhi.zazen on 2008-02-07
> **Clayton South said:**
> Hi! Thanks for this. 

I am the root user, and I typed this in and this is the resulting text (about 30 times of this line)

gdmsetup[7099]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed


I have no idea what this means...ive never seen this before..please help.

-Clayton South

Stop running as root. Running as root is never a good idea and seems to be the source of your problems.

If your problem persists once you are running as a regular user, in the admin group, re-post any error message.

---

### Post by Clayton South on 2008-02-07
Hi again,

I am no longer the root user but the changes still wont hold. I typed in gdmsetup and it told me that Genome Display Manager wasn't running - which isn't true because it's installed and I have desktop effects enabled....

When I typed in the gksu command I continued to get the same error messages as before, and when I simply typed in the gdmsetup without the gksu, the window appeared, without the error messages, but the changes didn't save....

I'm not sure what to do now...

-Clayton South

---

### Post by bodhi.zazen on 2008-02-07
Not sure if this will work, but it may be worth a try.

Log in as your non-root user

Open a terminal.

```
sudo -i # <-- enter user password
gdmsetup
```

If that fails, you could try re-installing gdm.

---

### Post by Clayton South on 2008-02-13
Hi, thanks for your help. Here's an update.

I had to uninstall and re-install GDM in the recovery boot mode.

Don't know if my update will be helpful to anyone else, but i hope so. As soon as I reinstalled GDM, my login worked fine.

-Clayton South

---

