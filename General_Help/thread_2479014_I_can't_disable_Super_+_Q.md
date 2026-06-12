---
title: "I can't disable Super + Q"
date: 2022-09-12
forum: General Help
---

### Post by silent90s on 2022-09-12
Hi everyone. I'm running Ubuntu and recently installed Pop!_OS tiling shell, on both my laptop and my main computer. 

In my laptop I haven't had any problem disabling Super + Q, which was previously bind by Dash to Dock, I just had to execute the following command: 
```
gsettings set org.gnome.shell.extensions.dash-to-dock hot-keys false
```

But in my computer the terminal returns this message: 

[I]No such schema &#8220;org.gnome.shell.extensions.dash-to-dock&#8221;

[/I]Which doesn't make sense because I've been using DTD for a long time.

I've also tried modifying this XML file, and deleting the reference to Super + Q but I have not obtained any result, even I've rebooted the computer.

[I]~/.local/share/gnome-shell/extensions/dash-to-dock@micxgx.gmail.com/schemas/org.gnome.shell.extensions.dash-to-dock.gschema.xml

[/I]Thank you very much!

---

### Post by vanadium on 2022-09-12
You do not provide any information on your current version, but in 22.04, you can remove the default Super+q binding with
```

gsettings set org.gnome.shell.extensions.dash-to-dock shortcut "['']"

```

---

### Post by silent90s on 2022-09-12
Sorry. I'm using 20.04. Also have tried the command you told and got the same message :(

[I]**No such schema “org.gnome.shell.extensions.dash-to-dock”**
[/I]

---

### Post by vanadium on 2022-09-12
You marked the thread as solved, but it is not solved? If yes, then please share your solution. Users coming to the forum expect to find a solution here. Else, please remove the mark "solved". Something else must be consuming your Super+q. If you tell us what happens if you hit Super+Q, that might be of help.

---

### Post by silent90s on 2022-09-12
Sorry. I don't know when I marked the thread as solved, I'm still having the same problem. How can I change it?

---

### Post by vanadium on 2022-09-15
If you tell us what happens if you hit Super+Q, that might be of help.

Strange though that the dconf key is not there if you are using the Ubuntu desktop. The Ubuntu Dock is a fork of Dash to Dock and uses the same settings.

---

