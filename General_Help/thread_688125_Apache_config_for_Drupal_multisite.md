---
title: "Apache config for Drupal multisite"
date: 2008-02-05
forum: General Help
---

### Post by maratonic on 2008-02-05
I'm running a Drupal multisite installation on a server with only 256 MB of RAM and I'm wondering whether I should have to make any particular changes to apache2.config (or other config files) to make it work ok? I'm having problems with httpd crashes, probably memory related... (see thread [http://ubuntuforums.org/showthread.php?t=684483](http://ubuntuforums.org/showthread.php?t=684483))

---

### Post by nemilar on 2008-02-05
How's your memory usage?  How much swap space do you have?

What's the output of the 
```
free
```

command, when things are running at full-use?

---

### Post by maratonic on 2008-02-05
As I posted in the other thread:

[HTML]<pre>
Fri Feb  1 02:40:01 CET 2008
 02:40:01 up 6 days, 17:41,  1 user,  load average: 0.28, 0.26, 0.25
             total       used       free     shared    buffers     cached
Mem:           256        219         36          0          0          0
-/+ buffers/cache:        219         36
Swap:            0          0          0
</pre>

[/HTML]

Normally 200-220 MB are used. I've been wondering about the zero swap used but I don't know what it should be or how to make it so...

---

