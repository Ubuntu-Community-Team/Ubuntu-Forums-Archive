---
title: "SFTP - SSH -JAIL / CHROOT - help reqeust"
date: 2016-12-03
forum: General Help
---

### Post by Pandee on 2016-12-03
Hello!

I have been searching high and low, yet I have not found proper material to help me with the task I want to do. 

What I want to do is this.

Register a user so that he/she  can only view the one folder via...
-- SSH access to only that one folder
-- SFTP access to that one folder

And also..
-- Restrict read/access/write certain folders or files within the said folder
-- I only need permissions / commands to tail -f a text file

If you need more details I am more than happy to provide. 

Many thanks,

Pandee

---

### Post by Pandee on 2016-12-08
Anyone?

---

### Post by Keith_Helms on 2016-12-08
The title of your post indicates you know the answer - chroot.

In general the steps you'll need to take are:
* Create a directory hierarchy / "root" that the user will be confined to.
* Copy or link any commands or files the user will be allowed to use into that directory tree (such as /usr/bin/tail).
* Create the user
* Modify the sshd config to only allow the user to ssh/sftp with chroot to that directory hierarchy.  You can google the config changes needed.

This will take a LOT of work if all you want the user to do is to be able to tail a text file.

---

### Post by Pandee on 2016-12-08
Hello and thankyou.

So say I just want a user to only be able to tail a text file and nothing else. Whats the best method?

I want to do something like this [http://serverfault.com/questions/608723/tail-a-file-from-ssh-and-mirror-to-a-local-file](http://serverfault.com/questions/608723/tail-a-file-from-ssh-and-mirror-to-a-local-file) with that file.

Some breakdowns or explanations would be great ^__^

---

### Post by Keith_Helms on 2016-12-08
Do they actually need to watch the file grow or is it enough to see a snapshot of the file?  You could set up samba and restrict the user to just being able to read that one file.  That would allow the user to see what the file currently looks like.  They could repeat that read operation however often they wanted to.  Is this a large file?  Some kind of logfile?

---

### Post by Keith_Helms on 2016-12-08
Here's one possibility.  You can use a command called netcat to take the output from tail and publish it to an ip address and port number.  The user could then use the listen option of netcat to receive that text and either display it on their terminal or write it to a file.

This is described here and sounds reasonably simple to me (I haven't tried it):
[http://osxdaily.com/2014/03/27/send-data-across-network-netcat/](http://osxdaily.com/2014/03/27/send-data-across-network-netcat/)

---

### Post by Pandee on 2016-12-08
> **Keith_Helms said:**
> Here's one possibility.  You can use a command called netcat to take the output from tail and publish it to an ip address and port number.  The user could then use the listen option of netcat to receive that text and either display it on their terminal or write it to a file.

This is described here and sounds reasonably simple to me (I haven't tried it):
[http://osxdaily.com/2014/03/27/send-data-across-network-netcat/](http://osxdaily.com/2014/03/27/send-data-across-network-netcat/)

Thank you! I will try that and tell you how it goes.

And yes its a log file ^__^ I will take a look at samba as well

---

### Post by Pandee on 2016-12-08
Ok i have decided to use netcat. Is it possible to do it via SSH and at the same time across two different networks (Internet)? Im having trouble finding guides for what i wanna do >_<

---

### Post by Keith_Helms on 2016-12-09
I thought netcat could broadcast and receivers could connect at any time, but after playing around with it it looks like a listener must be set up first and only then can netcat publish data to that listener.

There may be other publish/subscribe over the network type solutions, but I'm not aware of them at the moment.  I recommend you just build a user and chroot them to running tail and whatever other commands they might need.

---

### Post by HermanAB on 2016-12-09
Hmm, lemme see...

```
On the server with IP address 1.2.3.4:
# tail -f /var/file.log | nc -l 5555

On the PC:
# nc 1.2.3.4 5555
```

---

