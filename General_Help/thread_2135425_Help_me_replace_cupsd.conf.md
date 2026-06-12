---
title: "Help me replace cupsd.conf"
date: 2013-04-14
forum: General Help
---

### Post by strange_cathect on 2013-04-14
Hello,

I've been getting system errors involving cupsd.conf. I assume this is the result of some tweak I must have done to cupsd.conf. Can someone help me replace mine with a default version? Or is that not a good idea? Thanks for input...

---

### Post by schragge on 2013-04-14
Can you access the web interface of CUPS at the *[http://localhost:631](http://localhost:631)* address in your browser? It also would be helpful if you show *what* system errors you're getting.

---

### Post by Zill on 2013-04-14
Many Linux applications will generate a new configuration file if there is not an existing one when the application starts and so I suggest you rename the existing configuration file to see if this happens:
```
sudo mv /etc/cups/cupsd.conf /etc/cups/cupsd.conf_old
```

Then reboot the PC and if you take a look at /etc/cups/ you will hopefully see that a new cupsd.conf file has been generated.  Configure this file as required, either through the various GUIs or directly with a text editor.

If a new file has *not* been automatically generated then take a look in the /etc/cups/ directory again and you may find a file called "cupsd.conf.default" which could be copied manually and then renamed as "cupsd.conf":
```
sudo cp /etc/cups/cupsd.conf.default /etc/cups/cupsd.conf
```
Reboot and configure as before.

---

