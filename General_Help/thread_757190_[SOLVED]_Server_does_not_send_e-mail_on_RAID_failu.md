---
title: "[SOLVED] Server does not send e-mail on RAID failure"
date: 2008-04-16
forum: General Help
---

### Post by Kissell on 2008-04-16
Okay, I recently switched one of the file servers to Ubuntu from Windows, by blowing it away and creating it in Ubuntu and restoring files from tape, and creating samba shares and all that good stuff.  And it's been working great as a file server, that's all I want it to do is be a file server.  

Today I was showing someone else how to use the CLI in linux regarding the disk commands, and he noticed that my RAID-5 with hotspare had a failed drive and it automatically took the hot spare and made the RAID-5 redundant again...  great...  (don't worry, i have logic to why i'm not using raid-6)

But that reminded me of one important thing that wasn't pressing, which I hadn't gotten around to figuring out yet.  "Gee, it sure would have been nice if I was notified, perhaps via e-mail, when the drive f
ailed."  It's been dead, and I never noticed, and another failure means unheathy raid, and another means catastrophy.  :(    Obviously, since I'm relatively new to linux administration in a production environment, I have this data elsewhere...  but it's probably time I learn how to do this fairly important task. 

I've attempted to follow guides to setup all sorts of mail on this server, from sendmail to exim4, and none of them work for me.  I'm not completely hopeless, my problem is that my SMTP server is with my ISP, and they use a non-standard port (not 25) and they also require authentication.  None of the guides I've attempted to follow have addressed how to deal with these issues, which I'm sure is at least one of the reasons why I didn't get alerted.

Can someone please help?  I'd love to know the CLI from start to finish, but if there's a GUI applet that quickly/easily does this, that'll work too.  I don't need to send/receive mail for normal user e-mail, the only thing I want is to be alerted when I have a disk failure, cause protecting data is what I'm primarily concerned with, I can fix/replace hardware, software, connectivity, but i can't recreate intellectual property, so protecting the data is fairly important to me before I can roll out ubuntu to the rest of my world.
:confused:

---

### Post by fjgaude on 2008-04-16
I'm not sure I can help you. Here's the only command ever used to get auto mail on failure:

```
mdadm --monitor --mail=xunil@theanykey.com --delay=30 --scan
```

I personally never used such as I daily use **hdparm** to test the speed of my array. If it is slow I know a drive failed.

They was a guy around here that had a way to get what you need but I can't find his post of how he did it, getting out to his ISP and back again.

You might try posting in the Server Forum here.

---

### Post by Kissell on 2008-04-17
I think mdadm is setup to send mail, but I need the server setup to do send mail in general in order for it to work...  :(

And I think I have the server okay to send mail, if i was using a SMTP server that didn't require authentication and let me use a specificly specified port.

I'd like to get past this phase...  where I recognize linux as better but windows as easier, but I still need a lot of help.

---

### Post by Kissell on 2008-04-18
got it working, used ESMTP which was exactly what I wanted.  then used the mdadm --monitor service running as a daemon, works great!!!

---

### Post by fjgaude on 2008-04-18
Wonderful... we learn new things each day, eh?

---

