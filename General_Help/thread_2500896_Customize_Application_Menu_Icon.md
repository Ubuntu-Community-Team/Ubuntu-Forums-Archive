---
title: "Customize Application Menu Icon"
date: 2024-09-15
forum: General Help
---

### Post by chetinho10 on 2024-09-15
[COLOR=#000000]Good afternoon

I want to customize the app menu icon, but when I do, the icon I changed it to looks completely blank, is this normal?

Greetings.[/COLOR]

---

### Post by tea for one on 2024-09-15
If you are using Gnome 46 and Ubuntu 24.04, here we go:-

Place the icon you wish to use in /usr/share/icons (sudo privileges required)
Then you have to find and select the application where you wish to change the icon
Example herewith for GIMP
I downloaded an icon from the internet and renamed it as gimp.png
Then, I moved gimp.png to usr/share/icons
Navigate via terminal to /usr/share/applications
```
cd /usr/share/applications
```
```
sudo nano gimp.desktop
```
Navigate to the line [COLOR="#0000FF"]Icon=gimp[/COLOR]
Change to [COLOR="#0000FF"]Icon=/usr/share/icons/gimp.png[/COLOR]
Ctrl O to save
Ctrl X to exit
Log out and log in

---

### Post by chetinho10 on 2024-09-15
[COLOR=#000000]Good afternoon

I don't want to change the application icon, I try to change the show applications icon (9 points), I managed to change it but it comes out blank.

I remember that in previous versions of Ubuntu you could change it and it would come out with color.

Greetings.[/COLOR]

---

### Post by tea for one on 2024-09-15
Apologies - I misunderstood.

Dash to Panel (gnome extension) has a setting for changing the "Show Applications" icon

---

### Post by chetinho10 on 2024-09-15
> **tea for one said:**
> Apologies - I misunderstood.

Dash to Panel (gnome extension) has a setting for changing the "Show Applications" icon


Hello


The extension has helped me and I have been able to change the icon as I wanted.


Thank you very much, the topic can be closed.


Greetings.

---

### Post by tea for one on 2024-09-15
> **chetinho10 said:**
> The extension has helped me and I have been able to change the icon as I wanted.
Thank you very much, the topic can be closed.
You can close the topic by marking the thread as solved.
It is helpful to other users/searchers.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

