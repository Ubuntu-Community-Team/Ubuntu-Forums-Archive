---
title: "Im locked out of my Toughbook CF-73"
date: 2008-05-17
forum: General Help
---

### Post by Tru7h on 2008-05-17
Ok I have a toughbook with (i believe) 7.04 installed I can't get into the BIOS, it won't boot from CD or USB, and I have forgotten my username and pass.  Is there anything I can do to be able to use it again?

I found this but I need root access [Add new user through Terminal]("https://help.ubuntu.com/7.04/basic-commands/C/ar01s03.html#id2506691")

---

### Post by Aearenda on 2008-05-17
Can you boot into recovery mode from the GRUB menu?

---

### Post by Tru7h on 2008-05-17
Yes

---

### Post by Aearenda on 2008-05-17
1. Choose recovery mode, that should put you into a root prompt. 
2. type ```

grep 1000 /etc/passwd

```That should tell you the username used at system installation - it's the first word on the line.
Then do ```
passwd <youruser>
```(putting your username instead of <youruser>) and select a new password twice. Logout, continue the startup, and you should be able to login with your new password.

---

### Post by Tru7h on 2008-05-17
Thank you very much I've been stuck with a desktop for far too long.

---

### Post by Aearenda on 2008-05-17
The next option if that didn't work was to take the drive out and access it in a USB enclosure from the desktop. 

I'd be researching how to get into the BIOS next - just in case you need to again in the future. Desktops usually have a link on the motherboard that resets the BIOS password - maybe the laptop has too.

---

### Post by Tru7h on 2008-05-17
I took a look into it before but with toughbooks the entire bios is on a removable chip and it is impossible to reset it.  I also looked into getting a new chip but they cost like $200

---

