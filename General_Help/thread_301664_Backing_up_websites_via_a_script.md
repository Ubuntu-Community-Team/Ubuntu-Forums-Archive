---
title: "Backing up websites via a script?"
date: 2006-11-17
forum: General Help
---

### Post by Ted_Smith on 2006-11-17
Hi

Having just recovered by the skin of my teeth from a serious web site failure, it made me realise I need to work on my backup regime. 

I'd like to utilise the fantasticness of Linux by writing a script that I can simple launch that will do the following steps for me : 

Connect to remote MySQL database, log in, and export it as a SQL file (currently I do this via PHPMyAdmin)
Connect via FTP and download all the files

Not really sure whether this can be done though, or how to do it? 

Any ideas, suggestions, etc? 

Thanks

Ted

---

### Post by Ted_Smith on 2006-11-22
Perhaps there is more to this than I thought then? 
My line of thinking was of using ncftp to connect and download  the files (but I'm not sure how I'd 'give' the program the usernames and passwords) and then something else for the database download. I have written some PHP before that does that via an online PHP script, but I'm not sure how I'd do it from a standard bash script? How would I pass the host, username, password values, and also tell it to "Download X database in this way". 

Surely people must be doing it though. I thought writing maintenace scripts  was common for Linux\Unix admins?

Ted

---

### Post by justin whitaker on 2006-11-22
Did you check sourceforge? Someone must have run into this before.

---

### Post by cleentrax on 2006-11-22
I've been looking into this as well.

What about SSH instead of ftp? It seems like it would be better to create an archive file on the server, and then copy it via ssh rather than to try to ftp thousands of files via a script.

---

### Post by MJN on 2006-11-22
It might help if you can provide more context i.e. what's the setup at the moment? Is your web server offsite? What access to you have to it? Does/can it have rsync (and SSH) available?

If you're backing up a remote server you really don't want to be transferring every file, every time. Instead you want to be only transferring those files that have changed since the last backup - rsync can not only do this but it can get away with only transferring the *parts* of those files that have changed!

Furthermore, given it can run over SSH your username/password/files are safe from any eavesdroppers en route.

Mathew

---

### Post by Ted_Smith on 2006-11-22
Background : 

The website in question is commercially hosted with a provider based here in the UK. To access the MySQL I have to use PHPMyAdmin and log in over https with a username and password. I have written a PHP script before (see here [http://dev.xoops.org/modules/xfmod/project/showfiles.php?group_id=1318](http://dev.xoops.org/modules/xfmod/project/showfiles.php?group_id=1318)) that is able to connect, via HTTP, so access like that should not be a problem (once I sus out how to add it to a bash script, but my point is that the host allows that kind of connection). 

Then there are the files. Again, stored on the same commercail host (but different host name to the MySQL database of course) and accessible over a standard FTP connection - no encryption. 

wget was an option but that seems to be more of a mirroring facility than an FTP thing. It just access what it can publically access and resolves each of the pages, which with dynamic sites is not always what you want. So I don't think that is an option. 

ncftp, I thought, had a switch to tell it to only download the new or changes files, as desired and suggested above. Perhaps it hasn't - not looked into it enough but I;m sure I read that it had a switch to do that. 

That's it basically. Does that help at all? (I had not thought to look at sourceforge - will take a look)

Ted

---

### Post by Ted_Smith on 2006-11-23
I cannot find anything on Sourceforge. 

I have recently bought a C++ Programming book, and, having written some PHP before, I might have a go at writing a utility myself to do this, and then I'll release it as GNU. Gives me a good incentive to learn the language. 

Ted

---

### Post by Levez on 2006-11-26
You can run PHP scripts from the command line as well as from web-pages.  With a little bit of modification, you can make your original PHP script run as a script (there are lots of easily available tutorials around the web on doing this).  This would be your easiest option.

---

