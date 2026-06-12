---
title: "Command Line Streaming"
date: 2007-03-02
forum: General Help
---

### Post by jpcompagnone on 2007-03-02
Hi I was wondering if anybody could assist me. 

I have installed Ubuntu Server 6.10 on my PIII 1 Ghz. 
I would like to know if there is a tutorial or method in which i can trans code divx files in real time, and stream them over the internet/LAN.

Your help is greatly appreciated.

Jp

---

### Post by Paerez on 2007-03-02
I have a bit of an idea. It should be pretty simple to do.

First you write a quick script to convert files to divx. Try googling for "mencoder divx" to find out how to use the command line tool mencoder to convert a file to divx.

Once that is set, you should have a command like this:
./myscript file.avi file_divx.avi

So it will convert the file to the divx file.

Then use sshfs or nfs to mount the directly remotely on the other computer. Then you tell your server to start converting by running the script, and on the remote computer you open the file with totem or mplayer right from the folder.

As long as the server can conver to divx faster than you can watch it, you should be all set.

---

### Post by jpcompagnone on 2007-03-02
Thats Perfect.

Thank you for that, just one other question.

Is it possible to do internet streaming to say a windows media player of sorts?

---

### Post by Paerez on 2007-03-02
Hmmmm.

Now you are talking about setting up a web application for accessing the files.

I guess the easiest thing to do would be to install apache web server, and allow it to list directories. Then you would browse over http to your server and you would just see the contents of the directory, then click the file.

I don't know how well that would work.

There may also be video streaming apps out there for a web server. Like Ampache (which is for music). I use ampache a lot and its great, maybe there will be something like that for video.

---

