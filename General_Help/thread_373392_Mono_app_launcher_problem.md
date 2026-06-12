---
title: "Mono app launcher problem"
date: 2007-03-01
forum: General Help
---

### Post by max69 on 2007-03-01
Hi there.
Sorry if this is a stupid question but I'm a newbie. I wanted to create a launcher for an app I open using mono. So I created a shell script and made it executable and it does work from the command line. But when I want to point the launcher on that file it does not do do anything. I've spent the last two days trying to do it and I'm getting really frustrated :confused: :confused: . What am I doing wrong? Thanks in advance. Max
shell script:
#!/bin/sh
/home/max/mono-1.2.3.1/bin/mono /home/max/MPEG4Modifier.exe

---

### Post by zvacet on 2007-03-01
Open format menus and on the left side choose in witch secion yopu want to put your app.on the right side open new... anmd that will start launcher.
name:your_app
comment:
comand:browse to the place where you put your executable
icone:usr/share/icons or usr/share/pixmaps or something else 
close
if you want launcher on your desktop right click>create launcher
after this move everything is the same as I described above

---

### Post by max69 on 2007-03-01
Hi, thanks for your reply.
Unfortunately this does not solve my problem. I need to create a launcher to launch a MONO application, that means if I wanted to launch it from the terminal I would do:
$ mono myprogam.exe
where myprogam.exe is the name of my progam
That is why I looked around to create a launcher and created the shell script and trying to create a launcher to the shell file. I did this but nothing happens and when I create a launcher to run in Termiinal it does not work either, the terminal appears and close very quickly. I'm lost.

---

