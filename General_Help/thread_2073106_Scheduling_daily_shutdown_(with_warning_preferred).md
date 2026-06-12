---
title: "Scheduling daily shutdown (with warning preferred)"
date: 2012-10-19
forum: General Help
---

### Post by bogdarnet on 2012-10-19
Okay, so the problem is, I have a bad habit of staying up all night posting progressively dumber messages on internet forums.  

In other words, making sure the computer shuts down every night at midnight (or earlier if I get ambitious), would be wonderful.

So I looked at options, appear to be crontab and gnome-schedule...

Okay, gnome-schedule looks easier...

Okay, I got it to shutdown using "sudo gnome-schedule" and "/sbin/poweroff"

But... what if I'm in the middle of something at that point?  How do I get a warning?  So I tried "/sbin/shutdown/ -k 23:59"  (I know, the -k won't really shutdown, but I'm still testing at the moment, want to get the warning.)

Now when I tried that in the terminal, it gave me a warning message.  But when I put it in gnome-schedule, I get nothing.

Okay, well, what if I open a text file with a warning first?  Tried putting "/usr/bin/gedit" in a gnome-schedule, but nothing shows up...

Am I missing a shortcut here, some easy way to do what I want?

I thank you heartily in advance for your help with this!

---

### Post by fullmoonguru on 2012-11-22
Did you figure this out?  Mine shuts down every night at midnight...sometimes while I'm working.

---

### Post by bogdarnet on 2013-02-04
No.  I do get a message that it's shutting down, but then it doesn't shut down.  Maybe it's shutting yours down?  (Just joking!)

---

### Post by sudodus on 2013-02-04
> **bogdarnet said:**
> No.  I do get a message that it's shutting down, but then it doesn't shut down.  Maybe it's shutting yours down?  (Just joking!)

Did you remember to remove the -k option?

```
/sbin/shutdown/ -k 23:59
```

And are you running the command with root permissions (sudo)?

---

### Post by stinkeye on 2013-02-04
Why not use as the command.
```
gnome-session-quit --power-off
```
Test in the terminal first because I have gnome-session-fallback installed as well, so not sure if it works in default Ubuntu.

Run gnome-schedule as a normal user (without sudo) and set up the schedule.
Set it as an x-application and you will get a 60 second confirmation dialogue.

---

### Post by fullmoonguru on 2013-02-05
I'm using mint/mate these days.  No mate-session-quit command.

---

### Post by sudodus on 2013-02-05
I suggest to run cron as root. Edit the table with ```
sudo crontab -e
``` and enter two last lines, for example
```

# min hour dom month dow  command
   58  23   *    *    *   /sbin/shutdown -P +2
   59  23   *    *    *   /usr/bin/espeak 'Shutting down in one minute. Go to bed, please!'

```[FONT=Courier New]
--
[COLOR=DarkOrange]Test[/COLOR] it each minute with stars 'everywhere' and reset to midnight when you know it works.
[/FONT]
```

# min hour dom month dow  command
   [COLOR=DarkOrange]*   *[/COLOR]   *    *    *   /sbin/shutdown -P +2
   [COLOR=DarkOrange]*   * [/COLOR]  *    *    *   /usr/bin/espeak 'Shutting down in one minute'

```[FONT=Courier New]
[/FONT]

---

### Post by stinkeye on 2013-02-05
> **fullmoonguru said:**
> I'm using mint/mate these days.  No mate-session-quit command.
Oh well, I was posting a solution on an ubuntu forum thread prefixed with Ubuntu. Wasted my time there, eh.

---

### Post by sudodus on 2013-02-05
> **stinkeye said:**
> Oh well, I was posting a solution on an ubuntu forum thread prefixed with Ubuntu. Wasted my time there, eh.
Often we are not told enough to really help. 'A good description of the problem is almost a solution.'

---

### Post by fullmoonguru on 2013-02-05
Well back in November when I posted, I wasn't using Mate.  Anyway this got me interested again because I've never had a good solution.  So I ended up making a script that seems to work well.  My first script!!

Now I just need to find out why cron isn't working...

bogdarnet, this script does exactly what we're looking for.  It will come up with a dialog box that says the computer will shut down in 2 minutes & asking if you want to continue with the operation.  Click "No" & it goes away, click "Yes" or do nothing & it will shut down. 

This uses zenity so you need to have that installed.  Not sure about 'buntu but it was already in my Mint machine.

Extract & copy the script into /usr/bin

In the terminal:

sudo chmod +x /usr/bin/autoshutdown

Test in terminal:

sudo /usr/bin/autoshutdown

If it works you can sudo gnome-schedule to open as root & set up a task with "/usr/bin/autoshutdown" (no quotes).  That should do it.

---

### Post by bogdarnet on 2013-02-07
> **sudodus said:**
> I suggest to run cron as root. Edit the table with ```
sudo crontab -e
``` and enter two last lines, for example
```

# min hour dom month dow  command
   58  23   *    *    *   /sbin/shutdown -P +2
   59  23   *    *    *   /usr/bin/espeak 'Shutting down in one minute. Go to bed, please!'

```[FONT=Courier New]
--
[COLOR=DarkOrange]Test[/COLOR] it each minute with stars 'everywhere' and reset to midnight when you know it works.
[/FONT]
```

# min hour dom month dow  command
   [COLOR=DarkOrange]*   *[/COLOR]   *    *    *   /sbin/shutdown -P +2
   [COLOR=DarkOrange]*   * [/COLOR]  *    *    *   /usr/bin/espeak 'Shutting down in one minute'

```[FONT=Courier New]
[/FONT]

This worked fine.  Marking thread solved.

---

