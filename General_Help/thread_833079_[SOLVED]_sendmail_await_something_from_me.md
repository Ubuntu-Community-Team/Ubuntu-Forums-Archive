---
title: "[SOLVED] sendmail await something from me"
date: 2008-06-18
forum: General Help
---

### Post by mizar001 on 2008-06-18
I wrote a script , trying the perl way and the bash way, that attempt to send a mail using sendmail.

But during the script, when i call 'sendmail' it hangs, awaiting for the special CTRL+Z to stop the process.

Only after that i can see my mail received correctly.

Obviously i don't want to press that special key to terminate the process every time, because i'm going to scheduling that.

Some scripts in internet do not mention this clear problem... and even the perl scripts does work as others.

The script i used last time is this :
```

#!/usr/bin/perl
 
$title='Tracker mail';
$to=$ARGV[0];
$from=$ARGV[0];
$subject=$ARGV[1];

print "Sending mail to $to with subject $subject\n";
 
open(MAIL, "|/usr/sbin/sendmail $to");
 
## Mail Header
print MAIL "From: $from\n";
print MAIL "Subject: $subject\n\n";
## Mail Body
print MAIL "Hello from tracker\n";
 
close(MAIL);



```

---

### Post by HalPomeranz on 2008-06-18
Your code works fine on my system.  Perhaps there's a mail configuration issue on your machine rather than a mistake in the code?

---

### Post by mizar001 on 2008-06-19
I installed sendmail without any customized configuration and the log is only warning me that (mail.err): 
```

...
My unqualified host name (mizar-desktop) unknown; sleeping for retry
...
Jun 19 08:51:05 mizar-desktop sm-mta[7004]: unable to qualify my own domain name (mizar-desktop) -- using short name

```

---

### Post by mizar001 on 2008-06-19
SOLVED. Thanks. It was a problem in the qualified name. I have to put this line in the /etc/hosts file :
```

127.0.0.1	localhost.localdomain localhost mizar-desktop

```

Where localdomain could be any of my domains.

---

