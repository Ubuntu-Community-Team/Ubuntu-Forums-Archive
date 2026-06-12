---
title: "Folder Linking"
date: 2007-11-27
forum: General Help
---

### Post by mistaWAC on 2007-11-27
I need some help setting up a webserver, not much though.  Now I'm not completely new to Ubuntu/linux, but I know enough to do some damage.  I've been fidgeting with it for roughly a year now and I've finally got a computer that can run a few things no problem.  

I've got everything setup and running to my specifications, I think.  PHP is working, apache works, proftpd works.  The way my computer is setup is that the os is installed on a 160g harddrive and a 500gig is slaved for files.  Proftpd points to the 500gig as that's where I hold all my fun stuff, but the webserver points to /var/www.  I want to link that www folder to the /media/hdb/FTP-Shared folder so when people FTP in they can upload their websites to their folders.  How do I do that?  I tried 'ln -s /var/www' from within the FTP-Shared folder and it did link.  I can access the folder from the local system, but when FTP'd in it says "file or folder does not exist."  I use FlashFXP if that's any help.

Also, a currently minor issue, mysql isn't working.  Was trying to install a bittorrent app via Putty and attempted to execute 'mysqladmin -uroot -p create torrentflux' and it gave me some couldn't connect to localhost error.  I don't remember the exact error, but it would let me create my database.  Really I'd like to get the folder linking working first, but idealy I'd like bth the folder linking and mysql working.

Thanks in advance for any help!

---

### Post by mistaWAC on 2007-11-27
bump..

any help anyone?

---

