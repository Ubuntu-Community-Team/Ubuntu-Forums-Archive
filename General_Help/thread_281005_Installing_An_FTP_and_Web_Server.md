---
title: "Installing An FTP and Web Server"
date: 2006-10-20
forum: General Help
---

### Post by jamez15 on 2006-10-20
Hey,

I need assistance and your views on a problem I have. I have a studio and what I want to do is take one of my computers and rip all my albums and created songs all to this one computer. So that all the other computers in the house and in the studio can easily access the music on it. 
 
Now what I’m thinking is setup and ftp server so that I can easily download the music and upload new music to it from other networked computers. I want to setup a web server on the same computer which would stream the computer's music selection over the home network. Now im also thinking would it be possible to access the streamed music over the internet?

Now I know this can be done but I don’t really know how get started. I'm currently scouring Google for tutorials on setting up an ftp server but I’ve yet to find one using apache. 

Is it possible to use apache to be an ftp server and also stream the box's music collection on demand? Should I use something else? Really a true importance right now is security.

If so can someone explain how or give me some tutorials to follow. Also I would love some suggestions if you think there is a better way to go about doing this.:-D
:-D

---

### Post by almahtar on 2006-10-20
Alrighty... I've done this at my place and this is how I did it:

(on your server) apt-get install openssh-server

From your linux machines you can get to your music on the music server as follows:

*edit: the forums kept turning the quoted string in this paragraph into a smiley and a cussword, so I put spaces after "user" and before "pass".  They shouldn't actually be there.*
from nautilus, hit ctrl+l and type in "sftp://user : pass @yourmusicmachine" without quotes.  Obviously, replace "user" with your username on the music machine, pass with that account's password, and yourmusicmachine with the ip address of your music machine.

Nautilus will mount up your remote machine's file system as if it was a folder right there on that machine.  It's really slick.  Optionally you can add the path to your music after the host name: "sftp://user : pass@yourmusicmachine/home/user/music" - you'll be looking at a file browser that looks exactly like it'd look if you were using the music server.

To connect to the music server with your windows machines, download and install the program "sftpdrive" and you'll get similar slickness.

As far as streaming music, look into "shoutcast" - last time I streamed music from a server that's what I used, but it's been a long time so there could be better things out there now.

Instead of a web server, though, I set up a VNC server: it's really easy - you get access to the server's desktop as if you were right there.  It's the best way to administrate a machine on a local network as far as ease-of-use goes.  Run the vnc client from your other machine and it'll connect to the music server and open up a little window on your other machine that contains the desktop of the music server machine.  Point, click, easy.  There are VNC clients and servers available for Windows and Linux, and they're free.

If you'd still like to do it with an ftp server and a web server, let me know and I'll try to walk you through that - I just did it this way because it's easier to use day-to-day.  SSH is much more secure than FTP, but VNC vs. Apache is a toss up.  Apache is more likely to be attacked because it's all over the place and VNC servers are less common, and unless you have a reasonably skilled hacker after you it's unlikely they'd even know what to do with an intercepted VNC session.  On the other hand VNC passwords are (I think) limited to something stupid small like 8 characters, so they're easy to run dictionary attacks on.

In a standard household or small office network it's plenty secure unless you have reason to think you're being targetted.

---

### Post by jamez15 on 2006-10-20
Thanks for the swift response.

Thanks for reminding about openssh. It totally slipped my mind that using openssh will sercure the connections between all the computers 

Now about using sftp to connect the compters is that similar to regular ftp??? Because if it is it seems as though its more work use sftp because on all of my windows machines i have to download a separate program and then configure that program. I mean with ftp its just, set it up on one computer and then and any other computer can easily access that machine's files that i allow to be accessed. Also the frequent mounting and unmounting is unnesscary with regular ftp. But there might some advantages to using sftp over ftp that comes with the extra work.

Now to the streaming. I was looking for a solution that would allow me the folowing:

I open a web browser navigate to that computer using the internal ip
then all of my music comes up and from there i choose which i would like to stream over network to my computer.

Can shoutcast provide this functionality? Cause i haven't reasearched shoutcast yet seeing as you already used it. And you would able to tell me about it.

Thanks in advanced
James

---

### Post by almahtar on 2006-10-25
As far as the mounting/unmounting in Ubuntu, it's all handled by the OS.  You tell it to connect once and you get an icon on your desktop from then on allowing you to connect to it with a simple double click.  Only if you manually unmount it will you have to take the trouble to re-connect.

As for the web browser, I'm not sure if there are shoutcast clients for web browsers.  No idea.  You could look into AjaxTunes though... it might help.

---

### Post by TigerWolf on 2006-10-25
For ease of use and installation - [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

