---
title: "How do I run a script that requires root priveledges at startup?"
date: 2007-01-01
forum: General Help
---

### Post by escape on 2007-01-01
I've written a script that automatically connects my laptop to one of a certain set of wireless networks I am typically by. When I connect to one and later restart and connect to the same one, all is ok-the connection happens automatically. However, when I shutdown, change locations, and boot my computer again in a new one, I have to run the script again. This is extremely annoying as I have to open a terminal, type in the command with sudo, and enter my password. 

I would really like to keep things simple and keep the command for the script in gnome-session-properties; however, if other finangling is needed that's ok too. How can I run this script with root priveledges at startup?d

---

### Post by Ramses de Norre on 2007-01-01
Put it in /etc/rc.local, without sudo or such. It will be executed on every startup then after the other init.d stuff.

---

### Post by bruenig on 2007-01-01
Misread exactly what you were doing. Sorry don't know.

---

### Post by Ramses de Norre on 2007-01-01
That would give you permission to run the script without password but it wont be ran automatically on reboot.. So I wouldn't mess with sudoers for his purpose.

---

### Post by eggdeng on 2007-01-01
> **Ramses de Norre said:**
> Put it in /etc/rc.local, without sudo or such. It will be executed on every startup then after the other init.d stuff.

Right, sudo is not required. Alternatively you can just copy it to /etc/init.d. Either way don't forget to run ```
sudo chmod +x name_of_file
```.

---

### Post by escape on 2007-01-02
Thanks rc.local worked. The file was already executable as I ran it manually each time at startup.

If anyone has a set group of non-WPA wireless networks they connect to, PM me and I can send you the script. You can store any number of wireless networks and passkeys in it with copy paste, and if run in the terminal it tells you what it found and what it will connect to and what the signal strength is.

---

