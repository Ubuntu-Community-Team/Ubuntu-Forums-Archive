---
title: "&quot;Bad : modifier in $ (~).&quot; error with tcsh; similar solutions have not worked"
date: 2015-02-20
forum: General Help
---

### Post by jacksondhayward on 2015-02-20
Hello everyone,

I've been having some trouble with trying to run scripts with tcsh or even just running tcsh in general. Everytime I do I get the error "Bad : modifier in $ (~)." I've searched online and found similar problems that suggest using export in bash or setenv in tcsh and wrapping PATH but I haven't had any success with it. I thought it might be a permissions problem but sudo doesn't change anything. Any suggestions would be appreciated!

I'm running Ubuntu 14.04 LTS, GNU bash, version 4.3.11(1)-release (x86_64-pc-linux-gnu), and tcsh 6.18.01 (Astron) 2012-02-14 (x86_64-unknown-linux).

---

### Post by steeldriver on 2015-02-21
What is the output of

```

printenv | grep '~'

```

run from the tcsh?

---

