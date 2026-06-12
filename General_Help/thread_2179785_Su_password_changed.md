---
title: "Su password changed"
date: 2013-10-09
forum: General Help
---

### Post by david98 on 2013-10-09
Hi i recently updated my system from 12.04 to 13.04 and everything seemed to be running great after i updated the kernel. Now am trying to use the su -l command to install program's and when it ask me for my password I put my password in the only password iv'e used on my system and it's saying Authentication failure. How can this be it's been running fine before now. no one has access to my computer apart from my fiancée who only uses my laptop to do a bit general web surfing ie shopping social networking.  

Any advice would be greatly appreciated.

And thank you in advance Dave ):P

---

### Post by deadflowr on 2013-10-09
What happens if you just use sudo, instead of su -l.
like
```
sudo apt-get install <packagename>
```

---

### Post by david98 on 2013-10-09
It's still saying [COLOR=#000000][FONT=Ubuntu Mono]sudo [/FONT][/COLOR][COLOR=#000000]Authentication failure.[/COLOR]

---

### Post by scouser73 on 2013-10-10
Follow these steps to recover Ubuntu root password

1. Boot the machine

2. In grub menu select the **Recovery mode**

3. In the recovery menu select **Drop To Root Shell**

4. You got the root shell, change the password with **passwd**

5. If you get Authentication Manipulation error then do this,
 ```
mount -rw -o remount /
```

---

### Post by david98 on 2013-10-10
thank you very much another problem solved thank's to the help of the ubuntu community:guitar:

---

