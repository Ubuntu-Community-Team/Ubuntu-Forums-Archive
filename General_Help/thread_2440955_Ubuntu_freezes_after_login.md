---
title: "Ubuntu freezes after login"
date: 2020-04-17
forum: General Help
---

### Post by Hasimir on 2020-04-17
I am running Ubuntu 19.10 on mt Asus laptop since its first release with no major problems.
Today I was reorganising some JPGs and, after putting lots of them (but less than 200) in a single folder, I selected them all and hit the DEL key on my keyboard.
The computer froze.
(my file manager is Pantheon)

I had to reboot using the long-press power button on my keyboard.
On startup I entered my login credentials and the system booted normally.
I saw the desktop.
My usual programs started launching at startup (mainly Rambox).
And... everything is frozen again.

I can perform the Ctrl+Alt+F1 logout.
Or the Ctrl+Alt+F3 switch to the terminal. From here I tried pkill rambox ... but when I F1 log into the UI, everything is still frozen.

**What can I do?**

Maybe unrelated... I noticed that on system boot this message appears:
Initramfs unpacking failed: Decoding failed
/dev/sdb6: clean, 942975 / 3523856 files, 12936354 / 14115072 blocks

---

### Post by Hasimir on 2020-04-17
After many unfruitful attempt I "solved" (???) the problem like this.
At the login screen I clicked the gear button to select a different graphic environment (is that the correct name?).
I usually am on GNOME Xorg.
I selected GNOME Classic.
This made the desktop load in a way that seemed functional.
I went to my file manager and checked the folder where I deleted the images... it was empty.
So I went to the trash and gave the command to empty it too.
The system froze again.

Reboot, this time back to GNOME Xorg ... everything seems to work.
Hopefully.
Maybe.
So far.

---

