---
title: "Trouble starting a script at boot"
date: 2006-11-09
forum: General Help
---

### Post by BrandonLC on 2006-11-09
I'm pretty new to linux, but things are coming along pretty smooth. There is a lot more to learn but so far so good. I've had minimal headaches.

I'm trying to get Reliable Message Queue, a message queue built with ruby, to run at start up. So it's always there to applications to use.

I created an /etc/init.d/queues script, and I also created a symbolic link in the rc5.d folder (sudo ln -s ../init.d/tomcat S20queues).

Reliable Message Queue will not load on a reboot. 

However I can start/stop the process manually like this:

sudo /etc/init.d/queues start
sudo /etc/init.d/queues stop

That works fine.

Is there anyway I can figure out why this won't start after a reboot? Any log files I should look at? any other advice?

Thanks for your time

---

