---
title: "Keyring stuck on old password that I forgot"
date: 2019-03-03
forum: General Help
---

### Post by Rob_R on 2019-03-03
I'm on ubuntu mate 18.04

First I forgot the password for this computer, I had to go into the recovery mode and change it via the terminal.

Now whenever I launch a browser, I get a notification that the system password doesn't match the keyring password and it wants the old password.

It will go away after a spell, but I'd like to reset the keyring.  All the advice I've found via googling is obsolete.  I saw that the easy thing would be to delete the keyring files to reset it.  I just can't figure out where those files are and I don't want to delete the wrong thing.

---

### Post by gsahli on 2019-03-04
~/.local/share/keyrings

---

### Post by Rob_R on 2019-03-10
Greetings,
I went into the root folder and I'm not finding a .local folder even after revealing hidden files.

---

### Post by jdeca57 on 2019-03-10
> **Rob_R said:**
> Greetings,
I went into the root folder and I'm not finding a .local folder even after revealing hidden files.
Well it's not in the root folder but in your home folder - that's what the ~ means. And there should be that folder. Look again. ;-)

---

### Post by mthebeau on 2019-05-28
Hi, I do not see an answer or confirmation.  I'm on 16.04.  I am not using auto-login.

I had similar sounding problem this morning.  Summary: I had an old/lost keyring password, and an out-of-sync password for "Login" in the "Passwords and Keys" application (seahorse).

I had reset my login password over the weekend and was unable to unlock the keyring when prompted.  I used "Passwords and Keys", which is apparently "seahorse" command line.  I deleted "Default Keyring" under Passwords.  After reboot and login I was prompted for a new keyring password.  After that when being asked to unlock the keyring I was able to.

But each time I logged into Ubuntu I was asked to unlock the keyring, which I've understood should be automatic.  I used "Passwords and Keys" again, to manually unlock "Login" with my old password and manually reset the its password to the same as my login.

After that, when I reboot and login the keyring unlocks without my intervention.

So for me there was an old/lost keyring password and an out-of-sync password for "Login" in the "Passwords and Keys" application (seahorse).

---

### Post by yetimon_64 on 2019-05-28
> **gsahli said:**
> ~/.local/share/keyringsYes, that is the directory that holds the login keyring for the user. On a root prompt the system variable "~" will expand to "/root" not "/home/<user-name>", which is something to keep in mind when trying to change a password or fix an out of sync password from a root console.

@ OP, to avoid this issue in future; while on the root console and after you use the passwd command to change your user password, delete the existing login keyring  with ...
```
rm /home/<your-normal-user-name>/.local/share/keyrings/login.keyring
```Replace "<your-normal-user-name>" in the above command with your usual log in name,
**Ensure you type that path correctly**, **using the rm command as root can be catastrophic if used wrongly.**
 Then simply reboot back to a normal user log in.

Deleting the login.kerying file at the same time as changing the password will in future keep the keying in sync with your new password.

**Edit:** just noted that this thread is a couple of months old and recently resurrected. ;-)

---

