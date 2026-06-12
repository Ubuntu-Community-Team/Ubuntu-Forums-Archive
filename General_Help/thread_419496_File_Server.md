---
title: "File Server"
date: 2007-04-23
forum: General Help
---

### Post by meney on 2007-04-23
Greetings everybody,

I am in the works of making a file server on my home network. Now I have never done this before but I am looking for a place to store my large files, so I can free some space on my hard drive. So here come the big questions ;)

What version of Ubuntu should I install, Server or desktop?
Are their any setup guides for creating a home file server with Ubuntu (7.04)?

Idealy this is something that I would be able to remote into from anywhere in the world to access my files (not really sure how to make that tick).

Really I'm just wondering if anyone can give me some guidance and point me in the proper direction :D

Thanks all!

---

### Post by dbmnk on 2007-04-23
not having a clue, but wondered if you've considered a _n_etwork _a_ttached _s_torage device?
then you'll free yourself with the hazzle of maintaining a server. 

probably not that popular to suggest in here, but anyways thats what I'm about to. 

If I had the bucks I'd go with an Infrant Readynas, then you're having raid as well for backups. Just be carefull, though - lots of crap products out there too (e.g. the latest WD NAS)

---

### Post by rich.bradshaw on 2007-04-23
If you are unfamilliar with Linux I'd use the desktop version. The server install doesn't come with a graphical interface by default, so if you aren't that handy with the command line then you won't get far!

I use ssh to access from anywhere.

just sudo apt-get install openssh-server

then you can use something like winscp in windows to connect to your linux computer and use the files. That's the simplest way of doing it. ssh is nice and secure as well. If you want to connect to your computer via the internet then you will need to forward port 22 from your router to your linux computer.

---

### Post by rich.bradshaw on 2007-04-23
Oh - you can install NFS on Ubuntu if you want to make it an NAS. I wouldn't bother though. samba lets you share files with Windows computers using the network places system in Windows. SSH for everything else!

---

