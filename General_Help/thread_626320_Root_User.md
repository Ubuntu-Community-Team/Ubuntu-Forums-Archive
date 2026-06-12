---
title: "Root User"
date: 2007-11-28
forum: General Help
---

### Post by Krusader3z on 2007-11-28
Is there a way that I can automatically boot Ubuntu and be able to just do what I want?

I keep getting errors that say such-and-such is "owned" by the root user.

---

### Post by PmDematagoda on 2007-11-28
You can do that by using the Recovery Mode of Ubuntu, but this is rather dangerous as you can delete critical system files and mess your entire system up. Why do you want this anyway?

---

### Post by Krusader3z on 2007-11-29
Because I'm trying to play Rune Scape and it keeps telling me it is unable to store it's temporary files. It is unable to create it's temporary files in directory /rscache

Basically I want to be able to create and modify folders anywhere in the file-system like I can do in windows. Why can't i do this with Ubuntu? It seems like it forces me to limit myself to my home folder..

---

### Post by TDK800 on 2007-11-29
what the hell is the fricking default root password on ubuntu, so I could frickin su to root in terminal, the system didn't detect the usb clipdrive and now i can't manually frickin install it, says root permission required, didnt prompt to enter root pass during installation

---

### Post by oscarsfriend on 2007-11-29
Krusader3z, this is for security reasons.  Your best option is to change permissions of the directory, with something like "sudo chmod a+rw /yourdirectory".

TDK800, by default there is no root password.  Use sudo instead to run commands, and your account password.

---

### Post by tommcd on 2007-11-29
> **Krusader3z said:**
> Because I'm trying to play Rune Scape and it keeps telling me it is unable to store it's temporary files. It is unable to create it's temporary files in directory /rscache

Basically I want to be able to create and modify folders anywhere in the file-system like I can do in windows. Why can't i do this with Ubuntu? It seems like it forces me to limit myself to my home folder..

You could do "sudo chown your_user_name:users -R /rscache". Just cd into the directory where /rsache is located first. Many games are installed to /usr/local/games. Be careful about changing ownership or read/write permissions to system files though. Those permissions are there for your security. Passwords in linux are there to save your butt. Learn to love them!
Ubuntu uses sudo instead of a separate root account:
[https://help.ubuntu.com/community/RootSudo?highlight=%28root%29%7C%28account%29](https://help.ubuntu.com/community/RootSudo?highlight=%28root%29%7C%28account%29)

---

### Post by Keith Hedger on 2007-11-29
TDK800  the root account is not enabled by default for security purposes if you must use it you must enable it yourself but i wouldnt recomend it, sudo gives admin access to any part of the system and is usually sufficient (and no i am not going to tell u how to enable the root account, if u dont know u shouldent be doing it:) )

---

