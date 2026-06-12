---
title: "How to disable password keyring in Xubuntu 14.04?"
date: 2015-10-17
forum: General Help
---

### Post by markodd on 2015-10-17
Hey,

I'm using Xubuntu 14.04 and everytime I open chromium, after some seconds an annoying "password keyring" pop-up appears. If I cancel said pop-up and close chromium, for some reason, chromium will not open again. I'll need to restart the OS in order to open the browser.


So, how do I disable the goddamn password keyring?

---

### Post by mcduck on 2015-10-17
As long as the programs themselves want to use a keyring, you can't disable it without breaking those programs.

However if you just want to get rid of password prompts (and the security a keyring can provide), simply set the keyring password to empty and it shouldn't bother you any more. Although at least with Gnome/UNity desktops, having the keyring password set to same as your login password should automatically unlock the keyring at login time, while still keeping your passwords and keys secured.

---

### Post by markodd on 2015-10-17
Thank you for replying @mcduck. Though, could you explain to me why chromium requires that? As someone that is quite paranoid of google, is there any reason of why I shouldn't set it to the same pw as my login password?

---

### Post by mcduck on 2015-10-17
If you are paranoid with Google, then using the keyring would be perfect option, as it stores your website passwords and other things *outside* of chromium, using the keyring the OS provides.

Anyway, the security a keyring can provide is about what happens if somebody gets access to your computer. Keyring keeps the passwords stored in encrypted format, so as long as the keyring is locked (you are not logged in, or haven't unlocked the keyring otherwise), nobody can access your passwords even if they can read any unencrypted files from your hard drive. 

Using same password as login password is what you'd usually want, so the passwords would be available to you easily when you are logged in, and locked securely when you shut down the machine, log out or out or lock your desktop (which you should of course do when you leave the computer unattended and there are other people around ;)).

The only reason to use a different password would be if you wanted extra security in case somebody finds out your login password ot otherwise gains access to your user account (in which case I'd say you already have quite a security problem). Or possibly if you use multiple keyrings for different purposes, although that would be pretty uncommon setup for any normal use.

---

### Post by VMC on 2015-10-17
> **mcduck said:**
> As long as the programs themselves want to use a keyring, you can't disable it without breaking those programs.

However if you just want to get rid of password prompts (and the security a keyring can provide), simply set the keyring password to empty and it shouldn't bother you any more. Although at least with Gnome/UNity desktops, having the keyring password set to same as your login password should automatically unlock the keyring at login time, while still keeping your passwords and keys secured.

Using the empty password in the past made keyring folder viewable. Also, in the past I needed Seahourse installed into order tho blank the password. So I skipped all that and used your suggestion found [here]("http://ubuntuforums.org/showthread.php?t=1655397"), since Chrome triggers keyring on my machine.

---

### Post by mcduck on 2015-10-18
well, disabling the keyring completely most certainly won't make things any more secure than using the keyring but without a password ;)

What I really recommend, is using the keyring as intended, with the password set to same as login password so it gets unlocked automatically at login, and keeps things safe when you are not using the system. Pretty much zero effort for a nice improvement in security.

---

