---
title: "Best ftp client for Ubuntu"
date: 2005-10-24
forum: General Help
---

### Post by blackrain on 2005-10-24
I'm looking for a best ftp client for uploading. If you have the same problem, take a look at:
[http://g6-vn.com/vtk/bestftpclients.html]("http://g6-vn.com/vtk/bestftpclients.html")

Now, i'm using gFTP but it is not good. It is slow, always crash, quickly loose connection :???: Any recommend ?

---

### Post by aysiu on 2005-10-24
I tried gFTP, and a lot of people here will recommend gFTP, but I like Konqueror the best--yes, even in Gnome.

---

### Post by brentoboy on 2005-10-24
I really like the one built into naulilus

open nautilus
ctrl+L (to convert the bottons onto a text location)

[ftp://www.site.com](ftp://www.site.com)

login, and surf the ftp site like its local.

---

### Post by camj on 2005-10-24
The one built into Gnome/Nautilus

Places -> Connect to Server

Select FTP or FTP (With Login) from the Service Type list

---

### Post by taurus on 2005-10-24
[QUOTE=aysiu]I tried gFTP, and a lot of people here will recommend gFTP,[/QUOTE]
Yes, I recommand gFTP because I never have any problem with it and it is running fast too...  ;)

---

### Post by MarcDM on 2005-10-26
<rant style="kicking : true; screaming: 4Hz; crying: no;" >

I absolutely hate gFTP. :evil:  It reminds me of WS-FTP on another platform. 

When I used that platform I liked BulletProof FTP. It had a nice queue + cache system that allowed me to do lots of stuff on the remote site then the actions were queued and then executed in turn. 

This worked for uploads, downloads, file-renames, chmod/own  and various other ftp commands. 

Right now I use a combination of gFTP and Nautilus. (don't let me start on Nautilus. -- sudo killall nautilus --)

Below are the features available elsewhere that would make gFTP better. 
[LIST]
[*]give me the option to execute the queue later. Don't force me to do it now. A Go button would be nice here. This is GREAT on slower connections
[*]let me drag a file into a folder. drag a file from the remote site into a folder on the locat side or vice versa. I use Nautilus for this. It's a pain to click into 12 folders on 2 sides. Let me do it on one side and drag into folders on the other
[*]don't execute the queue immediately.
[*]if there's a problem with the connection, kill it [the connection] and reconnect. don't crash, don't hang
[*]try to make an educated guess at the file type [binary/ascii]. Ask gnome-vfs/gnome-settings-daemon whomever has a list. If not, make it easier to switch, gimme a hotkey, a button, a context menu. The file menu too far.
[*]On the topic of Context menus, the menu too long and is mostly useless. Am I the only one that has never sent a SITE command?
[*]Queue all remote (and possibly local) commands. It's a waste of time, bandwidth and processor power to generate a LIST -L for every RNFR/RNTO combination. Add that to the queue and they'll get done when I hit go.
[*]make it easier to stop a file transfer or with the new queue, to stop execution. Right now I'm not sure if I should STOP, SKIP or REMOVE. Usually I just `killall gftp`
[/LIST]

Oh and don't tell me that gFTP can be set to not "Start Transfers Immediately". Because if I select multiple transfers, I have to select each one and click "Start Transfer" from either the Transfers menu or the context menu; no button, no hotkey, no way to start them all at once.

I hope I haven't hurt anyone's feelings but this is how I feel about gftp after using it to connect to a few burdended servers over a 128/64 ADSL connection. 

I've used Konqueror in the past and it worked, but kde's "configurability" annoys me. And even though I'm asking for buttons in gftp, konqueror has too many.  Add to that, I'm aiming for a sans-QT environment so that rules out konqueror.

I plan to try write something better than gftp soon. I go on vacation in December and I plan to start working on it then, when I have some free time.  For now, I'll keep complaining, and use what I have. 

Love, 

Marc DM

</rant>

---

### Post by Jonne on 2005-10-26
I'm also looking for an alternative for gFTP. On Windows I use FileZilla, which I like very much. Sadly, FileZilla is only win32, so I'm kinda stuck with gFTP (that doesn't even seem to have drag & drop :().

---

### Post by manicka on 2005-10-26
I like gftp but I have very modest ftp needs. Nautilus also does a good job as previously mentioned.

---

### Post by mykey on 2005-10-26
why not use old nautilus - just Ctrl+L in any window of the file manager and type the location you want like [ftp://blabla.org](ftp://blabla.org) - you can drag and drop between windows, create bookmarks via 'Places' -> 'Connect to Server'

---

### Post by stoeptegel on 2005-10-26
I installed kftpgrabber with klik:// today. It worked fine and has some nice features.

---

### Post by munkymonkjr on 2005-10-26
i use gftp and it ain't that bad

---

### Post by ow50 on 2005-10-26
[QUOTE=mykey]why not use old nautilus - just Ctrl+L in any window of the file manager and type the location you want like [ftp://blabla.org](ftp://blabla.org) - you can drag and drop between windows, create bookmarks via 'Places' -> 'Connect to Server'[/QUOTE]
Nautilus won't allow changing permissions of remote files.
[http://bugzilla.gnome.org/show_bug.cgi?id=309700](http://bugzilla.gnome.org/show_bug.cgi?id=309700)

---

### Post by Appolusionist on 2005-10-26
[quote=munkymonkjr]i use gftp and it ain't that bad[/quote]
 
I second gftp also.

---

### Post by dizzy1234 on 2005-10-26
Are there any nice SFTP clients that work with Ubuntu? I've been having some problems with Nautiluses impression of an SFTP client :(

---

### Post by stoeptegel on 2005-10-26
Yes filezilla has sftp support and goes also linux from verion 3 :p (but kftpgrabber also does sftp)
[http://filezilla-project.org/nightly.php](http://filezilla-project.org/nightly.php)

---

### Post by Efwis on 2005-10-26
I use on of two ftp programs.

gFTP and fireftp 
I have found I like gFTP. to me it's easy to use and actually quite user friendly.

the only drawback to fireftp is that you have to have Firefox running in order to use it. but it comes in handy when i need it on the fly.

---

### Post by ow50 on 2005-10-26
[QUOTE=ow50]Nautilus won't allow changing permissions of remote files.
[http://bugzilla.gnome.org/show_bug.cgi?id=309700](http://bugzilla.gnome.org/show_bug.cgi?id=309700)[/QUOTE]
I just recompiled my gnome-vfs2 packages with the patch attached to the bug report. The patch works, Nautilus now allows me to edit file permissions.

---

### Post by scourge on 2005-10-26
I would use Nautilus if it could follow links on ftp servers (it always says "Broken link"). GFTP can handle that so that's what I'm using now.

---

### Post by ember on 2005-10-26
gFTP is okay, but it really sucks when it comes to large file transfers. If you ever tried to upload some 1000 or 2000 files with gFTP, you will know what I mean.
Yet it's the best solution I have seen (partly because it has a GTK2 interface and I like consistency in my apps).

---

### Post by Kyral on 2005-10-26
If you are Terminal Savvy, then IMO, the command line ftp and sftp and scp commands are the way to go :D

---

### Post by Efwis on 2005-10-26
> **MarcDM]<rant style="kicking : true said:**
> 
[*]give me the option to execute the queue later. Don't force me to do it now. A Go button would be nice here. This is GREAT on slower connections
[*]let me drag a file into a folder. drag a file from the remote site into a folder on the locat side or vice versa. I use Nautilus for this. It's a pain to click into 12 folders on 2 sides. Let me do it on one side and drag into folders on the other
[*]don't execute the queue immediately.
[*]if there's a problem with the connection, kill it [the connection] and reconnect. don't crash, don't hang
[*]try to make an educated guess at the file type [binary/ascii]. Ask gnome-vfs/gnome-settings-daemon whomever has a list. If not, make it easier to switch, gimme a hotkey, a button, a context menu. The file menu too far.
[*]On the topic of Context menus, the menu too long and is mostly useless. Am I the only one that has never sent a SITE command?
[*]Queue all remote (and possibly local) commands. It's a waste of time, bandwidth and processor power to generate a LIST -L for every RNFR/RNTO combination. Add that to the queue and they'll get done when I hit go.
[*]make it easier to stop a file transfer or with the new queue, to stop execution. Right now I'm not sure if I should STOP, SKIP or REMOVE. Usually I just `killall gftp`
[/LIST]

Oh and don't tell me that gFTP can be set to not "Start Transfers Immediately". Because if I select multiple transfers, I have to select each one and click "Start Transfer" from either the Transfers menu or the context menu; no button, no hotkey, no way to start them all at once.

I hope I haven't hurt anyone's feelings but this is how I feel about gftp after using it to connect to a few burdended servers over a 128/64 ADSL connection. 

I've used Konqueror in the past and it worked, but kde's "configurability" annoys me. And even though I'm asking for buttons in gftp, konqueror has too many.  Add to that, I'm aiming for a sans-QT environment so that rules out konqueror.

I plan to try write something better than gftp soon. I go on vacation in December and I plan to start working on it then, when I have some free time.  For now, I'll keep complaining, and use what I have. 

Love, 

Marc DM

</rant>
you might be interested in this FTP client then. 

[DPS-FTP - Multi-threaded FTP client.](http://www.icewalkers.com/Linux/Software/54160/DPS-FTP.html)
[quote=http://www.icewalkers.com]
DPS-FTP is an FTP client whose interface is loosely based on that of Bulletproof FTP. It has a transfer queue which allows multiple files from multiple directories on multiple sites to be uploaded and downloaded, in any order, and can automatically resume partially transferred files, among other features.[/quote]

your can download it at [http://dpsftp.sourceforge.net/](http://dpsftp.sourceforge.net/)

---

### Post by MarcDM on 2005-10-28
Yeah I remember reading about DPS-FTP client back when I used Warty. But on the home page the news item says :
**2000-06-27 DPS-FTP 0.7.0... Coming soon!**

My patience has run out.

---

### Post by Efwis on 2005-10-28
[QUOTE=MarcDM]Yeah I remember reading about DPS-FTP client back when I used Warty. But on the home page the news item says :
**2000-06-27 DPS-FTP 0.7.0... Coming soon!**

My patience has run out.[/QUOTE]
I just sent an email to the project admin asking about taking the project over. if your interested in helping revive this project, should I manage to get it, Please PM me and let me know.

---

