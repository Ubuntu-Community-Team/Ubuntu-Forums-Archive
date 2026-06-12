---
title: "What is it and how do I install it?"
date: 2007-01-23
forum: General Help
---

### Post by ardchoille42 on 2007-01-23
I would like to know what exactly is a file server? Is it just a spare hd or box that you keep files on? Is it an application I can install? I have been using Ubuntu since Warty but never looked into a file server. What is needed to setup a file server?

---

### Post by gh0st on 2007-01-23
That's a difficult question to answer fully but I'll have a go. A file server is basically a place that's used for storage on a network. Depending on how big the network is it can be an individual machine dedicated to the task, a cluster of machines or just an normal office machine that also serves files in addition to other tasks. You don't need a specific type of PC or anything, if you have a hard disk and networking ability that's basically all you need.

Imagine you work in an office with 3 PC's and you all want to have a shared area where you keep company files, this should be accessible to users on all machines on the local network. You could share calenders, spreadsheets, documents, any type of file really. All users could use one spreadsheet located somewhere on the file server to store expenses for example, it's better to keep all that in one definitive file rather than have lots of conflicting copies.

In Linux the software you would mostly use to facilitate this is called Samba. Samba allows Linux to share files with Windows and Apple machines. It's job is basically to sit there and deal with requests for files. As I said it doesn't have to be on a dedicated physical machine though, you could have one PC that is a web server, file server and print server if you wanted. It depends what kind of demand you have.

I hope that clears it up a bit. You basically run software to make your machine act as a file server but it doesn't have to be the only thing you use that machine for. You can get network storage devices or NAS boxes that are basically a hard drive with network ports to put it crudely and that would be a dedicated physical file server.

Any Linux PC can be a file server you just need to install and configure Samba. Check out their site for more info or have a look in the networking section of the forum. [http://us1.samba.org/samba/](http://us1.samba.org/samba/)

Hope that helps in some way, it's not the best explanation in the world :-) I'm no networking guru either so people may correct me on some of my explanation.

---

### Post by ardchoille42 on 2007-01-23
> **gh0st said:**
> That's a difficult question to answer fully but I'll have a go. A file server is basically a place that's used for storage on a network. Depending on how big the network is it can be an individual machine dedicated to the task, a cluster of machines or just an normal office machine that also serves files in addition to other tasks. You don't need a specific type of PC or anything, if you have a hard disk and networking ability that's basically all you need.

Imagine you work in an office with 3 PC's and you all want to have a shared area where you keep company files, this should be accessible to users on all machines on the local network. You could share calenders, spreadsheets, documents, any type of file really. All users could use one spreadsheet located somewhere on the file server to store expenses for example, it's better to keep all that in one definitive file rather than have lots of conflicting copies.

In Linux the software you would mostly use to facilitate this is called Samba. Samba allows Linux to share files with Windows and Apple machines. It's job is basically to sit there and deal with requests for files. As I said it doesn't have to be on a dedicated physical machine though, you could have one PC that is a web server, file server and print server if you wanted. It depends what kind of demand you have.

I hope that clears it up a bit. You basically run software to make your machine act as a file server but it doesn't have to be the only thing you use that machine for. You can get network storage devices or NAS boxes that are basically a hard drive with network ports to put it crudely and that would be a dedicated physical file server.

Any Linux PC can be a file server you just need to install and configure Samba. Check out their site for more info or have a look in the networking section of the forum. [http://us1.samba.org/samba/](http://us1.samba.org/samba/)

Hope that helps in some way, it's not the best explanation in the world :-) I'm no networking guru either so people may correct me on some of my explanation.

Thank you for the explanation. Acording to your definition, I already have this. I have /dev/hda1 - which is my Ubuntu system - and /dev/hdb1 - which is used as storage for documents that are requested on the LAN. I have a wiki and a "Files" directory on /dev/hdb1 and they can be accessed from the other 10 machines on the LAN. I guess I had set up a file server without realising it.

---

### Post by gh0st on 2007-01-24
Yeah it sounds as though your machine is already set up to serve files to the network. If the other machines on the network can access your files then it must already be working. If you found that delivering the files was putting extra strain on your machine at a later time you could set up a separate machine just to store these files and make them available, that's what most people would call a file server but it's not likely to cause a problem with only 10 clients. 

I used to work in a hospital with over 7000 PC's on the network and we needed a rack full of file servers but they were just PC's that we only used as network storage, like a web server is just a PC that delivers web pages, there's nothing special about them in hardware terms really. Server's are usually designed to run more efficiently because they need to be on 24/7 but they're basically just powerful PC's in thinner cases.

At least you don't have to worry about setting up anything extra now, you were doing it all the time without knowing it. You can put your feet up :D

---

