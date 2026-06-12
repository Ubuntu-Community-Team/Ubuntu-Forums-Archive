---
title: "[SOLVED] How do I Connect to Webdav Network in Nautilus?"
date: 2008-04-21
forum: General Help
---

### Post by ibuclaw on 2008-04-21
Hi all,

I have recently switched email to [GMX]("http://mail-eu.gmx.com/") as a "New Years Resolution" to slowly branch myself away from Microsoft products this year.

One cool feature that I've found is that I have a Gigabyte of file storage.
And instructions are given on how to [setup an integrated network drive in Konqueror.]("https://help.gmx.com/storage/network/linux/?si=2thgk.1jNWfl.4796AU.o**")

But can anyone figure out how to do this in Nautilus.

I've had a play about with the "Connect to Server" in the File Menu, but with no avail.

Oh, and by the way, if anyone knows how to setup any sort of connection with it (ie: in the command line), that will help also!

Thanks in advance.

Regards
Iain

---

### Post by ryanhaigh on 2008-04-21
You may want to look at davfs2.

Description:> 
 davfs2 is a Linux file system driver that allows mounting a WebDAV
 resource as a regular file system. Files in that resource can
 be edited using standard applications which interact with the file
 system (e.g. text editors).

Click here to install [davfs2](apt://davfs2)

---

### Post by ibuclaw on 2008-04-21
I've had a go at it, but there is one thing missing.

[EDIT]
Okay, I have it half fixed!
Changed it to my have my uid number in too.
And having it in /media seems to work better?
```
mount -t davfs -o uid=1001,gid=1001 https://storage-file-eu.gmx.com/ /media/GMX
```

I can now upload folders, but not files.
Also,  I can't see the files that are already uploaded to it.

here is my mtab output
```
https://storage-file-eu.gmx.com/ /media/GMX davfs rw,nosuid,nodev,_netdev,uid=1001,gid=1001 0 0 
```

Any help there?

Regards
Iain

---

### Post by ryanhaigh on 2008-04-21
Because I have never used this myself, although from reading what I have it sounds quite interesting, I will refer you to this post which others have pointed to as a good guide.

[http://ubuntuforums.org/showpost.php?p=2116697&postcount=12](http://ubuntuforums.org/showpost.php?p=2116697&postcount=12)

---

### Post by ibuclaw on 2008-04-21
Hey, thanks for your help...

Turns out the answer was much simpler than that.

I found a link in the thread of the post you gave me.

[QUOTE=pingflood]

Also, Konqueror can access Box.Net directly using the WebDAV protocol:

```
webdav://www.box.net/dav
```
(I think the protocol is just "dav://" in Nautilus)
[/QUOTE]

He was close, turns out that it was "**davs://**" all along!:lolflag:

Asked for username and password... I chose "Remember Forever"
And it works!

```
davs://storage-file-eu.gmx.com/
```

Anyway, cheers for the heads-up anyway.

Probably wouldn't of figured it out without the help.

Regards
Iain

---

