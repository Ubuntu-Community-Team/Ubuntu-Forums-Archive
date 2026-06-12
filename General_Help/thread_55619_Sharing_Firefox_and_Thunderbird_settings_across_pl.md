---
title: "Sharing Firefox and Thunderbird settings across platforms"
date: 2005-08-09
forum: General Help
---

### Post by cjoshuav on 2005-08-09
Is it possible for me to store my Thunderbird e-mail and settings files, as well as my Firefox bookmarks in a single location on a Fat32 partition so that both my Linux and WinXP versions of these app's could access them?

Joshua

---

### Post by manicka on 2005-08-09
It should be possible to symlink your bookmarks file from your fat32 partition to your Linux installation but I don't think you'll have any luck with thunderbird.

---

### Post by wylfing on 2005-08-09
The short answer is No, you cannot do this.

The long answer is Yes, this is possible, but you are going to run into many, many snags and hurdles that don't make any sense, and/or some major inconveniences.

(And no, symlinking things mysteriously does not work correctly. You can't save new bookmarks from the symlinked side.)

---

### Post by johanvdw on 2005-08-09
Check:
[http://texturizer.net/thunderbird/share_mail.html](http://texturizer.net/thunderbird/share_mail.html)

---

### Post by cjoshuav on 2005-08-09
Wow!  Exactly what I needed!  Thanks very much.

Joshua

---

### Post by wylfing on 2005-08-09
[QUOTE=johanvdw]Check:
[http://texturizer.net/thunderbird/share_mail.html](http://texturizer.net/thunderbird/share_mail.html)[/QUOTE]

This is technically correct, but it is going to be a major PITA to work with. Each install of Thunderbird will maintain separate indices for mailboxes. If you get a few hundred messages in there, prepare to wait 10 minutes just to look at your mail every time you boot to a different OS.

---

### Post by cjoshuav on 2005-08-09
Grrrr...how frustrating.  On the surface it seems like it shouldn't be that difficult to do.

Joshua

---

### Post by johanvdw on 2005-08-09
I haven't used thunderbird lately, but wouldn't it also be possible to just create a symlink ~/.thunderbird/default/1a2b3c4d.slt  to /win/c/MyMail/1a2b3c4d.slt if you haven't changed set the location for the mails in the prefs.js relative instead of absolute?

---

### Post by manicka on 2005-08-09
[QUOTE=wylfing]
(And no, symlinking things mysteriously does not work correctly. You can't save new bookmarks from the symlinked side.)[/QUOTE]
That's strange, I symlink my firefox bookmarks to my mozilla ones and they write/save from either program. Must be a fat32 thing

---

