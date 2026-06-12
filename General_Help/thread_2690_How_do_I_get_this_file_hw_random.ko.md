---
title: "How do I get this file hw_random.ko"
date: 2004-10-30
forum: General Help
---

### Post by united on 2004-10-30
I use a Toshiba notebook for work and now ubuntu as my os.

When I boot and the process gets to the . . .
starting hotplug subsystem . . . . .
it generates a error message that states . . . .  .hw_random.ko no such device..
and then has a long pause before it continues to finish booting.

I would post the actual error message but it seems ubuntu does not do a boot log file or least I am unable to find it.

So how do I get this file hw_random.ko or how do I have it not want that file but yet start the hotplug subsystem - which I need for usb support.

thanks - John

---

### Post by spoetnik on 2004-10-30
You don't need the file, you just need to blacklist it, so hotplug won't try to load it.

at hw_random  at the end of this file /etc/hotplug/blacklist

I don't know what hw_random is excatly, it think it's a random key genretaror, and has someting to do with ssh??

I have also added floppy on my laptop machine, to stop loading the floppy driver.

---

### Post by united on 2004-10-30
Thanks!!!!! that worked 
John :-D

---

