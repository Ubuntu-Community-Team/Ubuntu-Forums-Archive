---
title: "Converting email to plain text"
date: 2008-06-05
forum: General Help
---

### Post by mohnkern on 2008-06-05
Here's an unusual problem:

I've got a mail spool on my machine /var/spool/mail/<userid> that I'd like to take, and strip all the headers from and write to a file, so I have the plain text of the message body, and nothing else.

Is there a script out there, or a .procmailrc recipe that does this?

---

### Post by sdennie on 2008-06-05
Here is a script shamelessly ripped from Unix Power Tools.  I've not tried it though:

```

#! /bin/sh
case $# in
0)  exec sed '1,/^$/d' ;;
*)  for i
    do sed '1,/^$/d' "$i"
    done
    ;;
esac

```

---

### Post by mohnkern on 2008-06-05
hmmm.. Tried it a variety of ways, including:

./convertmail.sh /var/spool/mail/<username>

which is what I'd expect. 
and 

cat /var/spool/mail/<username> | ./convertmail.sh

Both gave me empty results.  

The principle is sound however, have to think about it some more, and read up on sed.

---

### Post by mohnkern on 2008-06-05
Well, it would have been helpful if there was something in the spool :).  Put the spool back in place, but now it's still displaying headers.

You'd think there would be some way using unix mail to say "show me all the bodies of the messages"  Kind of like a reverse from.

hmm.

---

### Post by sdennie on 2008-06-05
Here's a quick perl script that will do it (and would be easy to modify):

```

#!/usr/bin/perl

use strict;

use Mail::Box::Manager;

my $mgr    = Mail::Box::Manager->new;
my $folder = $mgr->open(folder => $ARGV[0] || $ENV{MAIL}, lock_type => "NONE");

print $_->body . "\n-----------------\n" for(@$folder);

```

To use it, you'll first have to

```

sudo apt-get install libmail-box-perl

```

If you don't want a seperator between messages, you can change the print line to:

```

print $_->body for(@$folder);

```

---

### Post by VMC on 2008-06-05
I'm sure AWk is up to the task. Can you supply the header/footer and leave the text as ..., so we can try stripping.

---

### Post by mohnkern on 2008-06-05
Bingo!  Thanks so much, every day I learn something new, even though I've learned a lot.

An explanation of what the project was for those curious:

Local commuter rail sends out email notices about problems.  However, when I'm sitting at the track, I don't want to have to surf through all of them just to figure out what's going on.

So, I set up a mail box on my local server, had the notices delivered to it, and wrote a cron job that takes the bodies of them, writes them to a web page, and resets at midnight.

Now I can open up a web page on my home server from my cell phone, see all of today's notices for the train line I ride, and its in an HTML format that's virtually plain text.  No graphics, no tables, just the info which tells me what's going on.

If anyone's curious, I can give them the URL.

---

### Post by sdennie on 2008-06-05
Sounds cool.  I don't know if you know perl or not but, it would be pretty easy to modify that script to make it print the body with html tags or other fancy things.

---

### Post by mohnkern on 2008-06-05
Already did it.  Headers, Title Tags, Horizontal lines, the whole thing.  I was missing the perl function.  I love perl.

---

### Post by sdennie on 2008-06-05
Glad to hear it's written in perl.

For future reference, the way I found the CPAN module to do that (and, in fact the way I find all CPAN modules) is with synaptic.  I just searched for "mail perl", noticed libmail-box-perl installed it and, based on the "mail-box" part of the package name, assumed that it would tell me exactly how to use it if I typed, "man Mail::Box".  Works every time.  ;)

---

### Post by mohnkern on 2008-06-05
Good choice.  I'm pretty sure there's a time traveling module for perl, but if I search for it, I'll create a paradox.

---

