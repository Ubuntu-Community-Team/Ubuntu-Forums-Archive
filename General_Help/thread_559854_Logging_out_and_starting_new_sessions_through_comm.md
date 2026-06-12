---
title: "Logging out and starting new sessions through command terminal"
date: 2007-09-25
forum: General Help
---

### Post by cinematography on 2007-09-25
Hi Folks,

I was wondering if there was a way to log out and start new sessions through the command line. I'm using Xubuntu 7.04.

Your help would be greatly appreciated,
Tony

---

### Post by dcstar on 2007-09-28
> **cinematography said:**
> Hi Folks,

I was wondering if there was a way to log out and start new sessions through the command line. I'm using Xubuntu 7.04.

Your help would be greatly appreciated,
Tony

"sudo startx" starts an X session in a terminal, or:

```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

will stop and start the graphical terminal.

---

### Post by cinematography on 2007-10-01
Thank you! 

And for starting sessions on new displays: 
```
startx -- :1
startx -- :2 
and so on...
```

---

