---
title: "Running VNC Server at Start Up"
date: 2008-01-20
forum: General Help
---

### Post by kyleflan on 2008-01-20
Can anyone give me advice on how to have x11vnc automatically run during start up. I have to manually start the server each time by typing "$ x11vnc -usepw". Is there a way I could have Ubuntu automatically do this when I boot? Or just having it run after I log in would work as well. Any help is appreciated.

Also, on a side note, does anyone know if there is a way to implement a Java viewer on x11vnc like tightvnc? I'm not sure if I used the correct terminology, but basically I'd like to be able to connect to the desktop via a web browser. 

Thanks in Advance,
Kyle

---

### Post by craig1709 on 2008-01-20
To make x11vnc run after you login go to System/Preferences/Sessions/Startup Programs and add your command, "x11vnc -usepw".

If you wanted it to run before you login, I *think* you run the following
```
sudo echo "x11vnc -usepw" > "/etc/init.d/x11vnc.sh"
sudo chmod +x /etc/init.d/x11vnc.sh
sudo ln -s /etc/init.d/x11vnc.sh /etc/rc2.d/S99x11vnc

```

Please correct me if I'm wrong,
-craig1709

---

### Post by krunge on 2008-01-20
> **kyleflan said:**
> Can anyone give me advice on how to have x11vnc automatically run during start up. I have to manually start the server each time by typing "$ x11vnc -usepw". Is there a way I could have Ubuntu automatically do this when I boot? Or just having it run after I log in would work as well. Any help is appreciated.


craig1709's System/Preferences/Sessions/Startup tip is a very good way to have it start up when you log in.

However I don't think his  /etc/init.d/x11vnc.sh idea will work in general for before someone logs in (because the DISPLAY and XAUTHORITY settings will be empty). See these for general info:

[http://www.karlrunge.com/x11vnc/#faq-service]("http://www.karlrunge.com/x11vnc/#faq-service")

[http://www.karlrunge.com/x11vnc/#faq-display-manager]("http://www.karlrunge.com/x11vnc/#faq-display-manager")

And there are quite a few discussions in the forums at this site on the topic.  Maybe search for "x11vnc" and "startup".

I recommend trying the "Xsetup/Default" way described on the above links first, and only try the "inetd" way if you can't get it working.


> 
Also, on a side note, does anyone know if there is a way to implement a Java viewer on x11vnc like tightvnc? I'm not sure if I used the correct terminology, but basically I'd like to be able to connect to the desktop via a web browser. 


x11vnc has this option ```
x11vnc -http
``` that will serve a Java viewer applet on port 5800 (like other vncservers, e.g. [http://vnchost:5800/](http://vnchost:5800/)).  It can also serve up a SSL java viewer (For encrypted https connections, [https://vnchost:5900/](https://vnchost:5900/)).

Sadly, recent Debian repositories have stopped providing x11vnc's  Java viewers because only a patch file is included in the source code.  Hopefully this will be fixed in the next few months.

---

### Post by kyleflan on 2008-01-24
Thank you craig1709 and krunge. I now have it working exactly how I wanted. I appreciate your time.

-Kyle

---

