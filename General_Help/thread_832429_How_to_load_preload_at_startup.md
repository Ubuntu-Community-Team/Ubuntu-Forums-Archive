---
title: "How to load preload at startup"
date: 2008-06-17
forum: General Help
---

### Post by stinkinrich88 on 2008-06-17
Hello,

I've installed preload and haven't really noticed any benefits. I think this is because it isn't running (it doesn't show in my process list). Do I need to add it to my startup list? If so, how do I run it with root privileges at startup?

thanks!

---

### Post by stinkinrich88 on 2008-06-18
right, as far as I can tell, there shouldn't be a preload process running in process monitor. It will start automatically at login anyway if it is installed. I don't need to do anything

---

### Post by Tomatz on 2008-06-18
It runs as a daemon. Also you wont notice any difference untill preload works out which apps you use most and starts caching. It can take days to start working properly.


[http://www.techthrob.com/tech/preload.php](http://www.techthrob.com/tech/preload.php)

---

### Post by Sealbhach on 2008-06-18
Just wondering if I should disable Preload before I start up a game?

I'm running Rainslick but I'm finding it slow and buggy. I was wondering if Preload had anything to do with it?



.

---

### Post by Tomatz on 2008-06-18
> **Sealbhach said:**
> Just wondering if I should disable Preload before I start up a game?

I'm running Rainslick but I'm finding it slow and buggy. I was wondering if Preload had anything to do with it?



.


Nope.

If you read the link i posted you will see that preload uses very little system resources ;)

---

### Post by kaibob on 2008-06-21
> **stinkinrich88 said:**
> Hello, I've installed preload and haven't really noticed any benefits. I think this is because it isn't running (it doesn't show in my process list). Do I need to add it to my startup list? If so, how do I run it with root privileges at startup? thanks!

You do not need to add preload to your startup list. Look at "Processes" in the System Monitor applet, and you should see preload. 

I've tried my system both with and without preload, and it does seem to have a bit more snap with preload. However, I agree that the difference is not great.

---

### Post by stinkinrich88 on 2008-06-22
I can't see it in my system monitor applet. "All processes" is selected in the "view" menu. Are you sure daemons are meant to show up there?

---

### Post by kaibob on 2008-06-22
> **stinkinrich88 said:**
> I can't see it in my system monitor applet. "All processes" is selected in the "view" menu. Are you sure daemons are meant to show up there?

I installed preload by way of synaptic and did not configure or enable it in any way. Preload does show up in the system monitor (see screenshot below).

I don't know why this wouldn't work for you. Perhaps someone with more knowledge can help.

---

### Post by Tomatz on 2008-06-22
Preload runs as a service so it wont show up as a process.

Go to *system, administration, services*.


Documentation in PDF format below:

[http://behdad.org/download/preload.pdf](http://behdad.org/download/preload.pdf)

;)

---

### Post by stinkinrich88 on 2008-06-22
> **Tomatz said:**
> Preload runs as a service so it wont show up as a process.

Go to *system, administration, services*.


Documentation in PDF format below:

[http://behdad.org/download/preload.pdf](http://behdad.org/download/preload.pdf)

;)


Cheers Tomatz, but I can't see it in my services list either. Is there any way I can check what services are running atm?

---

### Post by cariboo on 2008-06-22
To check what is running, in a terminal type:

```
ps ax
```

You might want to pipe that to a text file so:

```
ps ax > whats_running.txt
```

Jim

---

### Post by stinkinrich88 on 2008-06-22
Cheers Jim!

I don't think it's running, in that case. But I don't really know what I'm doing so I attached Whats_running.txt just in case. I searched for "Preload" with no results...

---

### Post by Tomatz on 2008-06-22
Open a terminal and type:

```
sudo less /var/lib/preload/preload.state
```

This will tell you if preload is running or not

Also you can access preloads log file by doing this:

```
sudo tail -f /var/log/preload.log
```

Hope that helps :)

---

### Post by stinkinrich88 on 2008-06-22
yeah, thanks dude! The first command printed loads and loads of lines of weird stuff. Didn't look very interesting. However, the log file is interesting:

> [Sun Jun 22 20:18:12 2008] failed reading state from /var/lib/preload/preload.state: line 13763: invalid syntax
[Sun Jun 22 20:18:12 2008] Exiting
[Sun Jun 22 20:49:38 2008] loading conf from /etc/preload.conf
[Sun Jun 22 20:49:38 2008] loading state from /var/lib/preload/preload.state
[Sun Jun 22 20:49:38 2008] failed reading state from /var/lib/preload/preload.state: line 13763: invalid syntax
[Sun Jun 22 20:49:38 2008] Exiting
[Sun Jun 22 20:51:05 2008] loading conf from /etc/preload.conf
[Sun Jun 22 20:51:05 2008] loading state from /var/lib/preload/preload.state
[Sun Jun 22 20:51:05 2008] failed reading state from /var/lib/preload/preload.state: line 13763: invalid syntax
[Sun Jun 22 20:51:05 2008] Exiting


Very queer. What do you reckon? I can open preload.state as root only.

---

### Post by Tomatz on 2008-06-22
> **stinkinrich88 said:**
> yeah, thanks dude! The first command printed loads and loads of lines of weird stuff. Didn't look very interesting. However, the log file is interesting:



Very queer. What do you reckon? I can open preload.state as root only.

It looks like there may be a bug (typo) in the preload.state file and preload was unable to read part of the file correctly but as you got the "lines of wierd stuff" from the first command "preload.state" it appears to be working fine (even though you called the file with the bug to do so).

And yeah you should only be able to open the file as root.

;)

---

### Post by stinkinrich88 on 2008-06-22
oh cool! So I've got nothing to worry about, eh! 

p.s. I called sudo preload a couple of times earlier to see if it would make it show in my process manager. Hope those "Exiting" lines in the log didn't mean it was exiting for good...

---

### Post by Tomatz on 2008-06-22
> **stinkinrich88 said:**
> oh cool! So I've got nothing to worry about, eh! 

p.s. I called sudo preload a couple of times earlier to see if it would make it show in my process manager. Hope those "Exiting" lines in the log didn't mean it was exiting for good...

Even if it did exit it would have only been till next boot ;)


You can mark this thread as solved if you like so others can benefit.

:guitar:

---

