---
title: "not working"
date: 2007-11-03
forum: General Help
---

### Post by paranoiahax on 2007-11-03
pleh. Right i'm gonna start from the beginning. I have just moved house, and it took me a while to get the internet up, so all these updates were piling up in my list. then i finally got the internet, but it's incredibly slow. i was downloading the updates, leaving it for ages, and put them on a different desktop. but i forgot about them and turned off my laptop. so yeah i turned on my laptop the next day, ubuntu loaded up fine.. until i got to the login window. it then crashed and then gave an error. however, I could do ctrl + alt + f1,f2,f3 all of my terms, and everything still worked fine from there. 

but i really needed to get on the internet at that point so i partitioned my HD with Windows on (pleh i know sucky windows) and then installed Windows XP and backed up all my files. now I need to reinstall the GRUB because Windows screwed that up. I'm just about to reinstall GRUB by adding the menu.lst file back into there. However, I just wondered how to actually back up Ubuntu to the way it was before I started installing all the updates, because I preferred it that way.

I have been told just to insall Gutsy because I had feisty on there, but that would mean I have to reinstall everything because I had Apache, Php, and MySQL all set up on there, and countless other set-ups that would take me forever to all reinstall, and it would be much easier just to get that back and then upgrade to Gutsy from 7.04. 

so could someone give me any ideas how to just restore Ubuntu to exactly how it was before?

many thanks, Para

---

### Post by CouchMaster on 2007-11-03
In a terminal as root type these commands
(assuming windows is on the first partition on the first hard drive hd1)
root (hd0,*) * means which ever partition Linux is on - if it's the 3rd partition it would be (hd0,3)
then type
setup (hd0)
then type 
quit
this will get grub to take back the boot operations from windows

---

