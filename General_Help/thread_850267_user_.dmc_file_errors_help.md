---
title: "user .dmc file errors help"
date: 2008-07-05
forum: General Help
---

### Post by wolfmanz51 on 2008-07-05
Im having a problem with my Ubuntu when I try to login it says that my x session settings could not be saved because of a ownership conflict with some .dmc file and it logs me out. I need help I'm going to go back and write down the exact message but if anyone knows this problem and could help I would appreciate it

---

### Post by sisco311 on 2008-07-05
Press Ctrl+Alt+F2 and log in, then type:
```
sudo chown -R your_username:your_username /home/your_home_folder[FONT=monospace]
[/FONT]chmod 0644 /home/your_username/.dmrc
```replace your_username with your login name and your_home_folder with you home
folder(by default your login name)
Press Ctrl+Alt F7 to go back to the graphical login screen.

---

### Post by wolfmanz51 on 2008-07-05
when I login under my username it says I don't have permission to use python/usr/bin when I try the command line you gave me

---

### Post by drs305 on 2008-07-05
Try booting into the recovery mode and choose the 'root' option. When you get to the command line, run the commands below. Change 'username' to your username (log-in name):

```

chmod 644 /home/*username*/.dmrc
chown *username:* /home/*username*/.dmrc
chmod 755 /home/*username*
chown *username:* /home/*username*
shutdown -r now

```

---

### Post by sisco311 on 2008-07-05
Try to boot in Recovery Mode and execute the commands
from the root shell.

---

