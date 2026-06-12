---
title: "get service to start at boot not login?"
date: 2008-03-10
forum: General Help
---

### Post by android6011 on 2008-03-10
I followed [http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402) to install a vnc server, and it works fine, but on the server if the computer is reboot I have to login to the computer before the vnc server starts, how can I change this?

I also followed [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#SSH](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#SSH) to install an ssh server, but I cant get that to start without doing /etc/init.d/ssh start , how can I get that to start on boot also?

---

### Post by SpaceTeddy on 2008-03-10
i don't know if there is an "easier" way to do this... but i am (unforteunatly ?) used to he very-hands-on-doing-it-yourself-way.

as for the vnc server - you will not be able to start that one before you log in, since i think it needs a running xserver to acctually display something. And i *think* that gdm (the login screen) might not count as that... i am not sure about that one. In any case, you'd just need to replicate what i am about to say about the ssh server and try it. If ssh does not work, i know that xdmcp works...

as for starting things during boot - you'd need to put the start script in your runlevel init directory - this sounds like a lot of work, but it really is only adding a single softlink in a directory...

after you are logged in, check which runlevel you are on with the command runlevel. it should tell you something like **N 2**

the number is the imporant bit here. armed with this number, navigate into the folder /etc/rc2.d where the 2 is corresponding to the number of the runlevel.
in this dir, you will find a whole bunch of links to other files... Also, all (or almost all) entries will be starting with a S and a two digit number.

Everything starting with a capital S will be run at boottime when the computer Enters that runlevel (K is run when the runlevel is left - i.e. reboot or shutdown). the Numer qualifies the order they are started in. the acctual files that get started (again, these are only links !) are all in the directory /etc/init.d. You mist be VERY CAREFUL if you start messing in that folder, since anything going wrong there can render your system useless :(

so, the ssh server is called... ssh :)

with this command, add an entry in your /etc/rc2.d directory to point to the ssh script in the /etc/init.d folder, resulting in the ssh to start at boot-time

```
cd /etc/rc2.d 
sudo ln -s ../init.d/ssh S16ssh
```

(that is the entry that gets automaticially created here on my machine)
the ssh server should start at bootime now :)

hope it works.

---

### Post by android6011 on 2008-03-10
thank you very much for the very detailed reply. now that i can get ssh to start at boot I could always start xserver through that, so im not too worried as far as that goes. thank you for your help

---

### Post by android6011 on 2008-03-10
heh, actually it did make the ssh server autostart, but not until I login :/  , how do i know which runlevel will make it start without logging in? the runlevel command says 2 after ive logged in

---

### Post by SpaceTeddy on 2008-03-10
if you are in runlevel 2, then placing something in /etc/rc2.d will autostart it... or so it should.

if that does not work, there is always /etc/rc.local (a file) which can be used to run usercommands at boot time...

---

### Post by android6011 on 2008-03-10
the computer is on wireless....when does the wireless network connect? after login?? , is there a way to start wireless before that?

---

### Post by SpaceTeddy on 2008-03-10
in standard ubuntu, network is started at boot time, but configuration of the network devices (i.e. getting an ip address and such) is done via network manager AFTER login. To change this, you would need to manually configure your network in the appropriate config files. 

The file which (staticially) configures the network interfaces is /etc/network/interfaces. But i do not know if/how you would configure a wireless card there - never done that before :(

---

