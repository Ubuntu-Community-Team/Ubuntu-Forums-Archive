---
title: "Unable to shutdown using gdm"
date: 2004-10-25
forum: General Help
---

### Post by josel on 2004-10-25
When cliking on reboot or shutdown, at gdm login screen, nothing happens except that user and password dialogs "cycle". I have to open a virtual console and do a "sudo shutdown -h now".
I think the problem showed up after i played around with kde 3.3 debs from [http://geeksoc.org/~jr/ubuntu/](http://geeksoc.org/~jr/ubuntu/) , but i'm not sure.

Any idea how i can return to "normality" with gdm?

Cheers

---

### Post by FLeiXiuS on 2004-10-25
This should restore default configurations..

```
sudo dpkg-reconfigure gdm
```

---

### Post by josel on 2004-10-25
[QUOTE=FLeiXiuS]This should restore default configurations..

```
sudo dpkg-reconfigure gdm
```[/QUOTE]

Unfortunattely it didnt change anything - also after killing gdm and running the command on konsole . 
When i log out of gnome get the options to reboot or shutdown. But when at gdm screen and cliking on "shutdown" or "reboot" it just cycles between user and password.
 #-o

---

### Post by FLeiXiuS on 2004-10-26
Perhaps this could be another power management problem...check this forum..


[http://ubuntuforums.org/showthread.php?t=2058](http://ubuntuforums.org/showthread.php?t=2058)

---

### Post by josel on 2004-10-27
It couldn't be the same problem since logging off from gnome gives med the correct options. Thank you for the sugestion thoug.

---

