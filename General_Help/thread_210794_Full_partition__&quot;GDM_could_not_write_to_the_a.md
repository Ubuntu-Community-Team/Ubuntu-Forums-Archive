---
title: "Full partition?  &quot;GDM could not write to the authorization file...&quot;"
date: 2006-07-07
forum: General Help
---

### Post by dishbert on 2006-07-07
I was going to make an image of my Ubuntu partition with G4L prior to upgrading, and I used the cleandrive script that came with G4L to try to delete all the unused space on the partition. I think that cleandrive successfully wrote numbers to all my blank disc space, but that when it deleted them they just ended up in the trash and left the hard drive full. Now I get the "GDM could not write to the authorization file..." message.

I've tried using the recovery teriminal and the "rm -rf /home/me/.Trash/* command, but no joy.

What else could I try before I give up and reinsall?

---

### Post by dishbert on 2006-07-07
I should have mentioned that the full text of the message was:

GDM could not open your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, is not possible to log in. Please contact your system administrator.

---

### Post by PriceChild on 2006-07-07
I did this once :P

press ctrl+alt+F1 and log in to that terminal.

Then navigate to a largish file you don't mind losing, and use the "rm" command to get rid of it.

Maybe simply deleting your trash: "rm .trash"

the ctrl+alt+F7 to get back to graphical and try logging on again.

---

### Post by dishbert on 2006-07-07
Thanks for the suggestion PriceChild, I just gave it a try and deleted 3 files I know are about 30MB each, but still the same message.  When I "ls" /home/me/.Trash there are no files listed, and when I rm /home/me/.Trash/* I get a "no such file" message.

Maybe I'm on the wrong track, maybe there is a problem with the authorization file instead.  I found another thread that said to try:

sudo chown /home/me/.ICEauthority
chmod 600 /home/me/.ICEauthority

but when I try these I seem to be missing some parameters.

---

### Post by aysiu on 2006-07-07
Is your username *me*? What errors do you get when you try those commands?

---

### Post by dishbert on 2006-07-07
No, it's chris actually, so in real life I ran those commands from the /home/chris directory.  

The sudo chown command said I hadn't identified a group or owner, I think.  I tried chown --help but it scrolled by so fast I couldn't read it, and neither up arrow or page up keys moved up on the screen.

I'm a bit of a Linux noob when it comes to this stuff.  Did the chown and chmod commands work for your problem aysiu?

---

### Post by aysiu on 2006-07-07
```
sudo chown chris:chris /home/chris/.ICEauthority
```

---

### Post by dishbert on 2006-07-08
Thanks for the proper syntax aysiu, it seemed to work, but I still get the same message and cannot login through GDM.

I'll try posting with the creator of G4L, since that seems to be the point at which my troubles began.

---

### Post by mbsullivan on 2008-02-08
Hi All,

I know this thread is old.. However, for future reference to people with similar problems, this problem may be caused by improper permissions being set on your /tmp directory.

Try: 

```
sudo -s
chown root:root /tmp
chmod 777 /tmp
```

Hopefully this may help somebody experiencing this fairly common problem.
Mike

---

