---
title: "synaptic, gparted, etc not opening"
date: 2018-12-04
forum: General Help
---

### Post by cmcanulty on 2018-12-04
I am running numerous computers on xubuntu 18.04 and am aware of the gksudo changes for opening sudo applications  to pkexec  . I also am aware of the fix of xhost si:localuser:root as a current login and xhost si:localuser:root in session start for a permanent fix. But on one computer these fixes don't work. I am the admin and only user. The only way I can open synaptic, gparted, and other applications on that computer is from the terminal, not from the panel or menus. Is there any additional fix I can try on that particular computer? For example I have in the panel for synaptic command synaptic-pkexec. As I said this fix plus the xhost si:localuser:root works on the other 20 computers but not that one. I also tried reinstalling the particular apps on that computer but no improvement. Thank you   

```
librarian@DarcyRemote:~$ xhost si:localuser:root
localuser:root being added to access control list
librarian@DarcyRemote:~$
```

---

