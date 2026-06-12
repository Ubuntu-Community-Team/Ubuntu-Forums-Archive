---
title: "Clock Skins??"
date: 2008-03-09
forum: General Help
---

### Post by Aaron_Griffiths_92 on 2008-03-09
I recently downloaded some clock skins and no idea how to apply them, anyone?

---

### Post by raul_ on 2008-03-09
Clock skins? What clock?

---

### Post by Aaron_Griffiths_92 on 2008-03-09
cairo clock

---

### Post by raul_ on 2008-03-09
Extract the files to /usr/share/cairo-clock/themes

---

### Post by Aaron_Griffiths_92 on 2008-03-09
"you do not have permission to write to this folder"   ??? now what?

---

### Post by raul_ on 2008-03-09
Well, you have to do it with root access. Just extract them to your Desktop and then

```

cd ~/Desktop
sudo mv <folder you extracted> /usr/share/cairo-clock/themes

```

---

### Post by Aaron_Griffiths_92 on 2008-03-09
no such folder or directory

---

### Post by Aaron_Griffiths_92 on 2008-03-09
aaron@aaron-desktop:~$ sudo mv <folder you extracted> /usr/share/cairo-clock/themesDebianEmerald
bash: folder: No such file or directory
aaron@aaron-desktop:~$ sudo mv <DebianEmerald> /usr/share/cairo-clock/themes
bash: DebianEmerald: No such file or directory
aaron@aaron-desktop:~$ sudo mv <DebianClassic> /usr/share/cairo-clock/themes
bash: DebianClassic: No such file or directory
aaron@aaron-desktop:~$ sudo mv DebianClassic /usr/share/cairo-clock/themes
[sudo] password for aaron:
mv: cannot stat `DebianClassic': No such file or directory
aaron@aaron-desktop:~$

---

### Post by raul_ on 2008-03-09
Post the contents of

cd ~/Desktop
ls

please

---

### Post by Aaron_Griffiths_92 on 2008-03-09
aaron@aaron-desktop:~$ cd ~/Desktop
aaron@aaron-desktop:~/Desktop$ 
aaron@aaron-desktop:~/Desktop$ cd ~/Desktop
aaron@aaron-desktop:~/Desktop$ cd ~/Desktop
aaron@aaron-desktop:~/Desktop$ ls
62914-Debian-Clocks.tar.gz             DebianClassic  DebianEmerald
cairo-clock_0.3.2-1_amd64.deb.sha1sum  DebianDark     GrayDark-Ice.emerald
aaron@aaron-desktop:~/Desktop$

---

### Post by raul_ on 2008-03-09
sudo mv DebianEmerald/ /usr/share/cairo-clock/themes

doesn't work?

---

### Post by Aaron_Griffiths_92 on 2008-03-09
aaron@aaron-desktop:~$ sudo mv DebianEmerald/ /usr/share/cairo-clock/themes
[sudo] password for aaron:
mv: cannot stat `DebianEmerald/': No such file or directory
aaron@aaron-desktop:~$

---

### Post by raul_ on 2008-03-09
Dude, you didn't "cd Desktop" :P you're on the wrong directory.

You know what, just do this, it's easier

sudo nautilus /usr/share/cairo-clock/themes

and then drag&drop the folders there

---

