---
title: "cvs / pserver help"
date: 2006-10-19
forum: General Help
---

### Post by ryjac on 2006-10-19
Hello All,

I've set up cvs on my machine which i can access locally without any problems by using:

cvs -d :_pserver:cvs@localhost:/cvsexample login

I can also login via another machine on the network using:

cvs -d :_pserver:cvs@xxx.xxx.x.x:/cvsexample login
where xxx.xxx.x.x is the ip address of the box with pserver

my issue is when i try to log in from outside the network, i get the following message
/cvsexample: no such repository

I've searched around and found that --allow-root option in the xinetd configuration file needed to be set. However, if i was able to login from a seperate machine on the network, shouldn't I be able to access it externally from the network?

I've already set the port forwarding on my wireless linksys router to that machine. I doubt that I wouldn't be getting that error if it was that. Which, by the way, the telnet testing worked on it. (telnet xxx.xxx.xxx.xxx 2401)

Thanks in advance for any suggestions.

[note: the _ in :_pserver is used to prevent it from turning into a smilie face. it's omitted during my actual tests]

---

### Post by ryjac on 2006-10-19
Okay, I've figured it out and it was 100% user error.

I was typing in the module name rather than the repository name.

---

### Post by jonathan.jbkt on 2007-02-27
I followed the instructions on this link

 [http://doc.ubuntu.com/ubuntu/serverguide/C/cvs-server.html#cvs-installation](http://doc.ubuntu.com/ubuntu/serverguide/C/cvs-server.html#cvs-installation)

and am still getting 

$ cvs -d :pserver:jgardner@192.168.79.15:/cvs login
Logging in to :pserver:jgardner@192.168.79.15:2401/cvs
CVS password: 
/cvs: no such repository
JGARDNER-MAC:~ jgardner$ 

This is the xinetd.conf file

service cvspserver
{
        port = 2401
        socket_type = stream
        protocol = tcp
        wait = no
        server = /usr/bin/cvs
        server_args = -f --allow-root /cvs pserver
        user = root
        type = UNLISTED
        disable = no
}

This is in the cvsd.conf

Listen * 2401   
Repos /cvs

Where else would I go to find out why this is happening

---

