---
title: "Screen Terminating"
date: 2015-10-31
forum: General Help
---

### Post by chrisbarnes1992 on 2015-10-31
Hi All, 

A quick question for everyone. I have a Minecraft server and I would like to start the minecraft.jar in a detached screen (Using screen -dmS mc java -Xmx1024M -Xms1024M -jar /srv/mc/minecraft_server.1.8.7.jar nogui) However the screen starts but terminates after a few seconds. 

I am planning to use that command on start up so I do not have to start it by hand on every reboot. 

Hopefully this can apply to other service's as well (Such as syncthing etc).

Can anyone suggest a way to stop it terminating? 

Many Thanks,

---

### Post by Lars Noodén on 2015-10-31
Why not -drS instead of -dmS ?

---

### Post by Lars Noodén on 2015-10-31
Also, screen will terminate when the designated command runs its course.  Maybe it is interpreting -Xmx -Xms and -jar as options for screen and not doing much.  It should be possible to terminate the screen options with a double dash --

```

screen -dmS mc **--** java -Xmx1024M -Xms1024M -jar /srv/mc/minecraft_server.1.8.7.jar nogui

```

---

### Post by chrisbarnes1992 on 2015-10-31
Would it be worth making a script to start the minecraft.jar file and change the command to :

```
screen -dmS mc /srv/mc/startmc.sh
```

This could stop screen seeing the other -'s as it own.

---

### Post by Lars Noodén on 2015-10-31
If that is the problem then putting it into a script should work just as well.

---

### Post by chrisbarnes1992 on 2015-10-31
Ahaha, Putting it in a script has seems to of done the job.

Thanks for putting the idea in my head.

I am guessing it thinks the -jar is a part of screen. Maybe,

So i can now put the command on a start up script somewhere so it starts on system boot up. However i know there is rc.local and the crontab but what is the correct one to put it in?

---

### Post by Lars Noodén on 2015-10-31
> **chrisbarnes1992 said:**
> So i can now put the command on a start up script somewhere so it starts on system boot up. However i know there is rc.local and the crontab but what is the correct one to put it in?

If you put it in rc.local, it will run as root, which is probably not what you want.  But you can preface it with *sudo -u someuser* and have it run as that user. 

If you put it in cron then you can use @reboot to indicate that it should run once at start up.  I think that can go in any user's crontab or else in a special file in /etc/cron.d/

---

### Post by chrisbarnes1992 on 2015-10-31
Thanks for the help,

I was expecting a bigger head ache with setting it up but its running happily now (First time ever adding stuff to rc.local).

From now on I am going to make a basic script to start the screen in all future uses etc.

Thanks,

---

