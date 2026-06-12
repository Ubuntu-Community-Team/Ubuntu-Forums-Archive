---
title: "Some Ubuntu Implementation Questions"
date: 2008-05-18
forum: General Help
---

### Post by Neodragon90 on 2008-05-18
I've been using Ubuntu in a dual boot config with my windows desktop and I'm kinda familiar with how ubuntu/linux works but I have some questions about a home server I wanna make.

The computer I plan to run this on has two hard drives a 80GB HDD and 160GB HDD

On the 80 GB I want to make 3 partitions: the normal / partition, a /home partition and a swap partiton.

On the 160 GB i want to make a /server partition that will be the main place that has the info I want to share.

Im also planning on using the desktop version and adding the server components because I'm still slightly command line-phobic since windows habits are hard to break.

[LIST=1]
[*]I was wondering if Ubuntu would allow me to make this /server and have it be accessible without needing root privileges to access it all the time.
[*]I also want to know what programs are good for remote access so I can edit my server from  my main desktop without a seperate keyboard monitor and mouse. 
I also want to access it from a friends house as well.  (Im used to Real VNC Free edition for windows) 
Im looking for something with authentication and hopefully sound forwarding as well (even if its only local)
Also local bandwidth shouldn't a problem for all this as it will be set up over a gigabit connection. 
[*]I want to make a file server thats sent over a secure connection and has authentication but also allows certain directories to be publicly available (by publically i mean no user/pass required for those files). I also want this server to have some sort of HTTP access so I can access it through the web browser at my school without the need for a ftp program.
[/LIST]

Thank you all for reading all this, as you can see I know what I'm looking for and I know the best place to find programs accomplish this is (Ubuntu) Linux and its also free.:)

---

### Post by DieB on 2008-05-19
as for your /server-partition, why not making it a /home/YOU/server (while YOU is your username)? That should save you some chown-commands.

otherwise put it to /server and after install run:

sudo chown -R YOU:YOU /server

this will make you the owner for that folder/partition

If you ask me, I would use the server install first, because it sets up some services with installation and after that run:

sudo apt-get update && aptitude install ubuntu-desktop

---

### Post by Neodragon90 on 2008-05-21
Sorry it took so long for me to post but Ive been very busy after that first post but tyvm for your suggestion about the /server partition i was just wondering if /home/server without the YOU would be a user unspecific option in case i get my bro to start using it (he would have his own user).
The reason i wanted to use the desktop version is because I wont need much of the normal server functionally and even if i install server i still don't which programs do what i want them to do.

---

### Post by strabes on 2008-05-21
Usually it's a better idea to mount external partitions in /media because a) they appear on the desktop and b) that's where everything is mounted automatically anyway.

---

### Post by Neodragon90 on 2008-05-21
@ strabes: thanks for the suggestion that's actually a good idea a /media/server folder. This is one of the things I love about Ubuntu forums everyone has a different way of doing things.

---

