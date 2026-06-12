---
title: "Mouse cursor is hidden while it's hover desktop area"
date: 2022-10-31
forum: General Help
---

### Post by vladkorobeinikov on 2022-10-31
Hi, all!

I have just upgraded Ubuntu distro from 20.04 -> 22.04 -> 22.10

The problem started to appear only on 22.10

[https://youtu.be/ilp2DfIPY-I](https://youtu.be/ilp2DfIPY-I)


What can I do to solve it?

---

### Post by MAFoElffen on 2022-11-01
The same setting is
```

gsettings get org.gnome.desktop.interface locate-pointer

```
You are wanting it set to true. If false, you can change it to true via
```

gsettings set org.gnome.desktop.interface locate-pointer true

```
Then, the left control key will find the cursor.

---

