---
title: "su"
date: 2007-02-05
forum: General Help
---

### Post by djhbrown on 2007-02-05
:confused: brand new to ubuntu.  am sure enty thousand others have had the same questions as me but cant find the answers.  
1. why does it need 2 "administrators" who cant do the same things? eg have to login as root do just about anything but cannot access synaptic package manager as root.  and as the user who can, have to sudo everything at a command prompt.
2. having trouble accessing repositories. am behind a firewall proxy server which only allows http traffic.  have set up proxy everywhere i can see ie network proxy preferences, synaptic preferences, firefox preferences.  and still it fails.

short non-jargon answer please.

---

### Post by djhbrown on 2007-02-05
ok i answer my own enquiry! thanks to dr nick..if anyone else has the same trouble, you have to set synaptic to "connect directly" ie tell it a lie, and set preferences-network proxy to be what you need.  that way synaptic wont muck up gnome. no need to sudo or edit etc/whatever.

odd that ubuntu team havent fixed this "feature".

i still dont understand why it wants 2 administrators...found a way around it by giving root permission as the other one to do anything  and then being root all the time, defeating the original intent of protecting idiots like me from themselves but then without root privileges i cant do anything.

please ubuntu team, let root use your lovely interface too by default. command lines - yecch!

---

### Post by Ramses de Norre on 2007-02-05
I'm not sure what exactly your problem is but you might want to read [this](http://wiki.ubuntu.com/RootSudo).

---

### Post by lamego on 2007-02-05
> 
1. why does it need 2 "administrators" who cant do the same things? eg have to login as root do just about anything but cannot access synaptic package manager as root. and as the user who can, have to sudo everything at a command prompt.
You must be confused, you don't need 2 administrators, you only need to have an user which belongs to the admin group, and you need to use that users password whenever an admin task is required (to ensure extra security).
> 2. having trouble accessing repositories. am behind a firewall proxy server which only allows http traffic. have set up proxy everywhere i can see ie network proxy preferences, synaptic preferences, firefox preferences. and still it fails.
You only need to setup the proxy on your synaptic preferences, all the other settings will not affect synaptic in any way.

---

