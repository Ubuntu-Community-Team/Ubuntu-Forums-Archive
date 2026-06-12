---
title: "[SOLVED] How to run VLC script as user, not as root..."
date: 2013-09-18
forum: General Help
---

### Post by hisli2 on 2013-09-18
Hello,

I would like to run a script file existing under /var/bin. Normally each segment of startup.sh script file works when I log into ssh as **user**.

At my first attempt, i put a line into rc.local as shown below:

```
/var/bin/startup.sh &
```

Then I rebooted the pc but VLC did not get started. 

Due to privilege restrictions of VLC program, it works only as user, not root.

I tried to run in crontab but could not be able to handle the issue.

in crontab:

```
30 19 * * * user /var/bin/startup.sh
```

it did not work.

What do you advise me to run VLC automatically when pc is rebooted?


Thanks in advance
Hisli


[COLOR=#0000cd][B]PS: I call visudo and edited the file. I am able to run the script as root.

Thanks[/B][/COLOR]

---

### Post by ajgreeny on 2013-09-18
Is this solved or not? I'm confused.

It is a very bad idea to run an application like VLC as root, so I advise you to stop doing so, if you are really using it that way at the moment.
I am also wondering why you needed to use /etc/rc.local as a place to put the command; why not use the startup-applications in the normal way.  It will be helpful to know exactly what OS you are using and the version of it, as the startup-applications utility, or at least, how you get to it, varies greatly between them
Can you also show us the content of the startup.sh file that you are trying to use, though I don't think that is the way to do what you want.

---

### Post by hisli2 on 2014-06-21
Hello,
Here is the code which I want to convert into bash script:

```
vlc -vvv file.avi --sout '#transcode{vcodec=mp2v,acodec=a52,vb=1024,ab=64,width=640,height=480}:standard{access=http,mux=ts,dst=192.168.0.1:8080}'
```

Thanks
Hisli

---

