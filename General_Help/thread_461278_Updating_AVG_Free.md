---
title: "Updating AVG Free"
date: 2007-06-01
forum: General Help
---

### Post by teejay17 on 2007-06-01
How do I update AVG Free? When I click on the update icon, I get the message: "Update process failed. Reason: Sorry, you do not have permission to execute avgupdate."
Does anyone know how I can override this, to get the most recent virus definitions?

---

### Post by teejay17 on 2007-06-01
Actually, it also looks like I need permission to do a scan. Anyone know?

---

### Post by teejay17 on 2007-06-01
bump

---

### Post by merlinus on 2007-06-01
sudo avgupdate -o

-merlin

---

### Post by teejay17 on 2007-06-01
> **merlinus said:**
> sudo avgupdate -o

-merlin
Thanks. Works great. 
Now I'm getting one error when I scan: it tells me that AVG doesn't have permission to scan "/", and that access is denied. How do I scan "/"?

---

### Post by merlinus on 2007-06-01
Check permissions in /opt/grisoft

-merlin

---

### Post by teejay17 on 2007-06-02
> **merlinus said:**
> Check permissions in /opt/grisoft

-merlin
Is it possible to change permissions?

---

### Post by teejay17 on 2007-06-04
> **merlinus said:**
> Check permissions in /opt/grisoft

-merlin
I went into opt/grisoft and right-clicked the icon, found "Permissions" but everything is grayed out. I cannot change anything because I don't have super user privileges. 
How do I get privileges? I'm running into privilege problems trying to give myself privileges. :confused:

---

### Post by merlinus on 2007-06-04
gksudo nautilus (or gksudo thunar) will give you root rights.

I have been able to change lots of permissions this way.

Alternatively, add yourself to the owner group.

hth...

-merlin

---

### Post by teejay17 on 2007-06-04
> **merlinus said:**
> gksudo nautilus (or gksudo thunar) will give you root rights.

I have been able to change lots of permissions this way.

Alternatively, add yourself to the owner group.

hth...

-merlin
hmmm...Neither of these seemed to work. I still cannot do an update graphically, nor can I do a virus check on "/". 
I changed my status to "sudo", and still nothing.

---

### Post by netstat on 2007-06-12
.......after installation create a new launcher with "sudo" permissions... 

3. Now remove the default launcher created, using the command below:
sudo rm -r /usr/share/applications/avggui.desktop

4. Create a new launcher. Type
sudo gedit /usr/share/applications/avg.desktop

Copy and paste the following lines:

[Desktop Entry]
Name=AVG Antivirus
Comment=Antivirus
Exec=gksudo avggui &
Icon=/opt/grisoft/avggui/prog/pixmaps/avgico_big.png
Terminal=false
Type=Application
Categories=Application;System;

Reference from: 
[http://www.blog.arun-prabha.com/2007/06/05/how-to-install-avg-anti-virus-in-ubuntu/](http://www.blog.arun-prabha.com/2007/06/05/how-to-install-avg-anti-virus-in-ubuntu/)

---

### Post by nutz on 2007-06-14
The above direction to create the launcher with sudo permissions also moves the launcher to the system tools tab. Originally it was in my accessories tab.

---

### Post by CautionaryX on 2007-06-15
or you could just type the following into a terminal:

sudo avggui

---

### Post by teejay17 on 2007-06-19
> **CautionaryX said:**
> or you could just type the following into a terminal:

sudo avggui
Wow, I never thought of that. I guess that gives you access to the AVG gui with full permission, from the terminal?

---

### Post by nutz on 2007-06-19
lol, yup.

---

### Post by StefanPieter on 2008-05-07
That Worked well for me...
Thanks

---

