---
title: "Start program based on files mimetype"
date: 2008-05-07
forum: General Help
---

### Post by NormR2 on 2008-05-07
What command/program can I execute in a script to call the application associated with a mimetype/file extension?  Like when you are in a File browser and you "open" a file.
The syntax in a script file would be: <start-app> <a-file>
The coding would be: <start-app> $1

For example, if <a-file> were: Something.html
then <start-app> would start a browser and have it open Something.html

Another example, if <a-file> were: Picture.jpg
then <start-app> would start an image program and have it open Picture.jpg

---

### Post by Vadi on 2008-05-07
replace <start-app> with "gnome-open".

I don't know what is the KDE equivalent though.

---

