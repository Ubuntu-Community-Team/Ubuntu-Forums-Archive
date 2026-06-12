---
title: "Setting $PATH for custom launcher; terminal, Dmenu"
date: 2014-09-28
forum: General Help
---

### Post by schema2 on 2014-09-28
Using Xubuntu with suckless-tools: 

I am trying to add a custom desktop launcher to the environment so I can launch it from terminal, and launch it from Dmenu. I simply copied the desktop entry into a file in /usr/local/bin. The terminal won't launch it and Dmenu wont list it. What do I need to do so that I can launch custom apps/custom launchers from terminal, and more specifically, from Dmenu? The desktop launcher looks like this:

[Desktop Entry]
Version=1.0
Type=Application
Name=manager 
Comment=
Exec=gksu 'exo-open --launch FileManager'
Icon=catfish
Path=
Terminal=true
StartupNotify=false


My echo $PATH looks like this:

echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

---

### Post by Dennis N on 2014-09-28
You can't launch a .desktop file from the terminal since they are not commands that bash can find and interpret. For example, you can launch **catfish** from the terminal, but not **catfish.desktop**

Bash can't look through the .desktop file and locate the command shown inside.

---

### Post by schema2 on 2014-09-28
Okay, thanks. Could you point me in the right direction then on how to add custom scripts to $PATH so that they can be launched from terminal and bash? I am not really sure what I am looking for.

---

### Post by Dennis N on 2014-09-28
I add the folder **bin** to my home folder and put my own scripts in there. ~/bin is automatically added to $PATH when you login, if it exists. Just make them executable, and if correctly written they should work.

---

### Post by schema2 on 2014-09-28
Thank you!

---

