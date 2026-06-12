---
title: "How to disable Darwin streaming server start everytime my machine starts"
date: 2007-05-17
forum: General Help
---

### Post by yinglcs2 on 2007-05-17
Hi,

I have installed Darwin on my ubuntu. And now Darwin starts everytime I start my machine.

But can you please tell me how can I configure ubuntu so that it does not start Darwin streaming server everytime I start my machine?

Thank you.

---

### Post by Goombie on 2007-05-17
1) Go to your System menu --> Preferences --> Sessions.

2) On the startup tab, you'll see a list of programs that load with Ubuntu. Highlight the entry for Darwin and click the delete button.

3) No step three, unless you want to reboot to make sure that worked. :)

---

### Post by yinglcs2 on 2007-05-18
Thanks I followed your steps, but I can't find darwin there.

Is it possible that it is in some place else?

Thank you.

---

### Post by Goombie on 2007-05-19
It probably is somewhere else, but I'm afraid I don't know where. I'm a bit of an Ubuntu newbie myself. One thing you could do is check the preferences dialog of Darwin. Sometimes there is a setting that you could change for it to not start up.

---

### Post by robertc36 on 2007-06-30
to start server at boot > /sbin/chkconfig --level 35 DarwinStreamingServer on
to do the opposite > /sbin/chkconfig --level 35 DarwinStreamingServer off

---

