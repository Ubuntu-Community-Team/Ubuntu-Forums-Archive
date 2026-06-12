---
title: "setuid, can't edit file"
date: 2008-02-26
forum: General Help
---

### Post by n2stc on 2008-02-26
Started out with:
```
This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
```

(process:24025): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.htmledit](http://www.gtk.org/setuid.htmledit)

Refusing to initialize GTK

I think I have found the offending file but when I edit it, I can't save it.  I have tried sudo gedit and gksudo gedit, but the the edit app. does not start(no feedback).  I tried chmod and chown on the file but I still can't re-save the file:(

---

### Post by jrib on 2008-02-26
What are you actually typing to get that warning?

---

### Post by n2stc on 2008-02-26
> **_jason said:**
> What are you actually typing to get that warning?

I'm trying to log in to my original account.  Thanks for the reply!

---

### Post by n2stc on 2008-02-26
I deleted /home/stan/.gnupg/gpg-agent-info-xxx  
Fine now.

---

