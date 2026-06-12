---
title: "Authentication token manipulation error"
date: 2016-06-05
forum: General Help
---

### Post by Gnusboy on 2016-06-05
I'm at wits end. I've been trying to find/change my root password with no luck at all. I've followed Psychocat's tips, read through many forum posts, and still can't seem to find out how to do it.

I can get through the "drop to root shell" etc. and on the enter new Unix password. I enter a new passwd and re-enter it, but then I get an error message "authentication token manipulation error"
"password unchanged"

I did read through the forum threads on this problem, but all of those forums are closed and the newest answer is from 2012. 
I'm using Ubuntu 14.04 with an internal partitioned HDD and also have n external HDD thatI "think" has been unmounted and unplugged. I'm unclear about the terminal commands to create new directories and concerned about doing some more major damage to my system.
I have not tried using the Live CD method yet, because I don't want more possible problems.

I am also having several system issues related to this, but I'll wait until I can fix the primary problem first.

So, if y'all can help figure this out I will really appreciate it. Thanks in advance.

---

### Post by Gnusboy on 2016-06-05
Oh, I forgot to mention that when I follow the steps that don't work and "exit" I get another message
"System error detected do you want to report it?"
That offers options to send a report, which requires my password, or cancel.
Don't know if that's important, or will it go away once I take care of the main issue.

---

### Post by steeldriver on 2016-06-05
The filesystem is mounted 'read-only' when you boot in recovery mode - hence the `passwd` command can't write your changes to the system

You need to remount the filesystem root with read-write permissions before running the passwd command:

```

mount -o remount,rw /

```
(note: no space between the 'remount,' and the 'rw')

Hope this helps

---

### Post by Gnusboy on 2016-06-05
Hey steeldriver
Thanks it worked. I was able to send the problem report. When I looked over the problem report one thing jumped out
Internal Error
Problem type kernal Oops

does this have to be dealt with, or is it just a thing?

---

