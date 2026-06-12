---
title: "file.desktop does not appear where it should, in the lxde menu of Lubuntu"
date: 2014-07-19
forum: General Help
---

### Post by linux_dream on 2014-07-19
Hello guys! 
I've got a program to play to the game of go on the Internet. So I would like it to appear in "Games" in my lxde menu. However it appears under "Java WebStart -> KGS Online". 
I have put the file.desktop in /home/linux_dream/.local/share/applications. 
Here it is: ```
[Desktop Entry] 
Version=1.0 
Type=Application 
Icon=/home/linux_dream/.java/deployment/cache/6.0/57/3fcad4b9-57193b3c.ico 
Comment=CGoban 3 
Terminal=false 
Categories=Games; 
Name=CGoban 3 
Exec=/usr/lib/jvm/java-7-oracle/jre/bin/javaws -localfile -J-Djnlp.application.href=http://files.gokgs.com/javaBin/cgoban.jnlp /home/linux_dream/.java/deployment/cache/6.0/54/21086f76-58cc87b8 
Encoding=UTF-8
```

Any idea why it doesn't appear in "Games"?
Thanks in advance.

---

### Post by Dennis N on 2014-07-19
The category should be **Game**, not Games.

reference on possible categories:
[http://standards.freedesktop.org/menu-spec/latest/apa.html](http://standards.freedesktop.org/menu-spec/latest/apa.html)

---

### Post by linux_dream on 2014-07-19
> **Dennis N said:**
> The category should be **Game**, not Games.

reference on possible categories:
[http://standards.freedesktop.org/menu-spec/latest/apa.html](http://standards.freedesktop.org/menu-spec/latest/apa.html)

Thank you very much! This in part fixed the problem, now the program appears in Games. However it also appears in "Java WebStart -> KGS online". I've no idea about how to remove it from there.

---

### Post by Dennis N on 2014-07-19
> However it also appears in "Java WebStart -> KGS online". I've no idea about how to remove it from there. 

The same thing happens with Wine programs. They can be put under a user specified category, but also can show in a separate Wine category.  I imagine the Java WebStart is a similar setup. 

Right now, I don't have an good idea how to supress the other listing. I just leave mine as is. 

Untried: alacarte menu editor might help.

---

### Post by Dennis N on 2014-07-21
> The same thing happens with Wine programs. They can be put under a user specified category, but also can show in a separate Wine category.

Update: After a little reading, the likely reason this happens is that Wine has a separately generated menu, which is then merged with the main menu - which seems to mean it is appended as an additional category.

---

### Post by linux_dream on 2014-07-21
> **Dennis N said:**
>  Untried: alacarte menu editor might help.  Thank you very much. That worked! A bit strange though, at first I was getting errors and it seemed I couldn't erase "Java WebStart". Then I closed alacarte and restarted it, and that part of my lxde menu was gone! Very, very nice! Problem solved. :)

---

