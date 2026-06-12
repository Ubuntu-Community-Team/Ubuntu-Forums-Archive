---
title: "Unable to copy the user's Xauthorization file"
date: 2007-06-14
forum: General Help
---

### Post by tj71587 on 2007-06-14
I am running the server edition of Ubuntu 7.04. Here is an example of the error I get. This was when I was trying to update it...

Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '46137347' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmpwzFjJ3' as user root.

Unable to copy the user's Xauthorization file.

The only option I have is close. I have similiar errors when I try to change settings or download anything from the package manager.

Thanks,

T.J.

---

### Post by fezouro on 2007-12-07
try installing "xauth". it worked for me. cheers.

---

### Post by Burillo on 2008-02-04
fire up terminal (xterm, konsole, terminal, ctrl+alt+F2, whatever), navigate to your home dir:
```
cd ~
```
them change permissions on that file:
```
sudo chown YOURUSERNAME .Xauthority
```
and you're done.:guitar:

---

### Post by tj71587 on 2008-02-21
Thanks, I feel like an idiot because I havent look at this in so long, but the problem turned out to be that it needed to be restarted, but thanks for the help!

---

