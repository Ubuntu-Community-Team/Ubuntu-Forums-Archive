---
title: "Apache &amp; Security"
date: 2005-06-16
forum: General Help
---

### Post by boosted on 2005-06-16
I have a question about how to make it so someone can't get a directory listing in apache?  for example say you are at [www.domainname.com/stuff/stuff.php](www.domainname.com/stuff/stuff.php)
on my server right now if i just took out stuff.php so it read [www.domainname.com/stuff/](www.domainname.com/stuff/) I would get a directory listing as well as anyone who did this.  How do I prevent this?

edit:  I just found out that the only page that is working right nis my main page (which is a .html)  anything else...  forum or any othere php file just comes up as a blank page on firefox and a Page cannot be displayed in "IE".  Somehow while I was sleeping my ubuntu box restarted??  now this happend?  any ideas?

I tried putting an html file in one of the other folders and it won't display it???  it is like anything outside the www folder it will not goto??   Please help....  I really need to get this fixed ASAP!

---

### Post by msgyrd on 2005-06-16
You have to edit your apache2.conf file to tell it to recognize .php extensions (this has been explained in a couple other threads, just search the forums).

As for your question about blocking directory access, I know it's possible, so don't give up hope, but I don't know how to do it.

For your last question, apache only recognizes folders where it's told to look.  In the apache2.conf file you tell it where to set it's site, and all folders beneath that with correct permissions are part of it (this usually defaults to /var/www/*).  If it's not working correctly, my first thoughts would be to check subfolder and file permissions.  if you didn't create them as root, it may be incorrect.

---

### Post by boosted on 2005-06-16
hhmm...  well all of this was working just fine then when the machine restarted while I was asleep it got all jacked up.....  I did create those subfolders etc...  as root.  So what should permissions be set to?  lol  I don't even kow how to view permissions! do I set them by chmod or something?

edit:
the first uncommented line in apache2.conf is this
ServerRoot "/etc/apache2"
is this right?  above you said it should point to /var/www/*  
i don't see how this changed because it was working just fine!

---

### Post by word_virus on 2005-06-16
[QUOTE=msgyrd]
As for your question about blocking directory access, I know it's possible, so don't give up hope, but I don't know how to do it.
[/QUOTE]

Blocking directory access can be accomplished by disabling one of Apache's default modules (I'm not at my usual box right now, so I apologize for the lack of specifics), I think mod_index.  Doing this will make it so that Apache will only let you access directories containing an "index" file.

I belive this is done via the .conf file, as well, but like I say I'm not at my usual box.  Perhaps I can post more specific info later today...

---

### Post by boosted on 2005-06-16
yes if you could post later with some details that would be great! Seeing as though I don't really understand what you mean by all that LoL  I am new to linux and apache!
Thanks

and if someone could help me with the other problems I mentiond above that would be great.. seeing as how I can't view any of my web site now.

---

### Post by boosted on 2005-06-16
I am at work and tried pinging my IP address and it just times out??  I havn't changed any apache config files so I can't understand why it would do this after the computer restarted .. does anyone have any ideas?

---

