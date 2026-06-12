---
title: "More of a general question then an problem"
date: 2007-08-20
forum: General Help
---

### Post by will71110 on 2007-08-20
Is there a reasion not to run the root terminal?  I like using it instead of sudo everything.  I use it to run natulius expecially to change some files that get put on my machine under root.(GproFTP has done this quite a bit and now SFTP is doing it but I think I have that resolved now).

Like I said, just worndering.

---

### Post by schallstrom on 2007-08-20
It's a general rule for all Unix like systems: Use root only if you absolutely need to!

The reason is simple: You can't really harm the system with normal user privileges. Worst thing you could do as a normal user is deleting all your own files, which isn't that bad as you are doing regular backups, right? But as root you can wreak havoc on the whole system with just one single misspelled command. It's not very likely if you know what you are doing, but it's possible.

And you should never browse the WWW as root user. The reason is similar: If a malicious web site succeeds in trying to run code on your machine through your WWW client, it will run the code only with the privileges of a normal user (worst case scenario of this happening: see above). But plead for mercy if you fired up your web browser as root and some evil site runs code on your machine: It will have the complete control and chances are that you wouldn't even notice.

---

### Post by will71110 on 2007-08-20
Yep,  I knew that.  The only thing I was saying is if I was going to sudo,  I'd use the root term to do so.  I never run anything in root unless it requires.  Also all my important stuff goes to a NAS so if I lost linux it's  all somewhere else anyways.

---

