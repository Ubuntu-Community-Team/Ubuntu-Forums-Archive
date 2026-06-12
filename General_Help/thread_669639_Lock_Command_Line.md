---
title: "Lock Command Line?"
date: 2008-01-16
forum: General Help
---

### Post by kinghajj on 2008-01-16
My work's IT guy recently implemented web filtering. The trouble is that it sometimes blocks sites that I need to use to actually work, or requires a network login, even to do something like go to Windows Update. So, to circumvent this, I leave my computer on at home and use PuTTY to setup a secure connection with a dynamic port, then configure my browser at work to use this encrypted SOCKS proxy to access the internet. It works very well.

However, I'm slightly paranoid, and I don't like leaving a PuTTY terminal unattended, and even though I'm sure that most in my office wouldn't know how to use it, I'd like to have a way to lock my terminal. Currently, I just open VIM, put it into Insert mode, then clear the scollback, but that's not as good as I would like. A command that would require me to enter my password before it returns to the shell would be awesome.

---

### Post by p_quarles on 2008-01-16
Short of shutting PuTTY off, I don't see how you could do that. Windows does, however, have a "lock screen" function which will require to log back in to get out of the screensaver.

Also, if your worried about sudo timeouts on the remote connection, you can type:
```
sudo -k
```
to end the timeout (i.e., the next "sudo" command would require the password, regardless of how recently it was entered).

---

### Post by kinghajj on 2008-01-16
The problem with locking Windows is that the computers switch between me and a co-worker, so it would irritate him and look a bit odd.

---

### Post by milosz.galazka on 2008-01-16
You could check *away* program in package repository.
```

milosz@bluebird:/etc/network$ away locked

       You went away at 23:16:19

 -- Press [Enter] to come back online --

       You have new mail in INBOX.

Password:
```

---

### Post by kinghajj on 2008-01-16
Thanks! That will do just fine.

---

