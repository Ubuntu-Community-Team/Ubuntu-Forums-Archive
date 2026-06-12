---
title: "Question about mounting extra partition in Ubuntu 7.04 beta version"
date: 2007-04-19
forum: General Help
---

### Post by Coop on 2007-04-19
Hi everyone

I've replaced my Ubuntu 6.10 with Ubuntu 7.04 beta version.


I have an extra partition which I use for backing up my data.


On Edgy, I mounted this partition by following [this tutorial]("http://www.psychocats.net/ubuntu/mountlinux").


Before installing Feisty beta, I backed up all my important data on this extra partition.


Now, I have installed Feisty beta.


I checked my /etc/fstab file, and I saw that my extra partition is mounted on /media/hda4.


So, I went there and now I can access my files on that partition.


However, when I right-click the hda4 folder and go to the permissions tab, it says the Owner is "1004" and the Group is "1002".


Please tell me what are "1004" and "1002"?


Also, in the basic tab, in the Contents section, it says: ```
66304 items, totalling 32.1 GB
(some contents unreadable)
```


Why are some contents unreadable, and how do I make them readable?


I have attached 2 screenshots.


Also, I can't write to the extra partition. How do I write to it?


Please reply to me early. I will highly appreciate any help you give me.

---

### Post by dcstar on 2007-04-19
> **Coop said:**
> Hi everyone

I've replaced my Ubuntu 6.10 with Ubuntu 7.04 beta version.


I have an extra partition which I use for backing up my data.
.........
However, when I right-click the hda4 folder and go to the permissions tab, it says the Owner is "1004" and the Group is "1002".


Please tell me what are "1004" and "1002"?
.........

Those are probably the account identifiers from your other O/S - where you had created accounts that you haven't yet created in your new install.

If you now only want to access that drive from your new Ubuntu install, you can replace the permissions using the chgrp and chown commands (in a terminal), for example:

```
sudo chgrp *group-name* /dev/hda4
sudo chown *owner-nam*e /dev/hda4
```

Replace the *....-name* with the account name you want to have permission to be owner and group.

Use **ch... -R** if you want the changes to recursively propagate through all the files.

---

### Post by Coop on 2007-04-19
Hello dcstar

Thank you for your help.
I'll try doing what you said.

---

