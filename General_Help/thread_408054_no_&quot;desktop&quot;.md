---
title: "no &quot;desktop&quot;"
date: 2007-04-12
forum: General Help
---

### Post by dbbolton on 2007-04-12
when i log in, my wallpaper is gone, and i can't right-click on the desktop. when i go to System > Preferences > Desktop Background and choose it, it re-appears. however, i still can't right-click the desktop. also, i tried to drag a file from ~ to the desktop, but it didn't go.

any idea about what's going on ?

---

### Post by neoaddict on 2007-04-12
Is nautilus running when your desktop is messed up?

---

### Post by dbbolton on 2007-04-12
yeah, that's how i tried to drag a file from my home folder to the desktop.

---

### Post by neoaddict on 2007-04-13
Open up Config Editor (gconf-editor), and go to:

/apps/nautilus/preferences

Is show_desktop checked?

When you run the command nautilus in Terminal, does your desktop reappear?  (not sure if you accidentally ran the --no-desktop option)

---

### Post by dbbolton on 2007-04-13
"show_desktop" is checked.

i ran nautilus from the terminal, and the desktop worked. so, do i need to add it to my startup programs ?

---

### Post by dbbolton on 2007-04-13
ok i think i figured this out.

in System > Prefs > Session, i had checked "Automatically save changes to session." whenever i logged in, my home folder was opening up. so, i deleted an entry "nautilus /home/daniel/whatever" from the current session. after logging out, nautilus wasn't starting up automatically anymore. so, i simply needed to launch nautilus from the terminal and log out. this fixed the issue. thanks for your help !

---

### Post by Ubris on 2007-05-18
I had this condition, too. My desktop icons were also missing, which dbbolton may have just forgotten to mention.

I actually found this thread after executing the suggested solution to "[Feisty desktop and panel problem]("http://ubuntuforums.org/showthread.php?t=441925")" (deleting ~/.gnome2/session). That also sorts this problem out.

I'll add a few points to the [process described in that thread]("http://ubuntuforums.org/showthread.php?t=441925#td_post_2654193"):
[LIST]no need to use sudo to delete the session file[/LIST]
[LIST]no need to reboot, just restarting the GNOME session was enough[/LIST]
[LIST]thanks to [fable]("http://ubuntuforums.org/member.php?u=44531") for posting the solution[/LIST]

---

### Post by dbbolton on 2007-05-18
> **Ubris said:**
> I had this condition, too. My desktop icons were also missing, which dbbolton may have just forgotten to mention.

I actually found this thread after executing the suggested solution to "[Feisty desktop and panel problem]("http://ubuntuforums.org/showthread.php?t=441925")" (deleting ~/.gnome2/session). That also sorts this problem out.

I'll add a few points to the [process described in that thread]("http://ubuntuforums.org/showthread.php?t=441925#td_post_2654193"):
[LIST]no need to use sudo to delete the session file[/LIST]
[LIST]no need to reboot, just restarting the GNOME session was enough[/LIST]
[LIST]thanks to [fable]("http://ubuntuforums.org/member.php?u=44531") for posting the solution[/LIST]
well, i didn't forget to mention it. i just couldn't have known since i don't have any. :)

---

### Post by Ubris on 2007-05-19
> well, i didn't forget to mention it. i just couldn't have known since i don't have any. 

I find that most … irregular … :rolleyes:

---

