---
title: "ssh config file"
date: 2015-11-12
forum: General Help
---

### Post by zaphod_es on 2015-11-12
I am trying to create a new file ~/.ssh/config which will enable me to simplify my ssh logins. I am having difficulty setting up the following command:

ssh -qTfnN -D 7070 -p 2222 [email]username@example.com[/email]

So far it has:

Host short_name
    HostName example.com
    Port 2222
    User username

I cannot work out how and where to put the parameters -qTfnN -D 7070

An alias for each command would do the job but a custom config file is much easier to manage.

---

### Post by Habitual on 2015-11-12
looks like
```
LocalForward 7070 127.0.0.1:7070
```
or a variation of it.

If one were to believe [http://www.cyberciti.biz/faq/create-ssh-config-file-on-linux-unix/](http://www.cyberciti.biz/faq/create-ssh-config-file-on-linux-unix/)
and I generally do. ;)


LocalForward in 
```
man ssh_config
```

---

### Post by Lars Noodén on 2015-11-13
> **Habitual said:**
> looks like
```
LocalForward ...
```

It would actually be [DynamicForward](http://manpages.ubuntu.com/manpages/trusty/en/man5/ssh_config.5.html) because of the -D 

```

DynamicForward 7070

```

If you are using the connection only for tunneling then you might want to throw in a 'ExitOnForwardFailure=yes' there also.

The for -T

```

RequestTTY no

```

And the -f implies the -n, so the latter is not needed, but the -N is.  But I don't (yet) see a way to skip the -fN part.

---

### Post by Lars Noodén on 2015-11-13
And for the -q you have 

```

LogLevel QUIET

```

or 

```

LogLevel FATAL

```

---

### Post by zaphod_es on 2015-11-13
Thanks a lot Lars, that was a great help.  I did not understand the man pages but now I see how it all works.

---

### Post by Habitual on 2015-11-13
Yes, Thanks Lars.

---

