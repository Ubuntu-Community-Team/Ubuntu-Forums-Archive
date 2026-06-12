---
title: "Edit a file"
date: 2006-12-03
forum: General Help
---

### Post by arthursc on 2006-12-03
I need to add the following line to an options file in /etc/modprobe.d/
# fix intel sound
options snd_hda_intel model=3stack

but whatever I do it is read only when opened. how do I edit a file in file browser with sudo root rights?

thanks

---

### Post by dbott67 on 2006-12-03
```
gksudo gedit /path/to/file
```
or 
```
sudo nano /path/to/file
```

-Dave

---

### Post by Ramses de Norre on 2006-12-03
Pasting this in terminal will do:
```
echo "options snd_hda_intel model=3stack"|sudo tee -a /etc/modprobe.d/filename
```

To get a graphical editor: sudo gedit filename in terminal.

---

### Post by taurus on 2006-12-03
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/modprobe.d/filename
(where filename is the name of the file you want to edit...)
```

---

