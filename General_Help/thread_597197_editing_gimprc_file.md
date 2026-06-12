---
title: "editing gimprc file"
date: 2007-10-30
forum: General Help
---

### Post by Dr.Suave on 2007-10-30
Hiya

I get green trails when I use a brush in Gimp - its a problem with my ATI Driver - I cant use firmware as I'm using the ATI 9000.

I found some instructions on how to get rid of the green trail here: [http://bugzilla.gnome.org/show_bug.cgi?id=487670](http://bugzilla.gnome.org/show_bug.cgi?id=487670)

to sum it up:

I have to put the following code into my ~/.gimp-2.4/gimprc file:

```
(show-brush-outline no)
```

But I can't find that file or directory! If I can find the directory I can make th file myself, but I can't seem to find it.

I'm new to Linux, so I can't find my way around, does anyone know where the Gimp files live?

Thanks
Wilf

---

### Post by ccrockett on 2007-11-06
I don't know if you have found the file yet but when you are in Konqueror or Dolphin. Go to View->Show Hidden files. Then go to your home directory /user name/home/ and it should be in there. If you are doing it from the command line do an ls -a command and it will show you all of the directories. In Linux directories starting with period are hidden under normal directory listings.

-Cameron

---

