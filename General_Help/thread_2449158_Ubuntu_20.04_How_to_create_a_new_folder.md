---
title: "Ubuntu 20.04 How to create a new folder"
date: 2020-08-21
forum: General Help
---

### Post by wmrp on 2020-08-21
This must be about the most elementary question asked, but for the life of me I can't figure out how to create a new folder under home>pictures so as to organize pictures. I am working on an urgent project, but new to Ubuntu, and am hoping for a useful and timely tip. Thanks!

---

### Post by sdsurfer on 2020-08-21
See attachment, open file manager and hit the icon.

or command line, cd to the directory you want like
```

cd /home/yourname/Documents

```

```

mkdir new-folder

```

---

### Post by Dennis N on 2020-08-21
In 20.04, Use the 'Options' botton (three lines) in upper right area of Files window. See attachment. In the dialog, the icon on the right is for 'new folder'. Use hover and tooltip to help find it.

---

### Post by ipv on 2020-08-21
you could just right-click the mouse and select **Create Folder**

---

### Post by sdsurfer on 2020-08-25
Unless the directory is full, then it (annoyingly) selects the file/folder closest to your click.

---

### Post by vanadium on 2020-08-27
There are multiple ways, but indeed, in the modern interface, it may be difficult to discover. See different way, using mous, or keyboard, or both, on how you can create folders [here]("https://askubuntu.com/a/1252817/558158").

---

### Post by HermanAB on 2020-08-27
The pictures directory is probably spelled with a capital P. 

Therefore:
$ mkdir ~/Pictures/newfoldername

---

### Post by ActionParsnip on 2020-08-27
If you want spaces then remember to escape them if you use CLI
```

mkdir ~/Pictures/Folder\ Name\ With\ Spaces

```

---

