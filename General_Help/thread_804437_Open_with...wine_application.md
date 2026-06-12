---
title: "Open with...wine application???"
date: 2008-05-23
forum: General Help
---

### Post by metaldeath on 2008-05-23
Hi,i have wine with photoshop and autocad installed...

I wonder if it is possible to click for example a dwg file or a jpeg file and open with one of these wine application becase giving the path of the software manually it only opens itself but not the file clicked...

Is there some wine settings to do so???

Hope it's clear :(
Thanks

---

### Post by DachaArh on 2008-05-23
I too would like to know this ....?

---

### Post by atomkarinca on 2008-05-23
Right-click the file and select Properties, Open With > Other Application, select "Use a custom command" and type in the field:

```
wine "/path/to/the/program.exe"
```

/path/to/the/program.exe would your application's location and name.

---

### Post by metaldeath on 2008-05-23
...it doesn't work...autocad starts but with blank drawing

---

### Post by mc4man on 2008-05-23
This is a bit of a longshot but
browse to drive_c and while in it in upper task bar click bookmarks and add drive_c - you'll see it in places as last choice before line (have to see it above line above computer ). Then right click on your file and under properties -> open with _> use custom command -> browse, then choose drive_c -> program files,  ect. edit; then try d.clicking the file

---

### Post by metaldeath on 2008-05-23
Now autocad don't start...:(

---

### Post by vanadium on 2008-05-23
The approach of atomkarinca is the correct one. You will need to check the command line options needed for autocad. In the worst case (quite unlikely), autocad does not support opening files from the command line. Very probably under Windows, files are opened from within the shell using DDE (dynamic data exchange) commands. However, normally applications also provide a possibility to open files through a command line argument. I am not sure whether wine supports DDE.

---

### Post by roderick on 2008-05-23
I tested the Open With using wordpad, and under Kubuntu, this works as expected. So, it may be that AutoCAD doesn't support the command line option (as stated above)

---

### Post by Dusal on 2008-11-04
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine) 

Find "Creating file associations" in the page.

And you can find a lot about using wine there ;)

---

