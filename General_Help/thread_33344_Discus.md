---
title: "Discus"
date: 2005-05-10
forum: General Help
---

### Post by RickSGM on 2005-05-10
First, let me say that I hadn't installed but one other unix system successfully, and that Ubuntu has been a good install already.  Even this newbie to linux has done it.  \\:D/ 
I have a problem with discus and am not sure what to do.  I used the synaptic package manager to install it, but don't know where to access it at to set up the forums, or to admin them at.  
I have the ssh, apache, php, mysql, etc installed.  If someone can help, it would be appreciated greatly.

---

### Post by mirtux on 2005-05-12
Hi,
   but the problem you have is that you cannot access discus?

Regards,
MC

---

### Post by RickSGM on 2005-05-12
Exactly.

---

### Post by GTvulse on 2005-05-12
Using synaptic, search for discus. Select the name and in the contextual menu choose properties. Click on the installed files tab and you'll find the files locations. You'll probably need to add discuss cgi-bin directory to apache's http.conf file with the correct configuration incantation (which I haven't done in a looong time and can't recall off the top of my head, should be in the extra files in /usr/share/doc/discus  :-). After that, point your browser to the installation CGI file and configure it.

Good luck!

---

### Post by RickSGM on 2005-05-13
Uh oh.  Come to find out, this isn't the discus forums.   #-o It's a disk space usage program.  Sure had me scratching my head.  Many thanks for the help.  Might have to try fudforums.

---

### Post by mirtux on 2005-05-13
Hi,
   have you tried **locate discus** to point out the location of the executable?

Regards,
MC

---

### Post by RickSGM on 2005-05-13
Yes.  I found the read me, and it was the disk space usage utility, not the discus forums.  I found fudforums on there, so I'll give it a whirl installing them.  May have to give a holler on them.  Thank you very much for the help.   :smile:

---

