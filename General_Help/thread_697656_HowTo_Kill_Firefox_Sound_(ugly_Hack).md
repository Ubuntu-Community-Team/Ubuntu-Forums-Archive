---
title: "HowTo: Kill Firefox Sound (ugly Hack)"
date: 2008-02-15
forum: General Help
---

### Post by SpaceTeddy on 2008-02-15
OK Folks,

first off - i am going to tell you how to disable sounds in an application - firefox is just an example here. But  - please -  bear in mind that this is not a good way to do it, and it is most definetly not the best...

Why would i want to not have sounds in Firefox ? Sometimes i like to play Flashgames or visit sites that have background sounds which are, mildly said, annoying. Also, with pages like that i cannot listen to my own music.
Even worse, sometimes one finds himself in places where a screaming laptop is not the best thing to have around... (don't you just love noisy computers in libraries ?)

So, again, this is NOT a good way to do, but it is a way of shutting an application up (yes, an application, not the entire computer !!!).

**The shortform of how to do it is - you run firefox as a different user who is not in the audio group, thus having no access to anything that is sound related...**

and now the step by step instructions how to set it up
[SIZE="4"]
1.) create a new user[/SIZE]
This user will be the one which firefox will be run under. I called mine "silent", but the name really does not matter. 

- Open the Usermanagement 
> System -> Properties -> User and Groups
(in German it is System -> Systemeinstellungen -> Benutzer und Gruppen) 
- Add a new User
Here, put in whatever you like - the only thing you really need to remeber is the username. the rest does not matter, you don't even need the password (set it to something random and forget about it. You can always reset it with this tool if you are ever in need of it)
**The most Imporant thing is the Profile - you MUST select unpriviledged there.**
Once everything is set, press ok and the user will be created

[SIZE="4"]2.) grant the new user access to your screen[/SIZE]
This is something you do not want to do every time you boot, so i will set it up directly in the session upon loading. Please be reminded that i am not entirely sure if this is a safe mode to allow access to your screen.. if it is not i would like to know how to do it safely
> System-> Settings -> Session
(in Germand it is System-> Einstellungen-> Sitzungen

Again press the Add button. there should be three fields comming up
Name and Description can be chosen by you, (mine are Name: allowUserSilent and Description: allow user Silent to run Programs on my xserver)
The important thing is that you put in the command right... which is
> xhost +local:silent
NOTE: if you did not use the username silent, then you must change the silent here to the appropriate username. Also the changes here don't take effect immediately. you Either need to relogin or reboot (or run the command in a termal) to acctually allow the new user to access your screen.
[SIZE="4"]
3.) create a start button for firefox which will run in silent mode[/SIZE]
I start everything from the Top gnome panel - so i will tell you how to put a started there (feel free to add other ways to start it)
first, create a starter for the gnome panel by chooseing firefox from the applications menu and right-clicking on it. In the appearing Menu, select "add to panel" (or add to desktop, which ever you like)
Once the new starter is there, rightclick on it, and choose properties...
To acctually be able to run something in silent mode, you will need to add 
> gksu -u silent
in front of the command specifed in the starter. Press OK afterwards.

Example: firefox has the starting command *firefox %u*
Edit this to read *gksu -u silent firefox %u*

now, when you run that new starter, you will be asked for your password - this is normal and does NOT mean that you are running the application as root - you are acctually running as an even less priviledged user. 
Also Note that you will not have access to your files (so downloading files will be a little... tricky)

but that is something for another day... 
I hope this is usefull to someone... and if i did any bad mistakes here, please correct me :)

---

