---
title: "su -l user2 gnome-terminal"
date: 2008-04-03
forum: General Help
---

### Post by pranab on 2008-04-03
I am user1 and I want to open a gnome-terminal as user2. So if I do this it works:
> su -l user2
enter password
gnome-terminal &

This also works:
> su -l user2 gnome-terminal

However, both the solutions require a bash shell to login first and cannot logout of that shell. So what I want is to be able to open a terminal with another users credentials and environment, without the need to have a separate bash shell open for that user. Perhaps kdesu would work but I could not make it work properly. It seems kdesu behaves more like sudo than su. 

Ideally, I would have a kde menu entry for logging in as one of the users that opens a gnome-terminal owned by that user. So that I can use gnome-terminal feature to open new terminals as windows or tabs. The reason behind all this is so that I can test different applications with different uid/gid and bash environments. I create several test users on my system for this. 

I have pam_xauth enabled in /etc/pam,d/su that allows x-apps to be run under different users. 

Any ideas? Do you need more clarifications. I am using gutsy with kde (kubuntu).

Thanks

---

### Post by uberg on 2008-04-03
If you hit the key combination alt+F2 this will pop up an Run Application box.  If you type in gnome-terminal -e="su -l name2" this will launch a terminal window in the other users profile asking for password.  Actually, you should be able to type  this from a current terminal without locking up that terminal.  Will launch a new terminal for that other user.  Hope this helps.

---

### Post by pranab on 2008-04-03
I tried that but then the gnome-terminal process is owned by user1 (me). So when I select a "New Terminal" or "New Tab" from the new gnome-terminal it presents my shell and not the 'user2' shell. I want this new gnome-terminal process to be owned by the second user. That is why I was trying to 'su' first and then start a gnome-terminal. Ideally, that terminal should be able to run detached without a controlling tty (I do not know whether I am saying this right). 

I can do this through a complex route: first run screen, then su -l user2, and then run terminal and then detach and then exit my shell. This ensures that the terminal is owned the second user and it is detached. I feel this is unnecessarily complex. I should be able run a process like this in almost the same way as other kde gui apps that run as root.

---

