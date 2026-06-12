---
title: "accessing X session"
date: 2006-10-24
forum: General Help
---

### Post by matthewstory on 2006-10-24
ok, this is really nasty, and i'm not sure if this is the right place to ask . . . but here goes:

I'm working on an Open Source application to play movies in VLC on Ubuntu via a webserver.  This will serve as a remote control, and also as a way to pool files across multiple real servers and serve them in one place via HTTP.  The problem is this, I'm using php to do most of the web interface stuff, and I want to have a feature such that you can open a movie by clicking on a button on the web interface in VLC.  The apache server will be running on the same machine as VLC.  I have all the stuff written to do this . . . except I keep getting an error.

The user www-data runs the apache server, and the user i run VLC as is the user matt.  So the initial problem is that www-data doesn't have permission to execute VLC, so i make some changes in the sudoers file to allow www-data to execute VLC as matt.  This works fine, it can execute VLC as matt, but it does it in www-data's X session, which doesn't exist.  So basically, I'm wondering if anyone has any info as to how I would go about setting this up such that www-data could access the current X session.  So basically, how one goes about accessing an X session.  I'm pretty sure if I gave www-data sudo privelege to access VLC as root without a password in the sudoers file (which is easy enough) it would be possible to do this regardless of the current X user.  The question is just how . . .

---

