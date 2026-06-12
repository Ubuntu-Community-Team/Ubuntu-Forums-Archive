---
title: "3 in trash will not delete"
date: 2018-08-08
forum: General Help
---

### Post by jgw on 2018-08-08
I have 3 libdvd.pkg folders, in trash.  When I empty trash they remain.  I suspect I can remove them with sudo nautilus, etc but am not sure I should.  They are exactly the same name but come from 3 different places; /usr/lib, /usr/lib/share, and /usr/share/doc.  Permissions; owner root, group root.  I guess I could also change the permissions and delete, but..............

I also have no idea how they got there.

Thank you.............

---

### Post by Impavidus on 2018-08-09
Files coming from places like /usr/lib are usually handled by the package manager and it's a bad idea to move them to trash, but that has happened already. It's not surprising these files are owned by root. Are they in root's trash or in your own trash? Anyway, you should be able to delete them using rm – or more likely, sudo rm.

Note that to delete a file, ownership and permissions of the file don't matter. It's about ownership and permissions of the directory containing the file.

---

### Post by jgw on 2018-08-09
Thank you for the reply

Your thoughts mirror mine.  I never put these here, the system did.  I suspect I was cleaning stuff up with stacer and that was what did it but, then again, maybe not (I really don't know).  From your reply I think you are saying that, since they are in the trash, go ahead and get rid of them.  I will make a run at it (I actually tried once, with sudo, and failed)

Deleted them with "sudo rm -r libdvd-pkg.3, sudo rm -r libdvd-pkg.2, sudo rm -r libdvd-pkg"

---

