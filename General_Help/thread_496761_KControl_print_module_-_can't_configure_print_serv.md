---
title: "KControl print module - can't configure print server"
date: 2007-07-09
forum: General Help
---

### Post by skullmunky on 2007-07-09
i'm using kubuntu feisty.  i have a printer hooked up to my desktop, and want to share it so i can print from my laptop over cups.  the good news it works, and was really easy, but i can only administer the printer from the cups web interface ([http://localhost:631](http://localhost:631)).  

but, i can't administer it from kcontrol.  when i go to Print Server->Configure Server i get asked to authenticate.  i'm running this sudo, but anyhow i go ahead and put in my username and password, or name and password from other accounts, or for root, and all i ever get is this error:

"Unable to configure print server. Error message received from manager:
Unable to retrieve configuration file from the CUPS server. You probably don't have the access permissions to perform this operation."

what's it talking about?  is that in fact an account username and password it wants, or is there an internal cups admin and password pair it wants?   how come it works fine from the web interface and doesn't ask for any authentication of any kind there?

---

### Post by marsbt on 2007-07-09
Just wondering: Do you have admin rights (list of sudoers)?

---

### Post by FractalBrain on 2007-09-13
Ah ha, Ive got the same problem.  In fact, I have that problem plus all but my default printer have disappeared.  Hmm, I wonder if there is a connection.  Anyway, Im a sudoer, but nothing would let me in....grrr...my computer.

---

### Post by erdalronahi on 2007-09-14
I got the same problem. I can't configure the printer server in KDE, it won't accept my username and password. I am the primary user and have sudo rights.

---

