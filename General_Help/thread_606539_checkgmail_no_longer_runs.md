---
title: "checkgmail no longer runs"
date: 2007-11-08
forum: General Help
---

### Post by _simon_ on 2007-11-08
Since yesterdays updates, checkgmail will not run.

Here is the error:

```

Specification mandate value for attribute Tamed
attributes construct error at /usr/lib/perl5/XML/LibXML/SAX.pm line 64
 at /usr/share/perl5/XML/Simple.pm line 299
A thread exited while 2 threads were running.

```

Any ideas?

Line 64 is  $args->{ParseFunc}->($args->{LibParser}, $args->{ParseFuncParam});
Line 299 is     $tree = $sp->parse_string($$string);

I've tried cgmail as a replacement but it doesn't check labels.

---

### Post by _simon_ on 2007-11-08
ok I fixed it.
It wasn't the updates, I remembered that I added a new label to check. It seems that it doesn't like spaces in label names!

If anyone else has this problem then view hidden files in your /home
Find .checkmail
Open prefs.xml with a text editor and remove the offending label
Now checkgmail will run.

---

### Post by pihbar on 2008-03-26
Yup, no weird label names. I had the character "<" in one of my labels and it failed to start



lame

---

