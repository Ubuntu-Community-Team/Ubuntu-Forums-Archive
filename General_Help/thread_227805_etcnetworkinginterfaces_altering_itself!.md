---
title: "/etc/networking/interfaces altering itself?!"
date: 2006-08-02
forum: General Help
---

### Post by Kibbo on 2006-08-02
Hoping that someone will be able to explain this:

Cliffs:
computer crashed, "auto eth1" line in /etc/networking/interfaces removed.

Extended version:
Recently, while starting up my machine, I experienced a power failure.  Note that I had fully booted the kernal, I was logging into gdm at the time. 

I thought "great, this is going to cause problems," and rebooted.  When I did so, I found I could no longer connect to my wireless network.  Gnome's wireless utility was unable to resolve the problem. Not wanting to troubleshoot then, I left it for a couple of days.

Tonight, I booted, noted that my wireless connection was still down, and checked out my /etc/networking/interfaces file.  The "auto eth1" line was no longer there.  An "ifup eth1" reestablished my connection.  I reentered the line in the config file, and all is well.

Question:
How did a crash specifically affect that file in that way?  If it were a matter of disk corruption, I would hardly expect to be so specifically altered.  I'm figuring that some proccess altered the file.  

Anyone know why this happened?

---

### Post by philippe_carlo on 2006-08-02
I've seen some programs change the file. Gnome network manager and wireless radar being among them. They run with root permissions, so they can change the file.

---

### Post by Kibbo on 2006-08-02
Oh,

So me fiddling with stuff in Gnome's network manager probably did the damage.  I should'a thought of that myself.

Thanks for the reply.

---

