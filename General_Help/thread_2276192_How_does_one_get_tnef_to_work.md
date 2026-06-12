---
title: "How does one get tnef to work"
date: 2015-04-30
forum: General Help
---

### Post by cigtoxdoc on 2015-04-30
The following DOES NOT work: tnef -f winmail.dat

The above does not do anything.

john

---

### Post by cigtoxdoc on 2015-05-14
I posted this over a week ago and no replies.  Am I the only one getting tnef e-mail?  Where does one go for help, if no one answers questions on this forum?

The following DOES NOT work: tnef -f winmail.dat

The above does not do anything.

john

---

### Post by Vladlenin5000 on 2015-05-14
[http://bernaerts.dyndns.org/linux/74-ubuntu/282-ubuntu-winmail-dat-thunderbird-nautilus](http://bernaerts.dyndns.org/linux/74-ubuntu/282-ubuntu-winmail-dat-thunderbird-nautilus)

Please do not open multiple threads for the same issue. You're welcome to bump after a reasonable time.

---

### Post by Bucky Ball on 2015-05-14
*Threads merged.*

Please do NOT duplicate post. If you are seeing no action on your thread (someone posted on your original thread an hour ago) after a reasonable amount of time, rather than posting a duplicate thread regarding the same issue, simply post 'bump' and that will put your thread back at the top of the list .

Posting in the correct section will also help your cause, therefore:

*Thread moved to **General Help**.*

Good luck.

---

### Post by steeldriver on 2015-05-14
What is the output of 

```

tnef -tvf winmail.dat

```

What happens if you run it with the interactive switch (-w)

```

tnef -wf winmail.dat

```

---

### Post by SeijiSensei on 2015-05-14
> **cigtoxdoc said:**
> Am I the only one getting tnef e-mail?
Millions of people receive mail with TNEF attachments every day.  Aside from your problem with the tnef program, what are you trying to accomplish?

TNEF is a Microsoft technology that doesn't always work very well with non-MS clients.  Can you open the message in Outlook?  Does that help?

---

### Post by cigtoxdoc on 2015-05-14
Apparently, i may be one of the few who is using Ubuntu for a business purpose.  I would not have asked the question if I were not getting e-mail that comes across as winmail.dat or similar.  There are posts on this forum that report that tnef works.  I have a Canonical support agreement.  One would think that Canonical would want to many more Ubuntu users.  Therefore, software needs to work with files coming from businesses that use MS software.

John

---

### Post by cigtoxdoc on 2015-05-14
output of tnef 1.4.9-1

johnl@john-Vostro-3500:~/Downloads$ tnef -tvf winmail.dat
johnl@john-Vostro-3500:~/Downloads$ tnef -wf winmail.dat
johnl@john-Vostro-3500:~/Downloads$ tnef -tvf wm43015.dat

---

### Post by steeldriver on 2015-05-14
Well that's a bit of a puzzle - I have the same version installed on my 14.04 system and have tested it on a small number of winmail.dat files. I can't find any circumstance (missing file, zero length file) in which it produces **no** output to the terminal - even without the -v (verbose) switch

The only thing I can think is that your version of tnef is aliased, or there is another executable of the same name in your PATH: what do the commands

```

type tnef

tnef --version

```

say?

---

### Post by cigtoxdoc on 2015-05-14
johnl@john-Vostro-3500:~$ type tnef
tnef is /usr/bin/tnef
johnl@john-Vostro-3500:~$ tnef --version
tnef 1.4.9
Copyright (C) 1999-2011 by Mark Simpson
Copyright (C) 1997 by Thomas Boll (original code)
tnef comes with ABSOLUTELY NO WARRANTY.
You may redistribute copies of tnef under the terms of the GNU General
Public License.  For more information about these matters, see the file
named COPYING.
johnl@john-Vostro-3500:~$ 

BTW, just upgraded to 15.04 and still same problem.  Also occurs on other PCs running 14.04

---

