---
title: "How to preserve permissions on remote system"
date: 2007-12-16
forum: General Help
---

### Post by david.rahrer on 2007-12-16
This may seem obscure, and I'm having a fit finding the answer so I could use some serious help :-k

I have some remote Centos 5 based servers.  I often connect to them using Places > Connect to server using SSH.  This lets me browse the remote file system through Nautilus, something I used to do with WinSCP in my Windows days.  It's easier to edit a conf file using gedit than using pico over the command line, etc.  

Ok, the problem, which has given me quite a mess:  when I edit a text file on the remote as I described, then save it, the permissions are changed to, in this instance, "root:root" (yes, I know, logging in as root).  So, if a file was originally say, root:mail, that screws things up.

Is there a way to use this method of access AND preserve the permissions on the remote files?  Please make my day and have an answer ;)

Thanks!

---

### Post by Keith Hedger on 2007-12-16
when u log in via ssh u have the same permissions as the user u logged in as so if you log in via ssh as root you will of course have root perms which is what is changing the file permisiions so why not log in as a different user and use their permisions, or if u have to change a file as root u can always reset the permisions/ownership via chown and chmod (long winded i know)

---

### Post by david.rahrer on 2007-12-16
Thanks for the prompt reply.  I thought the same thing, but here's my confusion. I am logged in as root through the command line when I SSH in that way as well, yet when I pico filename and save it doesn't alter the permissions.  See what I mean?

Also, if I were to log in as another user using the method in my OP, I don't think I could edit the file at all since it's owned by root.  I can understand connecting as root giving me access to files, but I don't understand why the permissions are being changed when I don't ask it to.  As it stands, I either use pico or I do as you suggest, and chown it back to the correct group (the group is actually what's being changed in these instances).

So the question I guess is, should it be changing the group on the remote file just because root is saving the edited file?  Is this caused by the way gedit on my local Nautilus edits the file?  Does it transfer it first to tmp, then edit and transfer it back to the remote?  If I drag and drop a file into a remote Nautilus file listing, it does transfer as root:root.  

So if all that is true, I'm still back to is there a way to preserve the permissions,  Even longer winded ;)

---

### Post by Keith Hedger on 2007-12-16
sorry ive tried all sorts of ways of getting gedit to change the perms but it doesn't it seems to be pretty good at preserving the permisions regardless of whether i'm root or not. personally i use vim if i have to change a text file as root rather than gedit ( but i use gedit for everything else! )

---

### Post by david.rahrer on 2007-12-16
> **Keith Hedger said:**
> sorry ive tried all sorts of ways of getting gedit to change the perms but it doesn't it seems to be pretty good at preserving the permisions regardless of whether i'm root or not. personally i use vim if i have to change a text file as root rather than gedit ( but i use gedit for everything else! )

So you're saying when you edit a remote file via gedit over ssh, it *preserves* the permissions?

---

### Post by Keith Hedger on 2007-12-16
basicly yes , but i have to go im putting up xmas decerations be back later:):):)

---

### Post by jken146 on 2007-12-16
You can change the permissions back to how you want them with nautilus (right click > properties > permissions tab) if you don't like the CLI.

---

### Post by Keith Hedger on 2007-12-16
you could try using vnc if youve got a reasonable connection which would certainly fix the problem, you could also use the external tools plugin for gedit to run a small script to reset the perms so circumventing the command line.
my machine is making very strange noises:( time for trip to pc world i guess

---

### Post by colgate on 2008-05-16
I'm on hardy stable and the same problem goes on.
let's make an example:
I got a file on my server
/var/ww/tmp.php which has permission as myuser:www-data

now I connect via nautilus via ssh to my server and I want to modify it with gedit.

Whenever I save that file gedit change permission to myuser:mydefaultgroup !!!

THAT IS ANNOYING! :confused:
Every time I modify that file and I want to be able to see it in the browser I have to launch a small shell script that change file owner and permission.

Bye,

  Federico

---

