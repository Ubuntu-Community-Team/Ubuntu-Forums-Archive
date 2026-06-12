---
title: "What is the &quot;file:&quot; folder in my home directory?"
date: 2007-10-26
forum: General Help
---

### Post by Meson on 2007-10-26
I'm not sure where it came from or what it's purpose is but I have a folder called file: in my user directory.  It is not hidden and contains the following subdirectory file:/home/user/Desktop/

What is it?

---

### Post by chris_nava on 2007-10-26
"file:...." is a URL reference to files on the local system.  Likely this was created by a program that does not understand  the file: URL syntax when the URL was supplied in a "Save As..." or other such dialog.
It should be safe to delete this folder.

---

### Post by jlacroix on 2007-10-26
It's a bug. It happens every time you create a launcher on your desktop. This bug was reported by me before release however it has yet to be fixed. [https://bugs.launchpad.net/ubuntu/+bug/153451](https://bugs.launchpad.net/ubuntu/+bug/153451)

---

### Post by Weevil on 2007-12-01
Tnx for making this clear! I'm having the same 'problem' here on opensuse 10.3 (GNOME).

---

