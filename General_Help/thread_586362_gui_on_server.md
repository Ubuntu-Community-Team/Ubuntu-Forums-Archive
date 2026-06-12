---
title: "gui on server"
date: 2007-10-22
forum: General Help
---

### Post by kinalas on 2007-10-22
how can i install gui on my ubuntu server

---

### Post by kerry_s on 2007-10-22
you just apt-get the 1 you want.
example:
[B]sudo apt-get install xorg fluxbox
startx[/B]

---

### Post by mahousaru on 2007-10-22
Depends on the use of the server.  I have a dedicated VMware Server and its a bit of a waste to not have a GUI on it and force myself console in when I can work directly on it.  Others might be a media server (I guess they call them HTPC nowadays :p).  In regards to making it more vulnerable, that depends on its exposure to risky factors.  If it is behind a home router, and the server never touches the internet apart from updating then what would the extra vulnerability be?

---

### Post by kerry_s on 2007-10-22
also there are just some fantastic gui based management tools that are just way better than using the console. just face it, there's no reason in this day and age not to use a gui and get things done faster and easier.

---

### Post by mahousaru on 2007-10-22
*sigh*

Even though what you say makes sense, it is pretty worthless advice without analysing the situation first.  Good practice, or any security procedures for that matter depends on what you are securing.  Blindly going through steps a, b, c, etc might not make the resource more secure and if practised without understanding can equal a less secure situation.

IMHO when advising someone about security the first and foremost thing to do is to find out about **their** situation.  Advice not suited to the problem either wastes people's time and resources as they try to implement something that is overkill, or it makes the system less secure.

Lets look at bad password enforcement.  If you cycle your passwords too quickly and enforce a overly long password most users will write them down on a postit note and stick it on their monitor.  See this is a bad implementation of good practice.

---

### Post by Lord_Dicranius on 2007-10-22
"Right!" *voice of Billy Idol from Wedding Singer*

---

### Post by Wharf Rat on 2007-10-22
I can answer some of this as an experienced user and admin.

Years ago I used a CLI on Netware -- no problem for server maintenance.  For user configuration, they provided a client GUI -- loosely using the term for a DOS graphic.

I always thought switching to a GUI for a Windows server was a terrible waste of time and resources.    Today, I have a Nitix server that uses a GUI (again if you want to call it a GUI) that is similar to Webmin.  

I find that for me to learn a new system (Ubuntu) and create a server environment, I need the crutch of a GUI.  Think of it as training wheels.

My desire is to set up a home server.  Nothing special.  Mostly for storage and allow me to play with some HTML/PHP stuff.  It will be behind a router /firewall.  So for internal users - 3 at most, I just want simple and quick to replace my aging Cobalt Qube.

Somewhere I read that another distro has a server side GUI -- I remember where I saw this information.   

So, is there a good GUI for Ubuntu i.e.  Xbuntu / Fluxbox, or should I look elsewhere?

---

### Post by Wharf Rat on 2007-10-22
> these are for server management if you like, desktops are for youtube
??

Do you have a pointer to Ebox?

---

### Post by KCPokes on 2007-10-22
> **LanDan said:**
> true,

but you are late and off topic.

for the second time!!


Not sure that I understand how it is off topic.  Forcing someone to go the route of CLI when it is going to be nothing more then a fileserver, used only on their private network, is unnecessary.  The OP never stated the purpose of the server, which is always a term used very loosely, thus a desktop could be used.  So the response is within the scope of conversation.  That said, I generally agree with you that CLI is still the best suggestion.  A GUI is just doing what you can do CLI, but you actually understand what is taking place when you actually make the changes CLI.  If you grow totally dependent on the GUI do you have any backup plan should the GUI not be available?  

[quote=kerry_s]
in class, there taught the console is option 2 should the gui not function for some reason.
[/quote]

Curious, but what class?  I only ask because if it teaching the high level basics, then fine, but I'd be surprised if any advanced training class for server administration had anything to do with a GUI.  Some servers don't even have graphics cards, rather rely on a frame buffer for emulation, thus X is not an option.  Additionally, if you are working in sector that is housing sensitive data you will become familiar with the DMZ model or 2-tier architectures.  In these cases the servers lie in a DMZ, separated from your by firewalls, thus your chance of getting them to punch a hole(s) for accessing a GUI is not exactly fun.  This is where you fall back to understanding the CLI interface (or you learn to tunnel via SSH).  Using the GUI is not a bad thing, long as you remember that CLI can still be your friend.  :)

