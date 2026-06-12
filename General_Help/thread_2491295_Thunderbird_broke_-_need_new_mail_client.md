---
title: "Thunderbird broke - need new mail client"
date: 2023-10-03
forum: General Help
---

### Post by lsutiger on 2023-10-03
As the title says. After autoupgrading to v115.2, the unified folder is broken and throws errors. And there are several other small quirks in the UI that just do not seem right(buttons missing, addons disabled, etc). After browsing for help on the subject there is a LOT of posts asking for help, but no solutions to for a majority of the problems with this upgrade.
I need a client that can handle multiple accounts and have a unified folder. It would be nice to import my calendar and contacts to the new mail client. 
What do you suggest?

---

### Post by TheFu on 2023-10-03
If thunderbird is a snap package, I'd roll back to v115.1 and freeze it there until the issue is reported solved.  I don't have the rollback command handy, but I know there is one.  It won't go to v114 - rollback across major release versions isn't allowed, but here's the hold command, once you get a version you want installed.

```
$ snap --hold thunderbird
```

I use Linux Mint to avoid automatic updates via snaps.

---

### Post by ajgreeny on 2023-10-03
You could alternatively download the archive of thunderbird as a tar.gz  direct from mozilla, [https://download.mozilla.org/?product=thunderbird-115.3.1-SSL&os=linux64&lang=en-US](https://download.mozilla.org/?product=thunderbird-115.3.1-SSL&os=linux64&lang=en-US) extract the archive and the run thunderbird directly from the executable file in the archive.

This is exactly the same method that I and i think many other users have made use of in order to keep using Firefox without having to deal with some of the difficulties and lack of control that snap versions can impart on the system.

---

### Post by Rubi1200 on 2023-10-04
You can look at some alternatives here:
[https://itslinuxfoss.com/top-8-best-email-clients-linux/](https://itslinuxfoss.com/top-8-best-email-clients-linux/)

---

### Post by SeijiSensei on 2023-10-04
If you're having problems opening links from within email messages, read this thread.

[https://ubuntuforums.org/showthread.php?t=2490769](https://ubuntuforums.org/showthread.php?t=2490769)

The problem arises because Ubuntu wants to play nice with Microsoft WSL.

Like you, I'm not happy with the changes to the user interface, especially with regard to threading, which I never use. Took me a while to find the right combination of settings to return to an unthreaded list of unread messages.

---

