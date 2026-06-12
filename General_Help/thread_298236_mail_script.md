---
title: "mail script"
date: 2006-11-12
forum: General Help
---

### Post by jmvidalvia on 2006-11-12
Can anybody help me with a simple script?
It should send a mail (I already have mailx and postfix running), with a fixed subject an the content of a short text file as the body of the mail.
Thanks in advanced!

---

### Post by kidders on 2006-11-12
Hi there,

You can do that with a single command, really. Try putting this in a text file called, say, "test"...

```

To: someone@wherever.com
Subject: A test message
From: "Joe Bloggs" <jbloggs@wherever.com>
Content-Type: text/plain; charset="ISO-8859-1"

Hello there

.
```

Then type **sendmail -t < test**

---

### Post by jmvidalvia on 2006-11-12
Thank you very much!
It works fine (I guess this is much simpler than mailx)
To be perfect, ¿can the body 
"Hello there

."
come from a different file?
I mean, one file for the header and a different one for the body...
Is that possible?
Thanks again

---

### Post by jmvidalvia on 2006-11-12
I solved it by myself with:
cat

Thanks again!

---

### Post by kidders on 2006-11-12
**Edit:** Kewl... you solved it.

Yep :-)

Strictly speaking, some sort of header is a good idea (for the sake of sticking stringently to international standards), but you *can* leave it out altogether if you like, and replace most of it with command line arguments to the "sendmail" command. Take a look at sendmail's man page for info.

Anyhow, you're clearly looking for something more elabourate, so let's try this:

Create a new test file containing:```
To: someone@wherever.com
Subject: A test message
From: "Joe Bloggs" <jbloggs@wherever.com>
Content-Type: text/plain; charset="ISO-8859-1"

Automated message -- do not respond

!BODY!

Isn't this pretty :-)

.

```
Now type **sed 's/!BODY!/Testing/' test**. That should give you some idea of the kinds of things that are _easy_ to do with scripting.

Another idea might be:

```
#!/bin/bash

if [ -z "$1" ]; then
	echo "Please at least specify a recipient!";
	exit
fi

if [ -z "$2" ]; then
	BODY="/path/to/default/body"
else
	BODY="$2"
fi

sendmail $1 < $BODY
```

---

### Post by jmvidalvia on 2006-11-12
I didn't know the sed command.
I think i will use this way.
Thanks a lot again!

---

### Post by kidders on 2006-11-12
Sed is quite powerful. I only tend to make quite humble use of it myself though ... I like it's "swap" function, for doing things like **USER_LIST=`grep "^admin:" /etc/group | sed 's/.*\://' | sed 's/,/ /g'`** to get member lists for groups.

It strikes me that something like that could be handy for a script-based mailer, in that you could then do something like **for i in $USER_LIST; do /usr/local/bin/mailer $i; done** to send mail to lots of people at once, or something.

Anyhow... all the best :-)

---

### Post by jmvidalvia on 2006-11-27
¿Does anybody know how to attach a file using this sistem: "sendmail -t < filewithheader"? Or any other...?
Many thanks!

---

