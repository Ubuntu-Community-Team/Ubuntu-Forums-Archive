---
title: "wine works poorly for non-admin user"
date: 2007-07-03
forum: General Help
---

### Post by ubuntnew on 2007-07-03
I'm computer literate but no power user and I've had problems setting up wine under Xubuntu Fiesty.

Wine installed and worked fine using the standard repository and I successfully installed Word 97 as an admin user. However, I then created a non-administrative user and installed Word 97 for them and the windows controls are playing up. I only get the first word or two on most dialog boxes and buttons and lists etc disappear.

I'm not entirely certain whether this happens before or after installing Word. I thought I had renamed the .wine folder and re-run winecfg and the controls worked, but I tried that today and the controls are still shot.

Any guesses what I'm doing wrong? Does wine not work well for non-admin users? Or is it something to do with Word?

Thanks.

---

### Post by GeeZor on 2007-07-03
other than being a microsoft product???  ;)

---

### Post by splintercellguy on 2007-07-03
Think you might have to chown the .wine directory.

---

### Post by GeeZor on 2007-07-03
and maybe do a ```
chmod 700 /home/<user>*
``` to make it complete...

---

