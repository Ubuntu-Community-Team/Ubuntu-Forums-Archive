---
title: "Permissions issues in a barebones installation"
date: 2007-02-26
forum: General Help
---

### Post by trevorv on 2007-02-26
Today I installed a server version of Hoary (that's the only release I had to hand) and then updated it straight to Edgy, and installed Fluxbox.

I installed Firefox, which would only run as root, but decided I'd rather have Epiphany anyway only to encounter the same problem.

The error it throws up is as follows:

(epiphany:7300): libgnomevfs-WARNING **:Unable to create ~/.gnome2 directory:Permission denied
Could not create per-user gnome configuration directory `/home/trevorv/.gnome2/': Permission denied


How do I give it the permission it needs?

Thanks :)

---

### Post by taurus on 2007-02-26
What are the output of these two commands from a prompt?

```
id 
ls -la /home
```

---

### Post by trevorv on 2007-02-27
Thanks for the response :) Using your reply I realised I didn't own my own /home folder... no idea why! Thanks for your help :)

---

