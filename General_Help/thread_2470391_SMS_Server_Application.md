---
title: "SMS Server Application?"
date: 2021-12-28
forum: General Help
---

### Post by tornbarb on 2021-12-28
I’ve spent a few months digging through a lot of documentation, but I’m not sure if I’m missing something or not really searching for the correct terminology to help me.
 
Context: 
 
I use postfix to send (with script) alerts within my server clusters.  It works great, but I’m not that disciplined to look at my email constantly for those alerts.
 
Question:
 
I’m toying around with the idea of setting one of my servers to drive messages to me via sms, however; I’m at a complete loss on how to go about this.
 
I’ve seen KDE efforts, signing up for a third party service, etc.  But I really want all this contained on my server and just have the server send sms to me directly.
 
Any ideas?  Thoughts? Opinions?  
 
If this is not a valid post, and I’ve missed something searching the forums, please let me know.

---

### Post by rsteinmetz70112 on 2021-12-28
Most wireless providers have a email to text gateway. You send an email to <phonenumber>@txt.att.net for att, there is a similar number for MMS <phonenumber>@mms.att.net. You may need to modify your scripts for the messages to work as texts.

There are sms tools for linux  that I've never used but they may require a wireless modem.

---

### Post by tornbarb on 2021-12-29
Wow....  That was too simple of a fix.  I guess I was over thinking it and trying to setup an actual SMS server, which might have been way over my head to do.  I modified one of my scripts to adjust for the new way of sending me the data and it worked.  Although slow, it worked for the application I need on a daily basis.

So for anyone trying, the bash code (if using mutt, because I'm a simpleton):

[I][COLOR=#ff0000]cat (file with data here) | mutt -s "subject line" <your phone number no dashes>@<email to text gateway>
[/COLOR][/I]
Appreciate the help....

---

### Post by unixrlz on 2021-12-29
> **rsteinmetz70112 said:**
> Most wireless providers have a email to text gateway. You send an email to <phonenumber>@txt.att.net for att, there is a similar number for MMS <phonenumber>@mms.att.net.

Thank you so much! I had no idea AT&T had this option. This will work great for me, I just had to say thanks!!

---

### Post by TheFu on 2021-12-29
> **tornbarb said:**
> Wow....  That was too simple of a fix.  I guess I was over thinking it and trying to setup an actual SMS server, which might have been way over my head to do.  I modified one of my scripts to adjust for the new way of sending me the data and it worked.  Although slow, it worked for the application I need on a daily basis.

So for anyone trying, the bash code (if using mutt, because I'm a simpleton):

[I][COLOR=#ff0000]cat (file with data here) | mutt -s "subject line" <your phone number no dashes>@<email to text gateway>
[/COLOR][/I]
Appreciate the help....

Mutt?  I use 'mail'.  
Also, no need to use cat.  People use cat all too often (it is a pet peeve of mine).  Just redirect stdin into the program.
```
$ mail -s "subject" you@domain.com < file-with-data
```
If being run from a script, use full paths.
```
/usr/bin/mail -s "Good Morning" you@gmail.com  < /home/me/morning.txt
```
Never trust the PATH in any script.

---

