---
title: "Firefox and Brave Browser defaults to Thunar when clicking 'Show in Folder'"
date: 2023-02-13
forum: General Help
---

### Post by xanizen on 2023-02-13
I installed 'Thunar' for the sole purpose of mass renaming files, e.g. change underscore to space character.

I've navigated to 'sudo gedit /usr/share/applications/defaults.list'

And ensured, I searched for thunar, and it doesn't appear in the file, also 'inode/directory=org.gnome.Nautilus.desktop'

Secondly, I navigated to 'cd /usr/share/dbus-1/services' and did 'sudo gedit org.freedesktop.FileManager1.service'

There's is are other files present, 
```

org.kde.dolphin.FileManager1.service
org.xfce.FileManager.service
org.xfce.Thunar.FileManager1.service

```

Finally, I looked at the mime file, 'sudo gedit /usr/share/applications/mimeinfo.cache', and removed thunar from the statement.

```

inode/directory=easytag.desktop;org.gnome.Nautilus.desktop;org.gnome.baobab.desktop;org.kde.dolphin.desktop;

```

I was hoping if there's a way to overcome this, to go back to using nautlius as the default, without having to modify each browser's settings/about:config?

I followed the instruction here, [https://askubuntu.com/a/1430542](https://askubuntu.com/a/1430542), and executed 
```

killall Thunar at login
systemctl --user mask thunar

```

And that seems to have solved the problem.

---

### Post by monkeybrain20122 on 2023-02-13
Because your user's settings override the system's. Instead of using sudo to edit system settings you should edit your user's settings (without sudo). The files you should edit are ~/.local/share/applications/mimeinfo.cache and  ~/.local/share/applications/defaults.list.

---

