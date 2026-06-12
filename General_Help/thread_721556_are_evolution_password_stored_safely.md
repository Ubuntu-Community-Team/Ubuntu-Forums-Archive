---
title: "are evolution password stored safely?"
date: 2008-03-11
forum: General Help
---

### Post by gsoundsgood on 2008-03-11
i would like to know if it is safe to store password with evolution. 
i'm running ubuntu gutsy, evolution 2.12.1.

as i understand it (and i might well be wrong), by default evolution passwords are not encrypted. so other sudoers on my computer could easily grab my password. 

i would like to set something like a master password for evolution.
or even better, store it in a keyring, possibly authomatically activated at login. 

thank you for your time

---

### Post by gobbles414 on 2008-03-11
> **gsoundsgood said:**
> i would like to know if it is safe to store password with evolution. 
i'm running ubuntu gutsy, evolution 2.12.1.

as i understand it (and i might well be wrong), by default evolution passwords are not encrypted. so other sudoers on my computer could easily grab my password. 

i would like to set something like a master password for evolution.
or even better, store it in a keyring, possibly authomatically activated at login. 

thank you for your time

I can't answer your question with specifics. But I can provide a commonsense answer. IMHO, it is never safe to allow an email program to store passwords on a laptop, PDA, or cellphone. That's just inviting ID theft. Are you using Ubuntu on a desktop PC? If other users have access to your desktop -- remotely or locally -- you shouldn't allow Evolution to store your password either, because anyone who has sudo rights on your system could easily install a keylogger on your system without your knowledge. Evolution may or may not encrypt your password. Of course, the keylogger threat exists on mobile devices such as laptops as well.

---

### Post by dcstar on 2008-03-12
> **gobbles414 said:**
> I can't answer your question with specifics. But I can provide a commonsense answer. IMHO, it is never safe to allow an email program to store passwords on a laptop, PDA, or cellphone. That's just inviting ID theft. Are you using Ubuntu on a desktop PC? If other users have access to your desktop -- remotely or locally -- you shouldn't allow Evolution to store your password either, because anyone who has sudo rights on your system could easily install a keylogger on your system without your knowledge. Evolution may or may not encrypt your password. Of course, the keylogger threat exists on mobile devices such as laptops as well.

Keyloggers - and I'd like you to tell us what Linux ones are out there - work when you DON'T have passwords stored and have to type them in - so if Evolution already has the password stored then a keylogger will be USELESS as you won't have to type any password.

Evolution's mail passwords are stored in .gnome2_private/Evolution and are encrypted.

---

### Post by gsoundsgood on 2008-03-12
thank you for your answers.
i tried to log out, and then log in with another user on my system. i might as well done the same with a live CD, not knowing any password,or booting in rescue mode.
i checked .gnome2_private/Evolution on my primary user. 
i could see usernames and passwords. passwords were "encrypted" in standard base64. so i just googled for base64, copy/pasted my "encrypted" passwords there, and i could see them in plain text.
actually i also expected them to be safely encrypted, and made available only at login.
i mean, i could encrypt .gnome2_private folder with encfs, and have it decrypted automatically at login (or later at request).

but isn't there a more straightforward way? i know it's never 100% safe to keep password saved on a laptop. but if they are encrypted, at least i'm sure i'll have all the time to change them. 

all suggestions are welcome.

---

### Post by gobbles414 on 2008-03-12
> **dcstar said:**
> Keyloggers - and I'd like you to tell us what Linux ones are out there - work when you DON'T have passwords stored and have to type them in - so if Evolution already has the password stored then a keylogger will be USELESS as you won't have to type any password.

Evolution's mail passwords are stored in .gnome2_private/Evolution and are encrypted.

I have to admit that you're absolutely correct about the flaw in my logic! A keylogger wouldn't have anything to copy if the password were stored in Evolution. Nevertheless, I'm still against storing passwords for any program or website on a computer -- especially after reading the results of gsoundsgood's experiment.

But I must strongly disagree with you about the existence of keyloggers for Linux. Due to my interpretation of the regulations of these forums, I hesitate to post any Linux keylogger-related links in this thread. But a 30 second trip to Google will provide links to both commercial and freeware Linux keyloggers.

---

### Post by gobbles414 on 2008-03-12
> **gsoundsgood said:**
> thank you for your answers.
i tried to log out, and then log in with another user on my system. i might as well done the same with a live CD, not knowing any password,or booting in rescue mode.
i checked .gnome2_private/Evolution on my primary user. 
i could see usernames and passwords. passwords were "encrypted" in standard base64. so i just googled for base64, copy/pasted my "encrypted" passwords there, and i could see them in plain text.
actually i also expected them to be safely encrypted, and made available only at login.
i mean, i could encrypt .gnome2_private folder with encfs, and have it decrypted automatically at login (or later at request).

but isn't there a more straightforward way? i know it's never 100% safe to keep password saved on a laptop. but if they are encrypted, at least i'm sure i'll have all the time to change them. 

all suggestions are welcome.

That makes it sound WAY TOO EASY to break Evolution's password encryption! I'm afraid that I don't have any technical advice to offer you. But I still think that the wisest course of action is to just forget about storing any passwords on your computer.

The only possible exception to this rule might be the encryption key for your wireless network. But due to a bug in at least my installation of Ubuntu 7.10 (GNOME), the encryption key for a wireless network is automatically added to the keychain anyway. So that kind of removes that choice from your control regardless of your stance on the issue of passwords.

---

