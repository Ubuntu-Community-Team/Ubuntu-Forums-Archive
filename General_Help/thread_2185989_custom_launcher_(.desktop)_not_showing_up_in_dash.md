---
title: "custom launcher (.desktop) not showing up in dash"
date: 2013-11-05
forum: General Help
---

### Post by remy-vand on 2013-11-05
Hi,

I recently upgraded from 12.10 to 13.10

I created some custom launchers for programs, but they do not show up in the ubuntu dash.

.desktop files are stored in: ~/.local/share/applications

```

# cat IntelliJ.desktop
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon=/home/remy/projects/tools/idea-IC-130.1179/bin/idea.png
Name=IntelliJ
Exec=/home/remy/projects/tools/idea-IC-130.1179/bin/idea.sh
```

I also tried placing them in /usr/share/applications but this also doesn't work.

Also, when I double click on the icon, I get an error: 'There was an error launching the application.'

edit: I solved it, I just copied my /projects folder from the backup location to my home folder, and forgot to make the *.sh files executable.
chmod +x did the trick.

---