Wow, I digressed there.  Anyway, each to their own for desktop environments.  Go lightweight, if you are going to have one at all, or look at web-based management, such as Webmin.  Starting with a GUI is a good place to start, but I'd try to ween myself a bit from relying on it solely.  I would stress that as you go through and set things up, get an understanding of what you did and what files changed, because those times having to boot up in "single user mode" to debug the server boot are going to be far easier if you understand what has taken place.

---

### Post by KCPokes on 2007-10-22
> **LanDan said:**
> fine, and which desktop has the right tool to set up samba? postfix? apache?

is it xubuntu, ubuntu or kubuntu?

For one, those weren't the only options provided by anyone in the thread.  And two, those (samba, apache, and postfix) are specific servers each requiring their own configuration, none of which are easily configurable by any desktop.  There are some interfaces that provide you a rough approach to configuring Apache, but it is rough at best.  Same with Postfix.  Far as Samba goes, there is SWAT, which only needs a web browser to configure.  Point is there are different areas that require different actions.  Perhaps the OP is not comfortable setting up his network via CLI and would rather use something like NetworkManager.  If it is just to get it up and running, what is wrong with using the GUI as long as they understand what was changed and could do it via CLI at a later time?  It all depends on the purpose of the server and how much the user wants to get from it.  People set up stuff all the time without truly understanding what it is that they have.  Why should this be any different, if they so choose?

---

### Post by matthew on 2007-10-22
I'm sorry if things seem a little disjointed here. I just removed a bunch of threads that were going off topic and making it difficult for the original poster to get the help he is looking for. The user in question won't be able to interrupt again. Please, carry on. :)

---

### Post by dbrooke on 2007-10-22
Thank you Matthew!

I am interested as well about any graphical solutions people find to manage their server parts... I just don't have the knowledge depth nor the time right now for CLI...  Hopefully someday.

Donovan

---

### Post by jayson.rowe on 2007-10-22
In responce to the poster who mentioned running a VMware server w/ a gui....
I have a dedicated VMware server as well, running Ubuntu server, and the last thing I wanted was a memory hogging DE on it when that memory could go to the VM's - simply load up to the promt, install VMware - you have to do that from the CLi anyway, then go to another computer, fire up the VMware console, connect to remote host, an viola, it's just like you're running VMware Server at that machine, with none of the GUI overhead on that VMware server...

Just an idea, and something that worked well for me. I use Fiesty on that server since VMware-Server was on the Commercial Repo - just enable that - apt-get update, and apt-get install vmware-server - bam done, simple as that...I've never actually touched that box since...runs like a champ.

---

### Post by kinalas on 2007-10-24
all i want really is to have my browser run on the server.. 

i tried to run startx, then i ask to insert my cd intaller, i did, then ask to reboot, i did but after booting still the gui did not start

---

### Post by jayson.rowe on 2007-10-27
> **kinalas said:**
> all i want really is to have my browser run on the server.. 

i tried to run startx, then i ask to insert my cd intaller, i did, then ask to reboot, i did but after booting still the gui did not start

Keep X off and install lynx

---

### Post by mahalie on 2007-10-30
I'm green too but thought I'd offer some words of encouragement. I couldn't get ubuntu-desktop to load on my LAMP for a while, after an uninstall, update and install again it worked. However, I'm not sure if I simply wasn't waiting long enough after startx before!!!

When you first start the GUI it looks like just a blank screen and a cursor, I thought the install failed, the logon screen started eventually though.

---

### Post by por100pre1 on 2007-10-30
> **kinalas said:**
> all i want really is to have my browser run on the server.. 

i tried to run startx, then i ask to insert my cd intaller, i did, then ask to reboot, i did but after booting still the gui did not start

Please read [this]("http://www.psychocats.net/ubuntu/minimal"). You can also browse from CLI using links2 or lynx as previously suggested:

```
sudo apt-get install links2 lynx
```

---

