---
title: "/usr/local/qt-3.3/bin/ld: cannot find -lqt-mt"
date: 2008-05-08
forum: General Help
---

### Post by mdt414 on 2008-05-08
I'm trying to install DIANA...but i got this error...what should i do ...???
is that because the QT library...???
i tried to install QT3.3.8
but it dosent work...!!!!


```
/usr/bin/g++ -o ../bin/coserver -O2  main.o  serverInfo.o simpleServer.o clientSocket.o  serverInfo_moc.o simpleServer_moc.o clientSocket_moc.o   -L/home/mdt414/Desktop/metnolocal/lib -lqUtilities -lpuTools -L/usr/lib/qt-3.3/lib -lqt-mt -L/usr/lib -lpthread -ldl -L/usr/X11R6/lib -lGL -L/usr/X11R6/lib -lXinerama -lXft -lXrandr -L/usr/X11R6/lib -lXext -lXt -lX11 -lm 
/usr/local/qt-3.3/bin/ld: cannot find -lqt-mt
collect2: ld returned 1 exit status
make[1]: *** [../bin/coserver] Error 1
make[1]: Leaving directory `/home/mdt414/Desktop/metnolocal/src/coserver/obj'
make: *** [server] Error 2

```

Please Help!!

---

