---
title: "In what file does evolution save mail?"
date: 2007-12-28
forum: General Help
---

### Post by hutxubix on 2007-12-28
Hello!

What file would one need to delete from a computer to erase all information concerning mails saved in Evolution without deleting evolution itself?

Thanks

---

### Post by forestpixie on 2007-12-28
you can find files  in a hidden folder on /home

/home/kevin/.evolution/mail

is mine, within that folder are folders for each e-mail account
is that any help

---

### Post by Joshua on 2007-12-28
I can't remember all the details, but I've tried deleting those files before and they kept getting recreated.  At the time, I was concerned with the contacts list.  I would close Evolution, and then delete the entire ".evolution" folder, but all the contacts would still be there when I re-opened evolution, and all those files would be back.  It may work for the mail files.  I'm not sure if they are handled differently, but if it doesn't, I ended up having to run a command that shut down a background process or two that were related to Evolution, or killing them in the System Monitor application.  After that was done I could delete those files without them being recreated.  Unfortunately, I don't remember what those processes were.

---

### Post by hutxubix on 2007-12-31
Thanks,

I will try and let you know.

---

