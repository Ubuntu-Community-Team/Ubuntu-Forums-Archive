---
title: "Connect to Server"
date: 2007-02-12
forum: General Help
---

### Post by sparty2809 on 2007-02-12
When you use the Connect to Server, where does it mount the file system?  I mean, it mounts it on the Desktop, but how can I browse it when I open Eclipse or Gedit or any other program?

---

### Post by kidders on 2007-02-12
Hi there,

You can open a terminal window and type **mount** to see where it went. You'll see something like "192.168.1.1:/home on /media/somewhere type nfs...." ... assuming it *has* actually been mounted. (Sometimes, KDE for instance, won't necessarily perform the mount for you.)

---

### Post by sparty2809 on 2007-02-13
Thanks, I tried that but I didn't see it.  Any other ideas?

---

### Post by Ramses de Norre on 2007-02-13
What protocol do you use to connect to the filesystem? (samba, nfs, ...)

---

### Post by sparty2809 on 2007-02-13
In nautilus, I go to File-Connect to Server and use Windows Share to connect to my network drive.

---

### Post by Ramses de Norre on 2007-02-13
Try smb://<ip address>/path

---

### Post by sparty2809 on 2007-02-13
Nope, that doesn't work either.  I can mount the drive fine, I just can't browse it with any application.

---

### Post by Ramses de Norre on 2007-02-14
Are you sure it's connected over samba? I've got another pc at 192.168.124.195 with a shared directory called "ramses" and I can connect to it with **smb://192.168.124.195/ramses** in firefox, nautilus, ... I don't know which app you're trying? And do you use the shared directory's name after the ip-address?

---

### Post by sparty2809 on 2007-02-14
I can browse it fine throught nautilus, but when I go to open eclipse or gedit, I can't browse to it.  I don't know where it mounts to.

---

### Post by Ramses de Norre on 2007-02-14
Gedit: file > open location > type the location like I told before: smb://ip-address/share-name/path to file relative to shared directory

E.g. I've got a file in the share I told about before called firefox.speed, in gedit in open location I type smb://192.168.124.195/ramses/firefox.speed and the file opens.

Eclipse: doesn't work it seems, I'll try to find a way (got interested in it too :) ).

---

### Post by kidders on 2007-02-14
> **sparty2809 said:**
> Thanks, I tried that but I didn't see it.  Any other ideas?If it's not on the list, then the share isn't mounted.

Over the past few years, some developers have started implementing silly filesharing "protocols", like smb://, afp://, webdav://, and so on, which is *extremely* unhelpful, because they don't work the same way (or at all) in every application. I can say with a good degree of certainty, that Eclipse (and most other Java-based applications) will never implement them, because they're not platform independent URIs.

The standard way to make a filesystem accessible to all applications & services is to mount it, just as you would a CD or a hard disk. There are various ways of making this happen automatically, but failing that, you can do it yourself with a **mount** command. Once you find a command that works the way you want it to (in terms of permissions, etc.), you can make doing it on a day-to-day basis more straightforward, by:

[LIST]
[*]Adding a line to /etc/fstab can make mounts quicker to type.
[*]There are various applications that can manage network mounts for you. (KDE can, for instance ... I'm not sure about Gnome).
[/LIST]

I suppose the basic point is that *something* needs to do a **mount //server/sharename** type thing at some point ... whether it's you, your graphical environment, or a little app you've downloaded, doesn't make any difference.

I hope that helps.

---

### Post by greyspoke on 2007-02-15
Thanks kidders this was confusing me also.  Now I know why my shared folders aren't mounted anywhere!  (That's know as in not-the-same-thing-as-understand.)

---

### Post by kidders on 2007-02-15
Think of it this way...

Afaik, if you hit CTRL+O and ask Wordpad to open http://www.wherever.com/document.doc it will tell you to go away and learn to spell. OpenOffice on the other hand is happy to open documents over HTTP. Similarly, some applications will have implementations of other protocols, such as media:// or smb://, while others won't.

The only to make sure that your entire system has access to your stuff (whether on Windows or Linux) is to mount your shares, so they can be accessed through the filesystem, the same way as local files.

Is that any help?

Taking Eclipse (which is available for MacOS, Linux & Windows) as a specific example, there would be little point in the developers making the application capable of opening media://sdc1/test.java, since notation like that would be completely incompatible with MacOS & Windows. The same idea applies to smb://, afp://, and so on.

---

### Post by leetcharmer on 2008-03-20
so, how could I browse my "Connect to Server" Windows Share with CLI?

---

### Post by Xvani on 2008-04-21
When using "SSH" as the protocol. Is it still not mounted? I can't get that working either with eclipse...

Is there a plugin?

---

### Post by jaime256 on 2008-04-26
I just installed Ubuntu 8.04 and I can't connect to my server either it's actually a nas. I used the connect to server, type the ip, then it places the icon on the desktop that I was using. I can still access it with my other machine, but when I try to do it with the new version I get "can't display location smb...and the ip...this is all I used to do, but this version won't let me, any other ideas? I'm not sure how they change this, but this is a bummer. I can manually go to each folder, but then I can't get to the files from within the program like Screem to edit my files...

---

