---
title: "Environment variables set permanently"
date: 2013-01-30
forum: General Help
---

### Post by friedl on 2013-01-30
Hi all, 
I have a very strange case and need some assistance.

I want to use the debug on demand feature of rsyslog. For this, I need to set two environment variables. When I set these in a shell session and start rsyslog in the foreground, it works just fine.

But, I need to run rsyslog in the background. Then the set variables will not work. I need them to be either set permanently or at least be set when rsyslog is started.

I assumed, these might need to be set in the init script. But that didn't work out as well. I tried it with
[B]/etc/init.d/rsyslogd
/etc/init/rsyslog.conf[/B]
No chance with both files.

Googling around revealed **/etc/environment**. But setting the variables there had no change as well.

I could issue the command to start the debugging, but it did not work. That means, that the variables were not set.

Does any of you gurus have a clue for me on where to properly set the variables (permanently)?

Cheers,
Florian

---

### Post by omeomi on 2013-01-30
How did you set the variables in **/etc/environment**, because that should work?

Maybe it works better if you put them in **~/.pam_environment**, however you need to do that for every user on your system.

---

### Post by friedl on 2013-01-30
In  **/etc/environment **I set them like this:

RSYSLOG_DEBUG="DebugOnDemand NoStdOut" 
RSYSLOG_DEBUGLOG=/somepath/example.log

I will try  **~/.pam_environment**

---

### Post by friedl on 2013-01-31
I tried this with **~/.pam_environment** but the file was either not present or I am too stupid to access it.

Also  I did some more googling and found, that if I do it via this file, I  have to insert it into this file for every user. Is this correct?

---

### Post by rnerwein on 2013-01-31
> **friedl said:**
> I tried this with **~/.pam_environment** but the file was either not present or I am too stupid to access it.

Also  I did some more googling and found, that if I do it via this file, I  have to insert it into this file for every user. Is this correct?
hi
as i know (in system V it's the default) you can send the syslogd the signal USR1.
have a look at: man rsyslogd. this signal cause the rsyslogd to switch the debug on/off (toggle).
cheers

---

### Post by friedl on 2013-02-13
> **rnerwein said:**
> hi
as i know (in system V it's the default) you can send the syslogd the signal USR1.
have a look at: man rsyslogd. this signal cause the rsyslogd to switch the debug on/off (toggle).
cheers

I know how this works. But, this only works when running rsyslog in the foreground. But I need to run it in the background AND have debug on demand enabled.

---

