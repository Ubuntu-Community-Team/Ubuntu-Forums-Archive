---
title: "SSH connection with domain credentials"
date: 2007-07-09
forum: General Help
---

### Post by Jamie Jackson on 2007-07-09
I'm used to connecting to SSH servers with credentials that are directly on the remote machine:

```
ssh myUsername@myRemoteMachine
```

Recently, our admin hooked up a particular Linux box to the corporate domain's Active Directory.

So, now, I've got one more parameter to specify, but I don't know how.

How do I connect to *myRemoteMachine* using the domain credentials (*myUsername@myDomain*)?

I hope that made sense.

Thanks,
Jamie

---

### Post by PgR on 2007-07-11
Don't know if this would work - and I've no way to test it... but you could try

```
ssh -l myUsername@myDomain myRemoteMachine
```

---

### Post by Jamie Jackson on 2007-07-12
Thanks for the suggestion.

I tried it, and responded with my domain login, but no luck.

```

$ ssh -l myUsername@myDomain myRemoteMachine
myUsername@myDomain@myRemoteMachine's password: 
Permission denied, please try again.
myUsername@myDomain@myRemoteMachine's password: 
Permission denied, please try again.
myUsername@myDomain@myRemoteMachine's password: 
Permission denied (publickey,gssapi-with-mic,password).

```

Thanks,
Jamie

---

### Post by trainerbill on 2008-07-03
you have to enable kerberos authentication in /etc/ssh/sshd_config.

---

### Post by Jamie Jackson on 2008-07-03
> **trainerbill said:**
> you have to enable kerberos authentication in /etc/ssh/sshd_config.

These are (what I think are) the relevant pieces in my ssh_config (not sshd_config, do I need that?)

```
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no
```

---

