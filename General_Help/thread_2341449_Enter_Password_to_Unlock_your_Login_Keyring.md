---
title: "Enter Password to Unlock your Login Keyring"
date: 2016-10-28
forum: General Help
---

### Post by Quarkrad on 2016-10-28
Running mate 16.04.  This has started to happen, and may not be related, when I installed Google Chrome.  I get this message each boot.  Many google searches refer to launching Seahorse and making changes to the Login Folder under Passwords - problem is, I do not have a Login folder.  Also, most of the suggestions (that have not worked so far) are for releases other than 16.04.  Any help appreciated - I cannot stop this window from launching and having to enter the password. (pc installed with automatic login).

---

### Post by Quarkrad on 2016-10-29
Sorted - it was sort of to do with Goolge Chrome.  I am trying to get Google Cloud working and in the process had to install gnome-control-center gnome-online-accounts.  During the set up process (to get google drive to work) these packages allow your pc to access and allow inter change with your google account.  Once I deleted these packages I no longer get the keyring window pop up at boot.

---

### Post by leunam12 on 2016-10-29
I have don't have those packages an I get the same error (issue) on all computers where I install Chrome Browser. I would like to find an answer.

---

### Post by oldrocker99 on 2016-10-29
I had to enter my password for the keyring all the time, and it was because I didn't log in, but booted directly to the desktop. I changed it to a standard login, and the messages stopped.

---

### Post by joseph85750 on 2017-01-26
I couldn't get this popup to go away, no matter what I did.  But I did find the following which finally worked:
When launching chrome, do it as follows:

$ google-chrome --password-store=basic

If you have an icon/button to launch chrome, just modify the icon/properties by appending the --password-store=basic

Annyoing popup gone.

---

### Post by leunam12 on 2017-01-26
> **joseph85750 said:**
> I couldn't get this popup to go away, no matter what I did.  But I did find the following which finally worked:
When launching chrome, do it as follows:

$ google-chrome --password-store=basic

If you have an icon/button to launch chrome, just modify the icon/properties by appending the --password-store=basic

Annyoing popup gone.Great! I'm going to try this. That popup is very annoying.

---

### Post by blomstertj on 2017-01-27
I had this when I had automatic login enabled.  I think the issue stems from Google Chrome wants to store your saved user names/passwords for websites in the keyring so they are encrypted.  So if someone steals your computer and can't log in or whatever they can't look and find your saved passwords in plain text.  With automatic login disabled, meaning you have enter a password to login at boot, that automatically unlocks this keyring and the message went away for me.  Just be aware that using that command line argument may make your passwords stored unencrypted.

---

### Post by Feliks on 2017-05-19
Great solution!
Unfortunately on my computer the original launcher comes back with every update of chromium.
I solved it doing a backup of the launcher, and recopying it after the update.
Not the most elegant solution, but much better than the  login-popup.
If somebody knows a solution to make it permanent??

---

### Post by again? on 2017-05-19
> **Feliks said:**
> Great solution!
Unfortunately on my computer the original launcher comes back with every update of chromium.
I solved it doing a backup of the launcher, and recopying it after the update.
Not the most elegant solution, but much better than the  login-popup.
If somebody knows a solution to make it permanent??
Copy the launcher to **~/.local/share/applications** and edit that launcher.
Launchers in this directory take precedence over system launchers and are not overwritten with updates.

---

