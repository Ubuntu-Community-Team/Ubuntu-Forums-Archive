---
title: "how do I remote desktop into my uBuntu?"
date: 2007-05-16
forum: General Help
---

### Post by warlock_handler on 2007-05-16
Hi guys,
I was wondering if there is a way i can remote desktop into my uBuntu home edition, please help me with this.
As of now i dont wanna VNC it.. any in build way??

Also my home setup has a LIVE IP but that goes to my router and from my router I get dynamic local IPs for my windows and uBuntu  machines. 

and now i wanna conenct to my uBuntu machine remotely.. please help

---

### Post by wormser on 2007-05-16
> **warlock_handler said:**
> As of now i dont wanna VNC it.. any in build way??

What do you mean 'any in build way??'.  What OS are you trying to connect from?

You can bind you dynamic ip address to a domain with this [free service]("http://www.dyndns.com/").

Here is a quick run down of what is needed.  I recommend tunneling threw ssh.

Ubuntu box:
System> Preferences> Remote Desktop - Enable it
Install Firestarter and open port 22 for ssh
Open port 22 on your router
Go to dyndns to get a domain name - makes it easier, i think there is a client you can install and if your ip address changes it will update it.

Remote Linux box:
Install a vnc viewer
In terminal:  ssh -L 5900:localhost:5900 yourdomain.dyndns.com
In the vnc viewer:  localhost:5900

The ssh command uses the L switch to bind your port to the remote port.  All traffic then tunnels threw ssh.  If it is an windows box then you will need putty.exe to ssh.

Good luck and if you need help post.

---

### Post by warlock_handler on 2007-05-16
> **wormser said:**
> What do you mean 'any in build way??'.  What OS are you trying to connect from?

You can bind you dynamic ip address to a domain with this [free service]("http://www.dyndns.com/").

Here is a quick run down of what is needed.  I recommend tunneling threw ssh.

Ubuntu box:
System> Preferences> Remote Desktop - Enable it
Install Firestarter and open port 22 for ssh
Open port 22 on your router
Go to dyndns to get a domain name - makes it easier, i think there is a client you can install and if your ip address changes it will update it.

Remote Linux box:
Install a vnc viewer
In terminal:  ssh -L 5900:localhost:5900 yourdomain.dyndns.com
In the vnc viewer:  localhost:5900

The ssh command uses the L switch to bind your port to the remote port.  All traffic then tunnels threw ssh.  If it is an windows box then you will need putty.exe to ssh.

Good luck and if you need help post.

I am at a windows machine at work, I wanna connect to my uBuntu machine which is at home.. and I have LIVE IP... so now do I go with the dyndns method? or is there a better way??

---

### Post by Gegglambi on 2007-05-16
Hi, I'm a ubuntu noob so if this seems like a sand box explanation just yell some crap at me or ignore it =) 

I have an ubuntu server (though running Ubuntu Desktop 6.06) at home in a closet. I connect to it remotely (it doesn't have a monitor attached) internally quite easily with ssh (putty) or vnc (i use realvnc from my windows desktop or my windows laptop and just type 192.168.X.Y:5900). I have set a vnc password in Administration - Remote Desktop in Ubuntu and set it to auto-login upon startup (administration - login window I think). Tadaa. 

From an external place I just ssh or vnc, and get directly to that computer because my router forwards those ports to it's internal ip. I also have a dynamic ip that fortunately never changes. I use my external ip and it works like a charm. If it should start to change, I need to get the dyndns service. 

And a bit about more about my setup and... stuff. 

One problem I have is that I can only get 800x600 resolution with vnc if a monitor isn't attached to the machine when it boots up even though I have tested to change things in xorg.conf. Working on that off and on. 

The things I think are good in ubuntu (compared to windows, which I use quite a lot as I support it in my work as a network monkey (which isn't as cool as a code monkey, but anyway)) are the amount of support from communities and all the guides available. It is almost too easy to install most programs and the computer is stable (until you do something stupid, like typing sudo apt-get remove python, like I tried once). 

The things I don't like is that it can take quite some time to edit config-files (compared to the gui-windows-style I'm used to) and that drives and devices aren't as easy to configure (for me, at least). 

The both good and bad things is the dual-edged sword of "things happening but I don't know why". In windows, a lot of things "just happen". Often it is things you want it to do, but in Ubuntu you need to tell it to do something most of the time. Mounting disks for example. 

Ubuntu noob signing off

---

### Post by wormser on 2007-05-16
> **warlock_handler said:**
> I am at a windows machine at work, I wanna connect to my uBuntu machine which is at home.. and I have LIVE IP... so now do I go with the dyndns method? or is there a better way??

Yes, dyndns is the best method.  You have a dynamic ip not a live one.  With dyndns you will make a subdomain to their site (yourname.them.com).  Then use that address in putty to ssh to your ubuntu box.

To connect from a windows machine download [putty.exe]("http://www.download.com/PuTTY/3000-11138_4-10500630.html?tag=lst-0-1").  Then download a [vnc client]("http://www.realvnc.com/").  Follow the directions in my other post to set up remote desktop, open your firewall and router.

Here is a [guide]("http://docs.cs.byu.edu/docs/sshtunnels/3.php") to tunnel ssh with putty.

The whole set up is pretty easy but there are a lot of little things that can go wrong especially on your first attempt.  Reply if you need more help or get success.

---

### Post by warlock_handler on 2007-05-16
> **wormser said:**
> Yes, dyndns is the best method.  You have a dynamic ip not a live one.  With dyndns you will make a subdomain to their site (yourname.them.com).  Then use that address in putty to ssh to your ubuntu box.

To connect from a windows machine download [putty.exe]("http://www.download.com/PuTTY/3000-11138_4-10500630.html?tag=lst-0-1").  Then download a [vnc client]("http://www.realvnc.com/").  Follow the directions in my other post to set up remote desktop, open your firewall and router.

Here is a [guide]("http://docs.cs.byu.edu/docs/sshtunnels/3.php") to tunnel ssh with putty.

The whole set up is pretty easy but there are a lot of little things that can go wrong especially on your first attempt.  Reply if you need more help or get success.

let me try will tell you what happens.. 

> Yes, dyndns is the best method.  You have a dynamic ip not a live one.

I have a LIVE Static IP.. not a LIVE Dynamic IP.. so my IP really doesn't change

---

### Post by wormser on 2007-05-16
If you have a static ip then there is no need for dyndns unless you want an easier name to remember instead of an ip address.

---

### Post by warlock_handler on 2007-05-16
> **wormser said:**
> If you have a static ip then there is no need for dyndns unless you want an easier name to remember instead of an ip address.

Thats what i was wondering.. when i read a little more on dyndns; anyways i will preferably do it with the IP.. i dont like the idea of saving my home IP anywhere. will let you know what happens...

---

