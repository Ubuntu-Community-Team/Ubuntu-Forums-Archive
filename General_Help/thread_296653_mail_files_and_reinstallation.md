---
title: "mail files and reinstallation?"
date: 2006-11-09
forum: General Help
---

### Post by detoj on 2006-11-09
I have recently been experiencing a great deal of problems with Edgy that have made it very unpleasant to work with.  I won't go into detail about the problems, but they have made me want to stop using Edgy.  Instead of stopping altogether, I have decided to try to reinstall Edgy using the cd, as I am hoping that my problems could have been caused by problems from upgrading from dapper to edgy.  Hopefully a fresh install will do the trick; if not, I will go back to using Dapper, as that release seemed to work much better for me.

When I reinstall (either Edgy or Dapper) I want to still have all my important documents and mail.  I know where I saved my files, but I don't know where Evolution saves my mail messages it downloads from the mail server.  I want to be able to transfer my mail elsewhere, reinstall, and then transfer my mail back to Evolution so it can appear in my inbox again.  Does anyone know which folder or file Evolution stores messages in, or a likely place it would put them?  By the way, I am relatively new to Linux and Ubuntu, so I'm sorry if the answer seems really obvious, but I'd appreciate the help.  Thanks.

---

### Post by Sef on 2006-11-09
Did you set up a separate home partition?

---

### Post by detoj on 2006-11-09
No, I have all my personal files, pictures, and music on a separate partition, but my home folder is on the same partition as everything else.

---

### Post by dcstar on 2006-11-09
> **detoj said:**
> 
.......
When I reinstall (either Edgy or Dapper) I want to still have all my important documents and mail.  I know where I saved my files, but I don't know where Evolution saves my mail messages it downloads from the mail server.  I want to be able to transfer my mail elsewhere, reinstall, and then transfer my mail back to Evolution so it can appear in my inbox again.  Does anyone know which folder or file Evolution stores messages in, or a likely place it would put them?  By the way, I am relatively new to Linux and Ubuntu, so I'm sorry if the answer seems really obvious, but I'd appreciate the help.  Thanks.

The Evolution files are in the (hidden) .evolution directory in your home directory, simply copy these to somewhere safe and then restore them to the same place on your new system.

---

### Post by detoj on 2006-11-09
Thanks!  I had already seen these files, but I couldn't find the specific file that contained my mail, so I assumed it was located somewhere else.  But if you say they're in there, I'll believe you, so thanks for the help.

---

