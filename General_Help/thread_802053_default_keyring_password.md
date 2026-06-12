---
title: "default keyring password?"
date: 2008-05-21
forum: General Help
---

### Post by adz666 on 2008-05-21
i am really starting to get annoyed at the fact that i have to enter my password to connect to my wireless internet.

is there a way to remove this password or make it automatically connect to my wireless.

i have tried going into home/.gnome2/keyrings but there isn't default.keyring in there.

please make any instructions as easy as possible as i am not exactly skilled with a terminal.

preferably stuff that doesn't include the terminal but copy and paste stuff is fine.

p.s. i am using Ubuntu 7.10 if that helps

---

### Post by sdennie on 2008-05-21
Are you using Ubuntu 8.04?  I think 8.04 has the pam utils setup such that if your keyring and login passwords are the same, it won't prompt you for a keyring password.

---

### Post by adz666 on 2008-05-21
i am using 7.10 is there still a way to do this?

---

### Post by sdennie on 2008-05-21
I don't know and have no way to check.  Are your keyring and login passwords the same?  There was a link for older Ubuntu versions about how to setup pam to not prompt for a keyring password but, I can't seem to find it anymore.

---

### Post by adz666 on 2008-05-21
my passwords are the same.

---

### Post by ctrlf5 on 2008-05-21
This thing drove my crazy for days. I searched all over the internet and couldn't get any of the proposed "use-same-password-and-do-something-with-pamkeyring" solutions to work.

Finally, I installed [Wicd]("http://wicd.sourceforge.net/download.php") and followed the **Installing Wicd in Ubuntu** instructions (very simple). No more wifi or login problems for me.

If however, you want to continue using Network Manager, then a search brought up [this solution]("http://ubuntuforums.org/showthread.php?t=192281").

---

