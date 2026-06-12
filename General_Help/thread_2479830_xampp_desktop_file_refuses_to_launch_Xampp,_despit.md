---
title: "xampp desktop file refuses to launch Xampp, despite intially being able to do so."
date: 2022-10-09
forum: General Help
---

### Post by xanizen on 2022-10-09
The shortcut is placed in the 'Gnome 3 Application Menu' initially worked, with my only gripe being it opened a new terminal windows despite setting 'Terminal=False'.

```

[Desktop Entry]
Encoding=UTF-8
Name=XAMPP Control Panel
Comment=Start and Stop XAMPP
Exec=sudo /opt/lampp/manager-linux-x64.run
Icon=/opt/lampp/htdocs/favicon.ico
Categories=Application
Type=Application
Terminal=false
```

I explicitly set executive privelege to kaign, and it still refuses to launch the application.

```

sudo setfacl -m u:kaign:rwx /usr/share/applications/xampp.desktop

kaign@kaign:~$ ls -l /usr/share/applications/xampp.desktop
-rwxrwxr-x+ 1 root root 218 Oct  8 17:49 /usr/share/applications/xampp.desktop

kaign@kaign:~$ ls -l /opt/lampp/manager-linux-x64.run
-rwx--x--x 1 root root 3361003 Jun 15 12:07 /opt/lampp/manager-linux-x64.run
kaign@kaign:~$ 

```

sudo /opt/lampp/manager-linux-x64.run works

I recall the issue starting after I installed MariaDB, but again, I can launch xamppp from the terminal.

---

