---
title: "How to use openssh to content MyPlex from my computer to my tv"
date: 2013-10-12
forum: General Help
---

### Post by Kojak Peg on 2013-10-12
Hi Everyone 
I don't really understand what I'm doing. I'm not a great linux user and if it's in the terminal I'm buggered (and yes I have read up on it, but still no joy). So I've got MyPlex installed on my computer and tv, but I've been having trouble making MyPlex work. My solution was to force it to work by using port forwarding, but I've been told it should work direct from my computer to my tv via a LAN

1. I've installed openssh-client and openssh-server, but I have no idea how to use them and when I do 

> $ cd .ssh
$ ls

it says > known_host 

2. When I try to config ssh

> $ gedit /etc/ssh/sshd_config

it says 

> (gedit:26317): Gtk-WARNING **: Theme parsing error: nautilus.css:31:0: 'sideb' is not a valid property name

then won't let me save the changes

3. When I do 

> $ nm-tool

it says my wlan0 is "connected" but my eth0 is "unavailable" 

4. When I do 

> $ ifconfig

it give my wlan0 inet address and Bcast address, but it does't give an IP address for my eth0

5. And finally when I try to ping my IP address it just goes on endlessly
 
So what am I doing wrong?
How do I connect my wlan0 and my eth0?
How do I make openssh work?
Why isn't MyPlex working properly?

Thanks

---

### Post by GWBouge on 2013-10-12
Plex streams content via [DLNA]("http://en.wikipedia.org/wiki/Digital_Living_Network_Alliance")'s [UPnP]("http://en.wikipedia.org/wiki/Universal_Plug_and_Play") protocol.  ssh is Secure SHell, typically used to connect to another machine to perform terminal commands, such as administering a headless server.  For Plex, ssh could be useful if you wanted hide your Plex server from the outside world, you could tunnel it through a secure connection, but that isn't what you're looking for right now.  The ping command will go on forever until you press Ctrl+C to stop it, or you can limit the count by using the -c option ( ping -c 4 [ip-address] ).  As for wlan0 vs eth0, you should be able to configure and connect to what you want in your network settings (since you used gedit, I'm assuming you're on a desktop machine instead of a server), or just select your wired connection from the drop-down.

But let's forget about those for the moment, and make sure Plex is actually working and discoverable ...

1)  Is Plex running?  Use the following command to find out:

```
sudo service plexmediaserver status
```

If it's not, start it

```
sudo service plexmediaserver start
```

Notice the 'sudo' in those commands?  As a user, you don't have permissions to perform tasks on certain parts of the system - that's why you couldn't save the changes in your ssh config.  You can gain temporary root privileges by using 'sudo'.

2)  Can you access it locally?  Open up a web browser on the machine running Plex and goto the following URL:

```
http://localhost:32400/web
```

It should load up a snazzy little interface that shows your media library.  From here, you can click the wrench icon and configure Plex.

3)  Is your router allowing UPnP?  Access your router (generally by going to '192.168.1.1' in a web browser) and poke around ... it's usually on by default in my experience, but every one is a little different.

4)  Is your TV DLNA capable?  If it's not, you'll need to stream it through another device that can do it, like a game console or HTPC.  Also noteworthy, the streaming device and its media list doesn't always show up immediately, it could take 15 or 30 minutes.

---

### Post by Kojak Peg on 2013-10-13
Hi GWBouge
Thanks for clearing that up for me, I've been gaining a real education lately, as I'm new-ish to linux and brand new to creating LAN and it all helps. I was having trouble with plex, it was either something on my computer stopping plex from working properly (firewall was switched off), or it didn't like zorin os 6. Either way after I removed avant windows manager my system crashed, and I was forced to reinstall. So I took the opertunity of installing ubuntu 12.04 and Plex is working perfectly now

As for gedit, I am on a desktop and I wish I could say that's why I used gedit, but that wouldn't be true. The terminal is still a bit of a mistery and I used gedit because I'd come accross it during my search, with plex playing up I was looking for a fix. I used port forwarding but wanted a better solution, hence my idea to try openssh, but thanks to a combitation of my computer not playing ball and my being a novice I couldn't make head nor tail of it

As for UPnP, I don't know what that is so I'll read up about it now

As for the TV, yes it is DLNA capable

Thanks for all your help and hopefully with all this messing about I'll be an intermidiate in no time, lol

---

