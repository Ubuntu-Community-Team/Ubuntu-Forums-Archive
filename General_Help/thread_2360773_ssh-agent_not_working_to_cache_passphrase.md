---
title: "ssh-agent not working to cache passphrase"
date: 2017-05-08
forum: General Help
---

### Post by vilwarin on 2017-05-08
Hello!

I just upgraded to 16.04. Since then I cannot cache passphrases of my ssh-keys anymore.
Before this was handled automatically by the system. I was prompted a GUI-prompt asking me for the ssh key passphrase and then caching it for this session.
Instead now I am prompted for the passphrase on the terminal each time I use ssh.

Browsing the internet and ubuntu forum, the standard way to cache ssh key passphrases is ssh-agent. This does not work for me.
This is what I do:

```
$ ssh-agent bash
$ ssh-add .ssh/my_key.prv
Enter passphrase for .ssh/my_key.prv
Identity added: .ssh/my_key.prv (.ssh/my_key.prv)
$ ssh-add -l
2048 SHA256:xxxxx .ssh/my_key.prv (RSA)
$ ssh user@host 
Enter passphrase for key '/home/user/.ssh/my_key.prv': 
```

Any ideas, what prevents ssh-agent from working?
Or any ideas, how to get the GUI-prompt for passphrase caching from the previous ubuntu version back?

---

