---
title: "Oh the troubles with fluxbox"
date: 2008-01-26
forum: General Help
---

### Post by adn258 on 2008-01-26
Okay so I used the guide on here using sudo update-menus and it didn't work even though I also have GNOME installed so I went to another guide and it said use the root sudo su and then type startx and you can see what happend below.  What's happening what should I do and how do I get fluxbox working?  

austin@bomb:~$ sudo su
root@bomb:/home/austin# startx
xauth:  creating new authority file /root/.serverauth.7513

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

---

### Post by vambo on 2008-01-26
The simplest way of having fluxbox is
Install from the repos (Synaptic/apt-get/aptitude)

As you have gnome you should find fluxbox as an option when you login, under sessions.
Again, as you have gnome, gdm should take care of your display i.e. you don't need to bother with xdm.

---

### Post by adn258 on 2008-01-26
> **vambo said:**
> The simplest way of having fluxbox is
Install from the repos (Synaptic/apt-get/aptitude)

As you have gnome you should find fluxbox as an option when you login, under sessions.
Again, as you have gnome, gdm should take care of your display i.e. you don't need to bother with xdm.

Okay I just logged in with GNOME as the session and nothing happend the desktop looks the same what do i do friends?

---

### Post by vambo on 2008-01-26
When you log in click on sessions. You should see fluxbox listed. Check it (not gnome) and log in - hey presto - fluxbox.

---

### Post by adn258 on 2008-01-26
> **vambo said:**
> When you log in click on sessions. You should see fluxbox listed. Check it (not gnome) and log in - hey presto - fluxbox.

Okay it worked and like I don't know if it's supposed to be this way but there are no icons on the desktop when I log in with fluxbox?  What should I do?

---

### Post by vambo on 2008-01-26
The best thing is to have a good read of the documentation, which you can find here: [http://fluxbox.sourceforge.net/]("http://fluxbox.sourceforge.net/")

Yes, it is meant to be that way (no icons etc). You will find a task bar, with nothing there!

It might be best to point out that flux is configured solely through text files - no gui's
It's a window manager you really have to work at to get the best from it. It is IMO worth it.

---

### Post by yabbadabbadont on 2008-01-26
You might find RedSquirrel's tutorial interesting too:

[http://www.ubuntuforums.org/showthread.php?t=371144](http://www.ubuntuforums.org/showthread.php?t=371144)

---

### Post by adn258 on 2008-01-26
thanks everyone :)

---

### Post by adn258 on 2008-01-26
> **adn258 said:**
> thanks everyone :)

but I just got to ask so like GNOME is the standard desktop then?  Like when I use that one nothing happens different?

---

