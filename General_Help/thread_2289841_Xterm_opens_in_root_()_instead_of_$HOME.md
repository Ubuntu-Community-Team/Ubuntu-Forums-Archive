---
title: "Xterm opens in root (/) instead of $HOME"
date: 2015-08-07
forum: General Help
---

### Post by Michael_Powe on 2015-08-07
Hello,

I created a launcher file, xterm.desktop, that sits on my desktop.  This is just a copy of the global desktop file, with some switches added to the xterm command, like "-bg blue" to change the background color.  It launches and works as expected, with the exception that it opens the xterm in the root directory instead of in my $HOME directory.  Using the default launcher from the launch bar lands me in $HOME.

Why is this happening?

I put this in the .bashrc file, which works around the issue, but why is this necessary?


```

if [ `pwd` = "/" ]; then
    cd $HOME
fi

```

Thanks.

mp

---

### Post by CantankRus on 2015-08-07
Works here if I create the launcher by running....
```
cp /usr/share/applications/debian-xterm.desktop ~/Desktop && chmod +x ~/Desktop/debian-xterm.desktop
```

What is your exec line command in your .desktop file?

---

