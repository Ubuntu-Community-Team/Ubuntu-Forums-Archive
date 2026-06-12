---
title: "Multiple cairo-docks (help)"
date: 2008-05-25
forum: General Help
---

### Post by Jesuses Left Leg on 2008-05-25
I have cairo-dock installed and set to run on startup (in xfce running on an ubuntu hardy install) and it works fine but after my computer's been on for a while i find that there are 2 or more instances of cairo-dock running and overlapping each other on the screen. I checked processes and they are in there too so what is happening is it is being run over and over again for some reason. :confused: Help!

---

### Post by RATM_Owns on 2008-05-25
In terminal...
```
sudo killall cario
```
I think that is it. Look in System->Administration->System Monitor under Processes and check. Or just kill the processes from the System Monitor.

---

### Post by signseeker on 2008-05-25
Basically the process is not being ended when you log out - which means that a new process is started when you log back in. 

I'm trying to figure out how to kill processes on logout too - am currently researching the bash.logout script. 

Any thoughts anyone??

---

### Post by Jesuses Left Leg on 2008-05-26
Well I know I can kill the processes using killall but I don't want to kill them all I just want it to stop running new instances of cairo-dock.

Also, @ signseeker - well I just thought that you were wrong about what you said but on closer inspection (lol) I found that I have just logged in and 3 are running, so you are probably right.
Isn't there a logout script that is run when you log out? I mean there's .bash_logout but I think that's also used for when a terminal exits?

EDIT: Well I have edited the /etc/gdm/PostSession/Default file
. I'll post back if this does what I want.

Well this didn't work, would it be feasible for me to put 'killall cario-dock && cairo-dock' as a startup script to get rid of all the extra docks and just end up with one?

---

### Post by signseeker on 2008-05-26
'killall cario-dock && cairo-dock'

sounds good. I might give that a go.

---

