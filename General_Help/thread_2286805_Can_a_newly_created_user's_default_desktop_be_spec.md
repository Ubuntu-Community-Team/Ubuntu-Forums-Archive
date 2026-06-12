---
title: "Can a newly created user's default desktop be specified"
date: 2015-07-14
forum: General Help
---

### Post by Hal_King on 2015-07-14
I'm in the process of creating a special user with a special window manager and tools directed toward a specific project.
The intent is for the participants to install this new user on their workstation -- several Linux and BSD distributions are planned 
to be supported -- obviously Ubuntu is an important one.

In this kind of situation one must to some degree cater to the lowest common denominator.  So a window manager other than 
Gnome or Unity being used.  The installed package works great in Ubuntu -- provided the user NEVER attempts to run some
of these programs in Unity, etc. -- at which point things tend to lock up -- sometimes to the point of requiring a system reboot.

I was looking for a way that at a minimum would allow the setting of the default window manger for this user -- ideally to
lock this user to only that window manager.

Is this even possible???

I do not have control of the code of all the programs that cause this -- so just going to other options is out.   At the moment
the only option I have is a big warning during install -- but there is no guarantee that the installer and the person running the 
workstation are one in the same -- these workstations will be scattered around the world for different organizations -- scienitific
research.

---

### Post by Hal_King on 2015-07-14
OK found a trival answer that works:

in the top of .xsession place:

if [ ! "`ps -efu $USER |  grep startfluxbox`" ]
then
   exit
fi

So if anyone tries to use anything except (in this case fluxbox) the xsession ends and the user is sent back to the greeter login
This is dependent on the greeter login having to call another known start script or program.

---

