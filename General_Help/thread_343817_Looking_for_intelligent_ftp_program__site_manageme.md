---
title: "Looking for intelligent ftp program / site management tool"
date: 2007-01-22
forum: General Help
---

### Post by pixelterra on 2007-01-22
For years I've used dreamweaver simply for it's extremely intelligent and intuitive site mangagement / ftp tool. Now I'm making the transition to linux and am looking for a similar site management tool even if it is stand-alone. I just want it to do 3 things:

1) store ftp info for many sites
2) has a built-in file manager
3) I want to select a file and hit a button that says "upload" and have it go to the **right** remote server in the **right ** directory. 

*Note that I am not looking for a simple FTP client. But rather one that is more of a **multiple site file manager**.

Is this a lot to ask? Any suggestions?

---

### Post by renzokuken on 2007-01-22
try gftp, very simple ftp tool thats easy to use.

```
sudo apt-get install gftp
```

---

### Post by souki on 2007-01-22
you can try :

- gftp (gtk+)
- nautilus built-in "connect to server"
- fireftp (firefox add-on)
- filezilla for linux (beta) : [http://filezilla.sourceforge.net/](http://filezilla.sourceforge.net/)
- iglooftp (closed source) : [http://www.iglooftp.com/](http://www.iglooftp.com/)

after trying a lot of different solutions, none of the gui based solutions worked for me, now I'm using console based solutions : lftp + sitecopy

but I'm still interested if someone has a good gui solution

---

### Post by Kulgan on 2007-01-22
ZDE is great if you develop from code. It also has awesome PHP highlighting, code completion and all that other stuff. Instead of the "upload" button, you just save files to the server, which saves having two copies of everything. But means that you can't dev without an internet connection, bu hell, who cares. 

ZDE also has database support, including MySQL, Oracle, PostgreSQL, etc...

I love it :D

You'll need Java installed, but it's (Java is) in the repos if you dont already. 

[http://www.zend.com/store/software/zend_studio/lp](http://www.zend.com/store/software/zend_studio/lp)

---

### Post by Josh1 on 2007-01-22
gFTP sucks, I hate how it crashes when I send large files (like over 10 megs!) it crashes......

---

### Post by glabouni on 2007-01-22
I second you. 
IMHO gftp is one the worst ftp client I have ever seen. To me it is a worthless piece of software.
but let's go back to the matter here.

total commander might be the answer to your needs. 
you'll find a howto to make it work under ubuntu here: [http://frankscorner.org/index.php?p=tc](http://frankscorner.org/index.php?p=tc)

---

### Post by pixelterra on 2007-01-22
I'll be honest, I've been looking for a program that can do these things for 4 years. But everyone seems to over-look the criteria for the program:

> I want to select a file and hit a button that says "upload" and have it go to the **[COLOR="Red"]right remote server[/COLOR]** in the **[COLOR="Red"]right directory[/COLOR]**.

That is what I mean by **intelligent**. For example I could select 4 files in 4 different directories on the local machine, hit the upload button, and have them all go **to the corresponding directories ** on the romote server.

None of the ftp programs mentioned above or anywhere else that I can find do this. Only dreamweaver seems to be able to do this. Four years in counting.

I don't even need a development environment, I would use a stand-alone app just as well.

---

### Post by Kulgan on 2007-01-22
Wouldn't know. Never even thought there would be a point in something like that, and seem to have managed without. If that's what you want, you could "just" make your own. Don't ask where that came from. 

The point about ZDE was that it had everything inbuilt, a little like DW...

---

### Post by glabouni on 2007-01-27
I guess you could give [kasablanca]("http://kasablanca.berlios.de/") or  [konqueror]("http://www.konqueror.org") a try to check if one of those suits your tastes and needs.

---

### Post by pixelterra on 2007-01-28
Thanks for the many suggestions folks, but unfortunately most of the suggestions are for "simple" ftp clients. I want much more. Like my post said, I'm looking for an **"intelligent"** ftp client. The specific intelligence I'm looking for is the ability to sync with a remote site, and intelligently put any file **in it's proper place** on the server when the upload button is hit. 

At this point I realize I'm hitting a brick wall. I guess the *nix world doesn't offer a client of this nature, and moreover, has difficulty grasping the concept at all. 

I do thank you for your suggestions, however, so please if you have something that fits the bill, please let me know.

So, like so many others (I know you've heard it all before), I siill have a couple of hangups before making the total switch to linux. The list used to be:

Flash
Photoshop
Dreamweaver

But Dreamweaver is halfway off the list since I've been using gvim for most of my code editing. Now I need a **proper site manager.** 

Anyone?

---

### Post by supirman on 2007-01-28
> **pixelterra said:**
> The specific intelligence I'm looking for is the ability to sync with a remote site, and intelligently put any file **in it's proper place** on the server when the upload button is hit. 


While it's not exactly 'ftp', nor is it graphical, you can implement rsync to sync the server to what you have locally.  And it will only update files which have changed since the last sync.  In fact, I have a script that will allow you to do just that, but you need ssh access to the server.

As for the feature you're speaking of in Dreamweaver, I've never heard of that feature before, but I agree it could save me a lot of time whenever I'm uploading certain files.  You figure it takes twice as long as necessary to browse to the same directory on the local and remote hosts before you can upload.  It would be nice to have a 'define site' feature, which if the file you selected for upload was under that site's defined path, it would put the file to the proper location.  

Neat feature, never thought of it before.  Perhaps somebody should implement that in one of the open source clients existing.

---

### Post by pcflunkies on 2007-02-03
I know exactly what you mean, I love Dreamweaver, I am going bald trying to get it to run via wine as we speak, because many of the other programs such as NVU, are pretty good, they are no comparison to Dreamweaver.

I managed to get Dreamweaver installed but I can't get it to run yet, Good luck finding anything, because I haven't been able too.

---

### Post by supirman on 2007-02-03
I don't typically have a lot of free time, but this sounds useful enough that I may look into implementing it.

---

