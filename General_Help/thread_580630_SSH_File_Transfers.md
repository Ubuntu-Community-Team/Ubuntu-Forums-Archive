---
title: "SSH File Transfers"
date: 2007-10-18
forum: General Help
---

### Post by gswang on 2007-10-18
I need some help with SSH file transfers, I'm trying to transfer files between my home computer and a certain server. I'm doing something entirely stupid right now. There are 2 servers, and I am running Feisty Fawn ubuntu.

Server 1: I have to go through a gateway to get to this server, so while I can ssh into it, it requires enough human input (I think...?) to simply use "scp" with that as the directory. On the other hand, I can't seem to use scp with my own computer as the target, and when I try to use scp and punch in my own ip, it fails..(does Ubuntu accept ssh connections...? Do I need to port forward something from my router?).
 
If that isnt clear: 
xxxxgw.lbl.gov is the gateway
yyy.lbl.gov is the ocmputer I'm trying to get to
but yyy does not accept ssh connections, so you have to connect through xxxxgw. 


Server 2: This doesn't have the files, but I can scp into this from both server 1 and my home computer.

So right now, I'm scping from server 1 to server 2, then from server 2 to home. 

---------

Before, in the ssh windows client, I could use the file transfer client and just drag the folder from server 1 directly to my home computer once I ssh into it...shouldn't there be an equivalent for linux?

---

### Post by eldragon on 2007-10-18
do you mean the following?

you got 3 computers.......
A, B and C

A is behind a NAT, B is within the same LAN A is, but its accesible through SSH from the internet., and you want to ssh from C to A....... is that correct?

if this is the case, you've got to set a tunnel from A to C first. so you have to install a ssh daemon on C first.

then from A, ssh -R 2222:localhost:22 username@computer_C

this will make all connections to computer C from localhost (same computer) at port 2222, be forwarded to computer A at port 22 (its own SSH server).

once the tunnel is set. from computer C, you can just ssh -p 2222 username@localhost which will patch you through the tunnel youve just created.
if you want to do scp, its just the same, you could use putty's psftp which behaves like the ftp command, but through ssh.

hope i was clear enough..

---

### Post by JTux on 2007-10-18
Did you try this.
Places->Connect to Server

This allows you to navigate the server with nautilus and do pretty much anything

---

