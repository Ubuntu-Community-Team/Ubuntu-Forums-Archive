---
title: "access_log too big to open in nano"
date: 2008-06-23
forum: General Help
---

### Post by shavenlunatic on 2008-06-23
Hi,

I need to read the apache2 access_log, unfortunately as I'm new to this I didn't know how quickly it could grow so big (few weeks and it's at 2.5GB)

I needed to check something in it but nano can't open it, after a few seconds it advises that it ran out of memory (via SSH to my dapper webserver) and I don't really want to download a 2GB text file.

Is there anything I can do?  I only really care about the log over the last few days to be honest, anything before that I am happy to lose.

(also, as a side note, is this a normal size for the access_log to get to? and is it an easy enough job to clear it out?)

---

### Post by dracayr on 2008-06-23
Why are you loading it into an editor? you only need to view it (use *less* instead of *nano*). You can also view only the last lines by executing this:

```
tail -n *numberOfLines* /path/to/file/access_log|less
```

dracayr

---

### Post by beckols on 2008-06-23
instead of trying to open it with a text editor, just use head/tail to get the logs from the last few days.
I'm assuming new log entries are appended to the bottom, so you want to use something like this:
```
tail -n 20 /path/to/access_log
```
where "20" is the number of recent lines you want to see, you might have to keep increasing this number until you get the amount of lines you need.
If the new entries are at the top of the log file, replace "tail" with "head"

If you want to save the output of that command just redirect it into a file:
```
tail -n 39 /path/to/access_log > ~/filename
```

---

### Post by brian_p on 2008-06-23
> **shavenlunatic said:**
> Hi,

I need to read the apache2 access_log, unfortunately as I'm new to this I didn't know how quickly it could grow so big (few weeks and it's at 2.5GB)

I needed to check something in it but nano can't open it, after a few seconds it advises that it ran out of memory (via SSH to my dapper webserver) and I don't really want to download a 2GB text file.

Wouldn't you be transferring the data anyway in order to read it? You could try vim.


> Is there anything I can do?  I only really care about the log over the last few days to be honest, anything before that I am happy to lose.

Split the file into manageable chunks. (See man split).

> (also, as a side note, is this a normal size for the access_log to get to? and is it an easy enough job to clear it out?)

It does seem excessive but that would depend on what you are logging. The apache configuration and logrotate are two places to seek to control the file size.

---

### Post by beckols on 2008-06-23
He only needs to view the logs, so opening into any kind of editor is a waste of time.

---

### Post by shavenlunatic on 2008-06-23
thanks :)  this may be more of a headache that it;s worth,

To give an idea of the file, I did it for the last 10,000 lines... and it gave me 6 minutes of info :O

I fear this is going to become a problem managing the sheer volumes of it, is it an essential file or could I just disable it unless I have a problem and just re-enable it to diagnose?

---

### Post by beckols on 2008-06-23
Wow, that's a lot of traffic... Well I looked for a way to set the verbosity of the logging, but I couldn't find it... it's possible I missed it though.  To keep it from taking too much space you should set a cron event that rotates your logs, and then you can delete older ones if you need the space.  Check out this link on how to accomplish this:
[http://httpd.apache.org/docs/2.0/logs.html#rotation]("http://httpd.apache.org/docs/2.0/logs.html#rotation")

---

### Post by shavenlunatic on 2008-06-23
thanks very much, I'll take a read into it

And it's a live browser based game built on constant ajax calls to php files... so yeah.. it seems we may have underestimated how much the server would be getting hammered..lol

---

### Post by brian_p on 2008-06-23
> **shavenlunatic said:**
> thanks very much, I'll take a read into it

There is no need to involve cron. A simple change to one line in   /etc/logrotate.d/apache2 would suffice.

[http://www.debianhelp.co.uk/logwatch.htm](http://www.debianhelp.co.uk/logwatch.htm)

and

[http://www.ducea.com/2006/06/06/rotating-linux-log-files-part-2-logrotate/](http://www.ducea.com/2006/06/06/rotating-linux-log-files-part-2-logrotate/)

---

