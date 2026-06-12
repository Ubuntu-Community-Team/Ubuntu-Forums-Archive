---
title: "How to probe a port for a service"
date: 2014-06-02
forum: General Help
---

### Post by CaptainMark on 2014-06-02
How do I check from my Ubuntu desktop if a certain service is running on a specific port on a Debian based server?

Specifically I want to check if the transmission-daemon web UI is running on port 9091 on my server 192.168.1.102 from a bash script and build an if/else statement around the results.

Regards

Mark

---

### Post by aromo2 on 2014-06-02
How do you do it from command line?

From command line, I would run [FONT=courier new]telnet 192.168.1.102 9091[/FONT]

From a bash script I probably would wrap it with [FONT=courier new]expect[/FONT] (I would have to read the man pages, as it is not as intuitive)...  Or probably try use the autofs filesystem (don't remember from the top of my head but it should be something like [FONT=courier new]/net/192.168.1.102/tcp/9091[/FONT] )

---

### Post by CaptainMark on 2014-06-02
Okay have searched around a bit more and answered my own question, I should have explained that I don't need to know details about what service is running on the port in question so simply```
nc -z 192.168.1.102 9091
```planted right into an if evaluation will give the result I need, but if anyone wants to suggest better ways, don't let me stop you.

Thanks
Mark

---

