---
title: "How to make Apache web server have an indicator in my panel in gnome?"
date: 2008-01-02
forum: General Help
---

### Post by inktri on 2008-01-02
Is there some indicator like the System Monitor to show whether Apache is up and running/stopped/restarting, etc.?

Thanks for the help

---

### Post by inktri on 2008-01-02
ANyone know?

---

### Post by p_quarles on 2008-01-02
I'm not aware of any panel apps that would do this, but I can see it being pretty easy to set something like this up with Conky. 

On the other hand, Apache is pretty sturdy, so honestly I wouldn't even bother with this. Unless you've had a problem with it crashing?

---

### Post by scxtt on 2008-01-02
you could have a cron/script that checks to see if it's running (maybe "**if ps -ef | grep -c apache2** < 1") and uses xmessage to pop up a message on your screen when it's not running ...

that being said, i've never had apache act up on me (ever :))

---

### Post by ayenack on 2008-01-02
Try this.

**sudo /etc/init.d/apache status**

Or type top in terminal to see what's running.

---

### Post by p_quarles on 2008-01-02
> **ayenack said:**
> Try this.

**sudo /etc/init.d/apache status**

Or type top in terminal to see what's running.
If the OP had wanted a command line solution, it would be easier just to run:
```
ps aux | grep apache
```

---

### Post by ayenack on 2008-01-02
> **p_quarles said:**
> If the OP had wanted a command line solution, it would be easier just to run:
```
ps aux | grep apache
```

To be honest I did not read the question properly. It's late here and I'm not fully switched on at the moment. But you're right.

---

### Post by p_quarles on 2008-01-02
> **ayenack said:**
> To be honest I did not read the question properly. It's late here and I'm not fully switched on at the moment. But you're right.
No worries.

But -- "late"? If I remember my GMT correctly, it would actually be tending toward early in your corner of the globe, no? ;)

---

### Post by ayenack on 2008-01-02
04:54:49 Secs to be precise and I'm totally shattered but that's another story all together.

---

### Post by scxtt on 2008-01-03
i've got xmessage sending me a message running as a while loop that sleeps, then checks every 3 minutes ... right now, it's popping up saying "it's running" / "it's NOT running" -- you could have it that way or only send a message if it's NOT running ...

i'm pretty sure if i set **export DISPLAY=localhost:0.0** w/in the script i could make it so it's a cron job ... but you could just add the script to your startup session - same difference really (maybe not, those *sleep 180* commands seem to waste CPU cycles, but i've got it working as a cron :)) ...

any interest?

---

### Post by ayenack on 2008-01-04
Now that I'm awake and a with it again you could do this, using /etc/init.d/apache status again. In terminal.

**sudo watch -n5 /etc/init.d/apache2 status**

This will display a nice little gnome-terminal checking every five seconds to see if your chosen app is running. You could add this as a launcher on your menu bar and just start it every time you log in making sure to click on "run in terminal" and it'll just sit there displaying the status of Apache or whatever. If you want it to update less frequently change the number after "-n" so 60 would be a minute and so on.

Not very elegant but it should work.

Edit: The above will not work as apache2 does not have option "status" my mistake.

There's also the Apache mod_status in /apache2/apache2.conf file you'll need to uncomment it to use it. Take a look at this.

[http://www.debuntu.org/apache-activity-performance-mod_status](http://www.debuntu.org/apache-activity-performance-mod_status)

---

