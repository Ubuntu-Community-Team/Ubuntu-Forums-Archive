---
title: "server in text mode + sometimes X"
date: 2007-04-27
forum: General Help
---

### Post by jmvidalvia on 2007-04-27
Hi, 

I will be setting soon a home Ubuntu-server, and I would need to start the GUI sometimes.
My questions are:
1- Do I install the server version and later I install the Desktop libs?
2- Or I just install the standard Desktop version and I add what may be missing?
3- Is *start X* the right comand to start the GUI?
4- Hoy can I close the X and keep the server in text mode?

Thanks a lot!

---

### Post by madmetal on 2007-04-28
> **jmvidalvia said:**
> Hi, 

I will be setting soon a home Ubuntu-server, and I would need to start the GUI sometimes.
My questions are:
1- Do I install the server version and later I install the Desktop libs?
2- Or I just install the standard Desktop version and I add what may be missing?
3- Is *start X* the right comand to start the GUI?
4- Hoy can I close the X and keep the server in text mode?

Thanks a lot!

1/2- its better to install ubuntu-server and then install gui (gnome or xfce so as not to consume system recources..)

3- startx is the command..

4- (i am not sure but i think kill x) 

hope i helped! :KS

UAResolved.

---

### Post by jmvidalvia on 2007-04-29
Thank you!
What about starting the computer without starting X?
How to configure that?
Thanks!

---

### Post by madmetal on 2007-04-29
> **jmvidalvia said:**
> Thank you!
What about starting the computer without starting X?
How to configure that?
Thanks!

well i am not sure about that..
but since you are preparing a server install then you should also have a look at webmin and you maybe wont use gnome or xcfe...
[http://www.webmin.com/](http://www.webmin.com/)
[http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html](http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html)

---

### Post by jmvidalvia on 2007-04-29
Nice proposal!
I will take a look.
Anyhow, if if works in a browser, I am suposed to have GUI, right?
Or it can be managed from another machine?
Thanks again!

---

### Post by arbulus on 2007-05-06
If you want to boot up without starting X, the easiest way is to install Boot Up Manager

```
sudo apt-get install bum
```

Under the adminstration menu, you'll find the app.  Open it up, and uncheck GDM or Gnome Display Manager.  Each time you boot up after that, you will start with only in CLI.

When you want to start the GUI, you can use 

```
startx
```

or

```
sudo /etc/init.d/gdm start 
``` 

and to shut it down, open a terminal and type

```
sudo /etc/init.d/gdm stop
```

I don't know the kill command for startx.


Webmin will work from a different machine on your LAN.  Once it's insalled, you open up your browers and type in [http://*serverip](http://*serverip)*:10000 substituting "serverip" for your server's IP address, example [http://10.0.1.50:10000](http://10.0.1.50:10000).

---

