---
title: "Fat Client(ish) Computer Lab"
date: 2008-02-26
forum: General Help
---

### Post by sparrowkc on 2008-02-26
My high school will soon be upgrading to new computers and transferring old Windows XP llicenses to the new machines, leaving the old ones useless.  Since there is always a class in need of labtime, I would like to put together an plan for an Ubuntu computer lab to present as an option. 

The only real problem I can think of is making it work with our current Windows system.  Each student has a their own user name, which can be used at any computer in the school.  They also have a networked folder that no other students can access.  We could duplicate the login server, but we would still need a way to preserve Windows file permissions on Ubuntu.  I also don't know if each student would have a remote /home directory or if they would all be the same with the documents folders mapped to their networked folders.  

All the computers in the school have deep freeze on them, and these machines would need to be configured to have a comparable level of security. 

These are decent P4 machines, so It really wouldn't make sense to do thin clients.  

I don't believe that this is likely going to happen, but I would like to be able to tell people how it would work.

Thanks,
-Mark

---

### Post by smcleish on 2008-03-06
I'm not an expert here - I'm replying because no one else has yet and I do have a thought that might be useful to you. Have you tried looking at samba ([www.samba.org](www.samba.org)) and what it might do in this context? You might get some interesting responses posting this question on the samba mailing list, in particular (but check out the docs first!).

Cheers,
Simon

---

