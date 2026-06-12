---
title: "Ubuntu Logging Me Off (maybe restarting) Constantly"
date: 2024-09-08
forum: General Help
---

### Post by newuser100 on 2024-09-08
I recently set up my HP Elite desk 705 mini PC with ubuntu. All seems well... I start running bitcoin core as the only program on the machine. Things seem to be syncing just fine (about 43% in). 

Well every time I come back to check on it I have to log back on to ubuntu and re-start bitcoin core.... not sure what's going on. I've changed all the power and privacy settings to stop the screen from going blank and auto logging off. 

Anyone have any ideas on what's going on with my system?

---

### Post by TheFu on 2024-09-08
The **uptime** command will tell you if it is rebooting.
Other than that, you'll need to look at the system log files.  help.ubuntu.com has a section on that.  Either journalctl can be used or the files are in /var/log/, but if you are as new as you seem to be, you'll want to find and read the help first.

---

### Post by newuser100 on 2024-09-08
Using the uptime command it does appear the system is rebooting. 

These are the logs... I think the last rebot was around the 9:13am mark:

[https://image.nostr.build/1b33192523c79334114b633202f7512eb5dc2197d0da0003b024fa2b3684d50f.png](https://image.nostr.build/1b33192523c79334114b633202f7512eb5dc2197d0da0003b024fa2b3684d50f.png)

---

### Post by newuser100 on 2024-09-08
Went down again around 10:55; more logs:

[https://image.nostr.build/07012dd3573ad58c849a2191d26ef484400c074f5b7f9c2117b0292d5e0065a4.png](https://image.nostr.build/07012dd3573ad58c849a2191d26ef484400c074f5b7f9c2117b0292d5e0065a4.png)

---

### Post by newuser100 on 2024-09-08
It appears like it's something to do with running bitcoin core... I've not run core and it's still online

---

### Post by newuser100 on 2024-09-08
Maybe there is a way I can manually limit the CPU usage of Bitcoin Core? Just watching it while it's running I don't see anything crazy on the Memory side. CPU cores are running pretty high. Very odd.... The machine isn't that old...

---

### Post by TheFu on 2024-09-09
> **newuser100 said:**
> Using the uptime command it does appear the system is rebooting. 

These are the logs... I think the last rebot was around the 9:13am mark:

[https://image.nostr.build/1b33192523c79334114b633202f7512eb5dc2197d0da0003b024fa2b3684d50f.png](https://image.nostr.build/1b33192523c79334114b633202f7512eb5dc2197d0da0003b024fa2b3684d50f.png)

I'm paranoid.  I don't click random links posted on the internet. 
Posting images of logs is crazy.  They are text.  More importantly, YOU need to review the logs and determine what's wrong.  Generally, you find the very first warning/error in the log file, take that (removing system specific stuff) and use that in a google search to see what others have discovered about the problem AND what they've done to fix it.  Things like the hostname or the timestamps shouldn't be included in the search.

I'm not paid enough ($0) to review other people's log files.  It is a skill you need to learn.  If you system is running fully utilized for hours and hours and hours, then you need to ensure there is sufficient cooling for all components.  That's common sense.  Watch the temperatures for everything inside that you can. There are usually about 5 of them that can be watched, but it depends on the "sensors" package setup for your specific hardware what can and cannot be monitored.  

Most of the time, a good system will throttle performance rather than crash.  Throttling events should be in the logs and say something related to "thermal" as the cause.

Just guesses.

Please don't post imaged of text.  Just copy/paste the ***_RELEVANT_*** text into the these forums and use the Advanced Editor to wrap them in 'code-tags' so the formatting is retained.  That's the '#'  button. Works just like quoting or bold or italics buttons work.

I haven't done anything related to bc in about 15 yrs, so I cannot help with any specifics about that.

You can lower the priority of work on a process by process basis using the "**nice**" command, but if the system isn't doing anything else, it will still use all the CPU and overheating will still be a problem.  nice is there to make long running batch tasks release CPU cycles for more immediate tasks.  For example, when I'm transcoding videos, I run that at a high nice level so that any other work I'm doing on the system has priority and isn't impacted. OTOH, the CPU cores are kept really busy the entire time, CPU-based transcoding makes for much better quality and smaller files than using the GPU hardware for transcoding.  For quick transcoding where quality isn't very important, I do sometimes, force the GPU to be used, but the quality is noticeably bad even with huge file sizes allowed.  For the most part, I've stopped using GPU-based transcoding due to that.  OTOH, GPU-based transcoding doesn't hit the CPU in any noticeable way.  Sometimes that can be important to some people (not me).

---

### Post by newuser100 on 2024-09-09
I'm communicating on this thread with my main PC that's remoting into the ubuntu machine. This is why I screen shotted them. 

ChatGPT has been helping

---

### Post by TheFu on 2024-09-09
> **newuser100 said:**
> I'm communicating on this thread with my main PC that's remoting into the ubuntu machine. This is why I screen shotted them. 

ChatGPT has been helping

To copy text, use the built-in select/paste method that every terminal supports.
You do realize that AI answers are wrong (incomplete/lies) about 50% of the time, right?

---

