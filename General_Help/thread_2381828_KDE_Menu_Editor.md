---
title: "KDE Menu Editor"
date: 2018-01-05
forum: General Help
---

### Post by anon_private on 2018-01-05
Hello,

The KDE Menu Editor starts when kubuntu starts. I have checked the Autostart menu and it is not included.

How can I stop the KDE Menu Editor from stating with kubuntu?

Thanks

REF. kubuntu 14.04

---

### Post by Xian on 2018-01-05
Some things to look at:

1. What is in your directory $HOME/config/autostart?

2. Is this an application that can perform a self-autostart?
Check for this in the application settings.

3. An application left running/active in the systemtray will often be restarted at next login.

4. In your Desktop Session settings menu do you have anything checked to restore a previous session?
This same menu should have an input field of applications to exclude from startup.

---

### Post by anon_private on 2018-01-05
Thank you for responding.

$HOME/.config/autostart
contains: docky.desktop

I can't find application settings

Best wishes.

---

### Post by vasa1 on 2018-01-05
[https://askubuntu.com/questions/428805/prevent-kubuntu-from-remembering-previous-session](https://askubuntu.com/questions/428805/prevent-kubuntu-from-remembering-previous-session) of any help?

---

### Post by Xian on 2018-01-05
[SIZE=2]Can you locate the Desktop Session Menu in KDE that appears as below:[/SIZE]



[IMG]https://i.imgur.com/Yn7OcOdl.jpg[/IMG]

---

### Post by vasa1 on 2018-01-05
> **Xian said:**
> Can you locate the Desktop Session Menu in KDE that appears as below:
...
+1. OP may prefer to choose "start with an empty session".

---

### Post by anon_private on 2018-01-06
> **vasa1 said:**
> [https://askubuntu.com/questions/428805/prevent-kubuntu-from-remembering-previous-session](https://askubuntu.com/questions/428805/prevent-kubuntu-from-remembering-previous-session) of any help?

I have the option to restore the session. The point is that the KDE Menu Editor was not open at the time of shutdown, so, it should not be restored.

---

### Post by anon_private on 2018-01-06
> **Xian said:**
> [SIZE=2]Can you locate the Desktop Session Menu in KDE that appears as below:[/SIZE]



[IMG]https://i.imgur.com/Yn7OcOdl.jpg[/IMG]

Mine is set to End Current Session, and Restore Previous Session. I have nothing in the Application to be excluded from sessions.

The point is that the KDE Menu Editor is not open at shutdown, so, it should not be restored.

Best wishes.

---

### Post by Xian on 2018-01-06
If you add "kmenuedit" to the excluded from sessions list does it continue to autostart?

---

### Post by vasa1 on 2018-01-06
What happens if you run, in a terminal,```
pkill kmenuedit
```and then log out? Does it restart when you log in again?

---

### Post by anon_private on 2018-01-06
> **Xian said:**
> If you add "kmenuedit" to the excluded from sessions list does it continue to autostart?

Yes

---

### Post by anon_private on 2018-01-07
> **vasa1 said:**
> What happens if you run, in a terminal,```
pkill kmenuedit
```and then log out? Does it restart when you log in again?

It is still autostarting

---

