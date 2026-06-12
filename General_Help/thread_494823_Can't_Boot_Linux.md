---
title: "Can't Boot Linux"
date: 2007-07-07
forum: General Help
---

### Post by Computer-Slave on 2007-07-07
HI,
    People please help me. I'm using Ubuntu Linux 7.04. I just changed it's theme and shutdown the computer. When i again started it, it went to the login screen and when i logged on it showed loading nautilus then it showed the outline of the desktop e.g no wallpaper but solid color instead, two panels above and below but without applets or anything. The desktop was also without icons. There i could do nothing and after sometime it automatically logged out. When i restarted it halted and then i restarted manually nut now when ever it boots it says "can't access tty; controls turned off" or a little bit change statement. So plz help me what can i do.

Thanks in Advance!

---

### Post by kagashe on 2007-07-07
Create another user and try to login the new user in default theme.

kagashe

---

### Post by Computer-Slave on 2007-07-07
> **kagashe said:**
> Create another user and try to login the new user in default theme.

kagashe
I can't even boot Linux?

---

### Post by darkdigger on 2007-07-07
Once you get the tty error, try pressing Alt-F1 or Alt-F2. Do either of those take you to a login screen? If they do, login and delete the theme from your home directory. The theme is probably installed in your home directory under ~/.themes. So login and then at the prompt type:

```

# cd .themes
# ls

```
find the name of the offending theme and then type
```

# rm -rf NAME_OF_THE_BAD_THEME

```

Hope that helps!

Peace,
Arash

---

### Post by Computer-Slave on 2007-07-08
> **darkdigger said:**
> Once you get the tty error, try pressing Alt-F1 or Alt-F2. Do either of those take you to a login screen? If they do, login and delete the theme from your home directory. The theme is probably installed in your home directory under ~/.themes. So login and then at the prompt type:

```

# cd .themes
# ls

```
find the name of the offending theme and then type
```

# rm -rf NAME_OF_THE_BAD_THEME

```

Hope that helps!

Peace,
Arash
Thanks! but i reinstalled ubuntu and now it'a 64-bit edition. and by the way how do i upgrade to gutsy gibbon.

Thanks!

---

### Post by confused57 on 2007-07-08
Here's how to upgrade from Edgy to Feisty:
[https://help.ubuntu.com/community/FeistyUpgradesManual](https://help.ubuntu.com/community/FeistyUpgradesManual)
You can just substitute gutsy for feisty...be prepared for plenty of breakage, things not working, etc,  and numerous daily updates.

---

### Post by Computer-Slave on 2007-07-08
> **confused57 said:**
> Here's how to upgrade from Edgy to Feisty:
[https://help.ubuntu.com/community/FeistyUpgradesManual](https://help.ubuntu.com/community/FeistyUpgradesManual)
You can just substitute gutsy for feisty...be prepared for plenty of breakage, things not working, etc,  and numerous daily updates.
Thanks but im already having many breakages on Feisty too.

Thanks!

---

