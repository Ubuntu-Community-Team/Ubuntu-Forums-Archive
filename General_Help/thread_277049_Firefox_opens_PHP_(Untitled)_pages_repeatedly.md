---
title: "Firefox opens PHP (Untitled) pages repeatedly"
date: 2006-10-13
forum: General Help
---

### Post by beckejc on 2006-10-13
This problem is strange:

I put this file on my desktop, indextest.php

When I open it with Firefox, I get (Untitled) windows opening one after the other until I shut Firefox down.

Any ideas?

---

### Post by beckejc on 2006-10-13
the php file should have been 

       <?php
         print "My php test page.<br>\n";
       ?>

---

### Post by ~LoKe on 2006-10-13
> **beckejc said:**
> the php file should have been 

       <?php
         print "My php test page.<br>\n";
       ?>

I can't tell you why it's opening multiple tabs, however...you have Apache installed, yes?

---

### Post by beckejc on 2006-10-13
Yes, apache2 I hope.  But I'm not sure it's working correctly with PHP, etc.

---

### Post by ansi on 2006-10-14
> **beckejc said:**
> Yes, apache2 I hope.  But I'm not sure it's working correctly with PHP, etc.

You must to have installed && configured Apache with enabled PHP module, before. You can visit [http://www.lamphowto.com/](http://www.lamphowto.com/) for details about apache && php configuration, also.

---

### Post by beckejc on 2006-10-14
That is not very helpful since it refers to installing from source.  I am installing from the packages via Synaptic.

---

### Post by jacob_lurch on 2006-12-03
Hi

Trying clearing the Firefox cache...

---

