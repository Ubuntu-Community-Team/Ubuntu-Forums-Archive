---
title: "I need to start program when ubuntu boots."
date: 2007-02-09
forum: General Help
---

### Post by zoffmann on 2007-02-09
Hello,

I would like to start apache, mysql and other servers when linux boots.

I saw there are direcotories /etc/rc?.d with symlinks for strarting programs when linux boots.

I need som program which creates these startup links for ceratain runlevel, in other words which command do I use for such purpose?

Thanks in advance
:KS

---

### Post by theolster on 2007-02-09
> **zoffmann said:**
> Hello,

I would like to start apache, mysql and other servers when linux boots.

I saw there are direcotories /etc/rc?.d with symlinks for strarting programs when linux boots.

I need som program which creates these startup links for ceratain runlevel, in other words which command do I use for such purpose?

Thanks in advance
:KS
Apache should be started as default - hmmm...?
Try System >> Administration >> Services - in the menu
You can start most services here.

---

### Post by zoffmann on 2007-02-09
There was similar command in Suse, but I forgott the name :(

It works like this

"command" "your program"

then your program is in rc?.d as symlink and it starts when system boots

så I wonder is there something similar in Ubuntu

It was very easy but I have bad memory :confused:

---

### Post by sdide on 2007-02-09
Hey,

I'm not sure what you need.
but the command "ln" can make symbolic links. 

So if you want some script "myscript.sh" to be run at say run level 3 say just after the various cron daemons, (they run at 89, on my machine). 
(be root or sudo for the following)
You could:
*put myscript.sh in /etc/init.d 
*make it executable 
* start it as level 90 on runlevel 3

```
$ mv myscript.sh /etc/init.d
$ chmod 550 /etc/init.d/myscript.sh 
$ cd /etc/rc3.d
$ ln -s /etc/init.d/myscript.sh S90myscipt

```

---

### Post by zoffmann on 2007-02-09
Is there anything more simpler?

Everything in one row.

---

### Post by bikeboy on 2007-02-09
I recommend installing sysv-rc-conf. Once installed you run it in a terminal using ```
 sudo sysv-rc-conf 
```

It allows you to see all services and choose which runlevel you want them started at in a tick-box style. Very easy.

---

### Post by ghandi69_ on 2007-02-09
If your using gnome.... there is a startup programs option in the menu.  Under preferences session I believe?  Just type the command you would use in the terminal to start it and your good to go.

---

