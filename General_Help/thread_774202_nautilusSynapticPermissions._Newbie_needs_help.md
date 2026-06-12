---
title: "nautilus/Synaptic/Permissions. Newbie needs help"
date: 2008-04-29
forum: General Help
---

### Post by DaleNewton on 2008-04-29
Hi,

Sorry for being clueless. I am new to this. I am up for a challenge though, and Im feeling the Linux vibe so I want to learn how to use my Ubuntu.

Basically, I think Ive dont something bad. I cant open Synaptic PAckage manager anymore. Whenerv I try it (graphically),  it says: 

E: ERROR: could not create configuration directory /home/root/.synaptic - mkdir (2 No such file or directory)

I am now using a user called 'dale', which I have given admin rights(the graphical way). I tried uninstalling and reinstalling Synaptic using the command line. 

Since then I have been able to get it to run, using the terminal. But, whenevr I just run it without sudo, it says 


"Starting without administrative privileges
You will not be able to apply any any changes. But you can still export the marked changes or create a download script for them."


If I try to run it in the terminal using sudo synaptic, I get the same message as before

"E: ERROR: could not create configuration directory /home/root/.synaptic - mkdir (2 No such file or directory)"

I looked on the boards and tried a few things.  When I try running nautilus, by typing sudo nautilus, or gksudo nautilus,nothing happens - Nautilus doesnt open. 

When I enter 'gksudo gedit' in the terminal nothing happens.

When i enter "sudo gedit synaptic" in the terminal, I get this:

(gedit:7731): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: No such file or directory
Could not create per-user gnome configuration directory `/home/root/.gnome2/': No such file or directory
dale@ubuntu:~$ 

PLease help!  DOnt know where to go from here and will probably make it worse.

Im using Ubuntu Ubuntu 8.04 hardy Heron.

Thanks.

---

### Post by oldos2er on 2008-04-29
Did you try to create a root (admin) account? Wondering why there is a user named "root" under /home.

 If you've messed up permissions, the easiest thing to do would be to reinstall Ubuntu.

---

### Post by DaleNewton on 2008-04-29
Hi,

No I didnt create a root account.

There was an account called OEM when I got the computer.  I wsa told to run a program called 'Prepare to ship to end user' whchi was on the desktop when I got it, because I didnt know the default password.  

After that I got an icon at the top of the screen saying 'configuring OEM account..."  It stayed there for ages.

I didnt delete the OEM account at any point, unless I did it without knowing it, but now the OEM account has gone.

ALso strting getting these problems with SYnaptic after an update started, but crashed half way through becasue I lost the WIFI connection.  Dont know if thats anything to do with it. I know that Firefox was one of the programs being updated and it gave me trouble until I finished updating it.  ITs ok now.

---

### Post by DaleNewton on 2008-04-30
Hi Ann,

Thanks. The problem was indeed with the path (I Think!).  I changed the path for the root account from home/root/, to /root/, using the user manager and it works fine now.

Dale.

---

