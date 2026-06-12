---
title: "tail -1 broken or new feature?"
date: 2008-07-09
forum: General Help
---

### Post by PadreSol on 2008-07-09
When did tail -1  * (that's a number one) stop working??

head -1 * works as always. Does anyone know why this has changed?

---

### Post by sdennie on 2008-07-09
"Tail -1" works fine for a single file.  For a group of files, I think you'll need to use:

```

tail -n1 *

```

---

### Post by PadreSol on 2008-07-09
head still works, why is tail doing things differently?  I don't expect you know since you didn't answer the question.  More of a rhetorical.

Too bad, it seems arbitrary and lame.

Maybe everything will be changed soon to ubuntu.gov, kernel.gov, debian.gov
(oh wait debian.gov happened two years ago with the openssl debacle)

---

### Post by ibuclaw on 2008-07-09
That could be a bug worth looking at, but to be honest, if you read the manpages, you are supposed to use "-n" option to specify the number of lines anyway.

But, curiously enough, you do have a small point.

The following couplings work as opposites in both apps:
```

head 1 *
tail 1 *

head -n1 *
tail -n1 *

```
So **head -1** and **tail -1** could be expected too.

But, alas. Use the **-n** option to display the number of lines from now on. That has been the way it has been, always.

Regards
Iain

---

### Post by PadreSol on 2008-07-09
tinivole, not to discourage, you have it wrong.

It has not always been this way.

and head 1 * and tail 1 * don't do jack.


head -1 still works, so why does tail -1 not? Again rhetorical since you don't know the answer either.

---

### Post by sdennie on 2008-07-10
No need to be upset or defensive:

**Hardy:**
```

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy
$ cd /etc
$ tail -1 *
tail: option used in invalid context -- 1

```

**Gutsy:**
```

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy
$ cd /etc
$ tail -1 *
tail: invalid option -- 1
Try `tail --help' for more information.

```

**Ubuntu 6.06.1 Live CD (Yes, that's 2006):** Same as Gutsy

**Fedora 9 Live CD:** Same as Hardy.

**Suse 10.3 Live CD:** Same as Hardy.

The command you are trying to run has not worked in Ubuntu for more than 2 years.  It also doesn't work in any recent version of any popular distro.  This is not something to flame Ubuntu for.  I agree that the inconsistency between head and tail is odd but, that's the way it is.

---

### Post by PadreSol on 2008-07-10
vor, agree about not getting upset/defensive.  So why are you getting upset/defensive?

But anyway I use many different *nix in the course of a day or week.  And one more inconsistency is just one more thing that's annoying.

Why would anyone change tail -1 ??  What did it break? Was someone annoyed by the option code that allowed -1 for tail?  (all rhetorical)

And it's not flaming.  If you think that's flaming than you ain't seen a real flame.  Don't be so sensitive.

I'll just create an alias and be on my way.

---

