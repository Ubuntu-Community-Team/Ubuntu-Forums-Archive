---
title: "Free up disk space /var/tmp folder"
date: 2014-05-04
forum: General Help
---

### Post by J_Me on 2014-05-04
Why would programs choose to use /var/tmp and not /tmp, is it safe to delete /var/tmp files, are /var/tmp files flushed out when powering off the system like /tmp files are.

The story was that I ran out of disk space and a program crashed. I deleted as much rubbish to free up disk space but couldn't recover the amount I had before, only after reusing that program(audacity) did it decide to remove the /var/tmp file it made and I got back my lost disk space.

Thanks

---

### Post by claracc on 2014-05-04
Please, see: [http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/var.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/var.html) for a full explanation of /var directory and /var/tmp.

---

### Post by J_Me on 2014-05-04
Thanks for the reply, from the link(for /var/tmp) it says
> /var/tmp

    Temporary files that are large or that need to exist for a longer time than what is allowed for /tmp. (Although the system administrator might not allow very old files in /var/tmp either.)Could you tell me if I were to remove unwanted files from /var/tmp with 'sudo remove theFile' whether it will break the program. As an example I have another program installed which I haven't used in a year but there is a 6gig file for it in /var/tmp.
Thanks

---

### Post by davea42 on 2014-05-04
That is a bit non-specific.  If you named the program and showed ls -l output on the /var/tmp file it might give
someone a way to help.  One wonders: is the file owned by you? root? Some other owner?

---

### Post by J_Me on 2014-05-04
What initially drew my attention to /var/tmp was audacity(in my first post), even though I restarted ubuntu I could not recover the lost disk space until I used audacity again. Anyway I've been doing some googling and from what I gather it's not a good idea to delete /var/tmp files but it can be done, next time I'll give it a go and see what happens.
For the program that I haven't use in over a year, yes I'm the owner 'drwxrwxr-x 260 me me'.  It wasn't installed from the repositories, I'm in the process of asking the company where I purchased it what I should do.
Thanks

---

### Post by J_Me on 2014-05-05
I'll mark this thread as solved.
Here's a link to another post
[http://ubuntuforums.org/showthread.php?t=2222135](http://ubuntuforums.org/showthread.php?t=2222135)

---

