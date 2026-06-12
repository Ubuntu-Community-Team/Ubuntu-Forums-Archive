---
title: "auto start or enable service on boot up permanently in ubuntu 16.04 lts server"
date: 2017-02-22
forum: General Help
---

### Post by leetskil on 2017-02-22
how to auto start or enable service on next boot up or start up? in ubuntu 16.04 lts
how to start or enable service on the next boot up or start up? in ubuntu 16.04 lts


without doing it manually enable or start services again everytime i start up or boot up the ubuntu 16.04 lts

thank you

---

### Post by stepanboyko on 2017-02-22
to add use
sudo update-rc.d servicename defaults
to remove use
sudo update-rc.d -f servicename remove

---

### Post by RobGoss on 2017-02-22
If I understand you correctly you want specific programs to startup when your system boots correct?

The best way I know is to add them to the **Startup Application**, this will allow each application to resume when your system boots each and every time your system starts up

This might be of use for this process
[https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html)

You can also remove applications you no longer want at startup as well just make sure you fully understand what each application does for your system

---

### Post by leetskil on 2017-03-05
how can i start a service using update-rc.d ? how to start service? 

i am having this error or notification in the cmd-line using the syntax below: "Running in chroot, ignoring request." setup running in ubuntu 16.04 lts server

```


[COLOR=#111111][FONT=Consolas]systemctl [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]start [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]service
[/FONT][/COLOR]

```

---

