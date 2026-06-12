---
title: "apt-get autocompletion"
date: 2008-03-24
forum: General Help
---

### Post by chadeldridge on 2008-03-24
My autocompletion in bash seems to be completely broken in Hardy.  Namely in apt-get install the package name will not autocomplete.

---

### Post by mali2297 on 2008-03-24
> **chadeldridge said:**
> My autocompletion in bash seems to be completely broken in Hardy.  Namely in apt-get install the package name will not autocomplete.

You need to install the package **bash-completion** (in the universe repo).

[https://bugs.launchpad.net/ubuntu/+source/bash/+bug/196021](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/196021)

---

### Post by chadeldridge on 2008-03-24
Its already install, but not working.  I will try a purge and reinstall.

---

### Post by lefthand on 2008-03-26
This worked for me (after restarting the terminal). I hope this gets put back in the final release.

---

### Post by `GooZ´ on 2008-03-28
Yes. Why isn't this installed by default? Is there already a bug filed on this?

---

### Post by mali2297 on 2008-03-28
> **`GooZ´ said:**
> Yes. Why isn't this installed by default? Is there already a bug filed on this?

See the link in the second post.

---

### Post by `GooZ´ on 2008-03-29
Silly me. Thanks :)

---

### Post by chadeldridge on 2008-03-29
Autocompletion works in bash but not in apt-get ... any ideas?

---

### Post by mali2297 on 2008-03-29
> **chadeldridge said:**
> Autocompletion works in bash but not in apt-get ... any ideas?

Do you have these lines in your .bashrc? (uncommented)
```

if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

```

Also check that /etc/bash_completion exists.

---

### Post by strabes on 2008-03-29
This was a bug in an earlier release of hardy; copying the /etc/bash_completion file from gutsy fixed it for me and many others.

---

### Post by chadeldridge on 2008-03-29
Great catch.  the lines were there but commented out.  I should have caught that, but I guess i missed it.  I had tryed to copy the bashrc from another user but the issue persisted.  Thank you very much.

---

