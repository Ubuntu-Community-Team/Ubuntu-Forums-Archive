---
title: "stdin redirection and finding my external IP"
date: 2005-06-08
forum: General Help
---

### Post by Zifnab on 2005-06-08
Three things I'm trying to figure out...

Thing one:
I know you can use < to redirect stdin to a file. What if I just want to redirect to a string I append to the end of the command line? My friend assures me I can but told me to figure it out myself, but I researched and  can't figure it out so now I'm cheating and asking here. :D

Thing two:
What is a simple command with parsable output that will tell me what my home network's external IP address is? I can get my internal IP easily enough, but that isn't doing me any good. (Yes, I can just look at the router's interface or use ipchicken.com or the like, but I want to do this in a script.)

Thing three:
I want to be able to SSH (or more specifically, use scp) in an automated script (to, you guessed it, send a file containing my external IP to a remote machine), but am loathe to put the password in plain text, as this password is even more important than the root password of my machine. Is there a way I can store it not-in-plain-text that will still be usable by ssh/scp and the like?

Thanks!

---

### Post by Takis on 2005-06-08
[QUOTE=Zifnab]Two things I'm trying to figure out...

Thing one:
I know you can use < to redirect stdin to a file. What if I just want to redirect to a string I append to the end of the command line? My friend assures me I can but told me to figure it out myself, but I researched and  can't figure it out so now I'm cheating and asking here. :D
[/quote]
If you have a text file 'mytext', with the string "this is some text", the following are equivalent from the program's point of view:
```
$ ./myprogram < mytext
$ echo "this is some text" | myprogram
```

> What is a simple command with parsable output that will tell me what my home network's external IP address is?
So your box is behind another box (e.g. a hardware firewall or a router) which has the IP you're after? This is pretty difficult to do, if that's the case.

---

### Post by Takis on 2005-06-08
[QUOTE=Zifnab]
Thing three:
I want to be able to SSH (or more specifically, use scp) in an automated script (to, you guessed it, send a file containing my external IP to a remote machine), but am loathe to put the password in plain text, as this password is even more important than the root password of my machine. Is there a way I can store it not-in-plain-text that will still be usable by ssh/scp and the like?[/QUOTE]
Not any GOOD way (IMO). Seriously, do you absolutely need to store your password? Why not let it prompt you each time? I have some scripts I use to synchronise my uni work with what I have at home, and I still put in the password every time.

---

### Post by Zifnab on 2005-06-08
Heh, well it's just because of what I'm trying to do.

My home network is on a cable modem, so it has a dynamic IP. I often SSH into my computer from elsewhere, so if my ISP happens to change my IP on me, I'm screwed until the next time I go home and check it.

Note that this is NOT a huge nuissance - I decided to conquer this problem mostly just to see if I could do it. To improve my Linux skillz, if you will.

So what I'm trying to do is cron a script that will check my external IP every hour and, if it is different than the last time it checked, upload a file containing the new IP to my university webspace (which has limited space and allows only HTML). So I can check on the IP if I want.

---

### Post by rosslaird on 2005-06-08
You should be able to get a static IP from your cable provider if it's important to get this working (my provider charges an extra 3 bucks a month for this, I think).

And even if you don't have a static IP, it shouldn't change more than a few times a year.

---

### Post by Zifnab on 2005-06-08
Heh, I know it only changes a few times a year; as I said, this is more of an exercise. A challenge to myself.

---

### Post by Takis on 2005-06-09
[http://www.no-ip.com/services/page/free/dynamic/dns](http://www.no-ip.com/services/page/free/dynamic/dns)

Edit: Even if it defeats the purpose of this thread...

---

### Post by word_virus on 2005-06-09
[QUOTE=Zifnab]Three things I'm trying to figure out...

Thing two:
What is a simple command with parsable output that will tell me what my home network's external IP address is? I can get my internal IP easily enough, but that isn't doing me any good. (Yes, I can just look at the router's interface or use ipchicken.com or the like, but I want to do this in a script.)
[/QUOTE]

Use a shell script to point lynx or dog (a "cat" replacement) at whatismyip.com or something similar then call sed to parse the output down to the relevent information.

> 
Thing three:
I want to be able to SSH (or more specifically, use scp) in an automated script (to, you guessed it, send a file containing my external IP to a remote machine), but am loathe to put the password in plain text, as this password is even more important than the root password of my machine. Is there a way I can store it not-in-plain-text that will still be usable by ssh/scp and the like?


I think SSH will let you use a hash of your password for this?

---

### Post by Kophein on 2008-03-01
I was trying to do the same thing.
Based on word_virus's hint, I got to the following satisfactory result:

```
dog http://www.showmyip.com | grep Connection > /tmp/result.txt
```

All you need is to install dog, and then set your system to automatically run this command and send let's say an e-mail to yourself with the file results.txt attached.

Hope this helps.

---

