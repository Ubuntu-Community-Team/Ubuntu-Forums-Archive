---
title: "Qt-moc not found"
date: 2006-10-22
forum: General Help
---

### Post by raul_ on 2006-10-22
I'm trying to compile qtella but i get this error:

```

Qt's moc not found! If you have installed Qt in an
unusual place, please use the "--with-qt-moc=" option

```

i did a locate on qt-mt and this was the output
```

/Desktop/qtella-0.6.5$ locate qt-mt
/usr/share/qt3/lib/libqt-mt.so.3.3
/usr/share/qt3/lib/libqt-mt.so.3
/usr/lib/libqt-mt.so.3
/usr/lib/libqt-mt.so.3.3
/usr/lib/libqt-mt.so.3.3.6

```

so i guess i have it installed. I didn't get the syntax of the "--with-qt-moc=" option. I tried putting the directory, the file, but i get the same error

---

### Post by lloyd_b on 2006-10-22
Have you installed the package "qt3-dev-tools"?  That's the package that contains "moc"

Also - are you aware that Qtella is a dead project?  AFAIK, there hasn't been  any active development on it in well over a year.

Lloyd B.

---

### Post by raul_ on 2006-10-22
Now i get the "can't find qt3 header files" error. But those are definitly installed :P the thing is, i don't like frostwire. I just want a simple gnutella client (gtk didn't work for me) and qtella seems cool

---

### Post by lloyd_b on 2006-10-22
As for not finding the QT headers:  There is an option for the "configure" script.  It is something like "-with-qt-dirs=".  Just run "configure" with "-with-qt-dirs=/usr/include/qt3".  "configure" should have given you a reference to the exact command.

I agree with you on FrostWire/LimeWire - I use an older laptop (P3-500), and I don't have the CPU power for Java based apps like those.  I'm using Gtk-Gnutella, which has a few problems, but it's still under active development, so the problems *are* getting fixed.

Lloyd B.

---

### Post by raul_ on 2006-10-23
I had fixed the headers problem but thanks anyway :) I'll continue my quest in order to find a good gnutella client 8)

---

