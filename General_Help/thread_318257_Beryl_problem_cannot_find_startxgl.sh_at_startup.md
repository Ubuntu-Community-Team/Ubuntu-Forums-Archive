---
title: "Beryl problem: cannot find startxgl.sh at startup"
date: 2006-12-13
forum: General Help
---

### Post by raul_ on 2006-12-13
So i followed the guide.

Created a script called startxgl.sh in /usr/local/bin/ and a new session entry in file /usr/share/xsessions/xgl.desktop :

```

raul@raul:~$ cat /usr/share/xsessions/xgl.desktop
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application

```

But when i choose the Xgl session in the login screen, it gives me a message that it couldn't find the file /usr/local/bin/startxgl.sh

and it obviously doesn't start.

And my system often freezes when i log out, i don't know if this is related to beryl install

PS: just to prove that my file exists 

```

cat /usr/local/bin/startxgl.sh
#!/bin/sh
#Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
#sleep 4  
#export DISPLAY=:1 
#exec /etc/X11/Xsession

#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:1 
exec gnome-session

```

---

### Post by dgath on 2007-08-02
Bump as I have the same problem.  File not found error, but yes... I have the file.

I'm trying to install Beryl using this guide
[http://64.233.167.104/search?q=cache:56KVWX0FmlwJ:wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL+ubuntu+install+beryl&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a](http://64.233.167.104/search?q=cache:56KVWX0FmlwJ:wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL+ubuntu+install+beryl&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a)

---

### Post by emodro on 2007-09-10
in the console type this
sudo nautilus

go to file system, go to usr/local/bin 
right click on startxgl.sh 
and select the permissions tab then select allow executing file as program. close 
ctrl+alt+backspace login under xgl

---

