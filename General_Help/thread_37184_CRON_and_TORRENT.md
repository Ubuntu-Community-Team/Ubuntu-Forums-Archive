---
title: "CRON and TORRENT"
date: 2005-05-26
forum: General Help
---

### Post by pierre on 2005-05-26
Hi All,

Supposing i have a Samba shared folder named "Torrent" on my ubuntu server, in which i am copying torrent files ( for example a.torrent b. torrent and c.torrent ), 

How can i do for these to be downloaded automatically ?

Automatically means CRON for me, thus i thought i could create a bash file using a command like "btdownloadcurses.py --max_upload_rate 7 x.torrent"

But how can i detect the torrent file name ? ( a, b and c )
Supposing a file name d.torrent is added ... how can i start this one without restarting the others ?

I was sure i saw a command like btdownloadmanycurses .. but no relevant result on google.

Thanks for your replies.

regards,

Pierre

---

### Post by Leif on 2005-05-26
How about using azureus ? It keeps track of such things for you.

---

### Post by pierre on 2005-05-26
My ubuntu is a server without GUI .... that's why

---

### Post by shakin on 2005-05-26
You could have a shell script that loops through the files in the directory. Each time it starts a download it adds that torrent filename on a new line in started.txt. So, before starting each download it checks to make sure the torrent filename isn't already in started.txt.

I'd write some script, but I'm all scripted out at the moment :(

---

### Post by btdown on 2005-05-26
If you use the btlaunchmanycurses at startup, specifying a directory to look for .torrent files, it will check that directory every 60 seconds and start downloading any new .torrent files.
 
I use this a lot for my headless machine at home...If I see a torrent I like during the day, I log in remotely and wget the torrent to my /torrent directory. btlaunchmanycurses sees the entry 60seconds later and starts the download.....
 
You can check here for more btlaunchmanycurses options...
 
[http://annys.eines.info/cgi-bin/man/man2html?btlaunchmanycurses+1]("http://annys.eines.info/cgi-bin/man/man2html?btlaunchmanycurses+1")

---

### Post by pierre on 2005-05-26
i've found the following command ( which is working fine )

/usr/bin/btlaunchmanycurses /yourfolder/ --minport 7000 --maxport 8000 --max_upload_rate 40 --max_files_open 3 --saveas_style 3 --save_options 1

I cannot make a cron job of it, everytime i try to launch it, it says :
Error opening terminal: unknown.

Any idea ?

---

### Post by pierre on 2005-05-26
[QUOTE=btdown]If you use the btlaunchmanycurses at startup, specifying a directory to look for .torrent files, it will check that directory every 60 seconds and start downloading any new .torrent files.
 
I use this a lot for my headless machine at home...If I see a torrent I like during the day, I log in remotely and wget the torrent to my /torrent directory. btlaunchmanycurses sees the entry 60seconds later and starts the download.....
 
You can check here for more btlaunchmanycurses options...
 
[http://annys.eines.info/cgi-bin/man/man2html?btlaunchmanycurses+1]("http://annys.eines.info/cgi-bin/man/man2html?btlaunchmanycurses+1")[/QUOTE]

Nice ! thanks for the link ... 

How did u launch the command initially ? ( is it a cron job or anything else )
This could be interesting for me if my machine is restarting for any reason.

Cheers,

Pierre

---

### Post by btdown on 2005-05-26
Actually..try this:
 
type the command 'btdownloadheadless' without any arguments. Then look/use those arguments....At first, I would only trying using the /torrent directory, then add other arguments till you find whats broken.
 
You can use either btdownloadheadless or btlaunchmanycurses but the args may be different for each.
 
BT
 
Off the top of my head, im not quite sure how to start commands at startup, however, Im sure there are threads here about it, or at ubuntuguide.org

---

### Post by pierre on 2005-05-26
Tks a lot !

---

