---
title: "Malformed line in source list"
date: 2007-02-05
forum: General Help
---

### Post by crimsonmx on 2007-02-05
I have the nearly the same problem as this user:
[http://ubuntuforums.org/showthread.php?p=2019042]("http://ubuntuforums.org/showthread.php?p=2019042")
except I only get the error:

E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)

my sources.list looks like this
```
# deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security restricted main multiverse universe #Added by software-properties
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

and my edgy-multiverse.list looks like this:
```
# automatically added by gnome-app-install on 2007-02-02 22:43:25.526790
deb http://us.archive.ubuntu.com/ubuntu/ edgy
deb http://security.ubuntu.com/ubuntu edgy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates multiverse

```

The error occurs whenever I try to open the package manager or anything related, I think
Thanks in advance for any help, I'd really appreciate it.

---

### Post by taurus on 2007-02-05
Edit /etc/apt/sources.list.d/edgy-multiverse.list

```
gksudo gedit /etc/apt/sources.list.d/edgy-multiverse.list
```
and put a # sign in front of this line.

```
deb http://us.archive.ubuntu.com/ubuntu/ edgy
```
Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by crimsonmx on 2007-02-05
I applied the change, but I'm still getting errors

I now get two of the original error messages, plus this one

E: The list of sources could not be read.

Thanks for responding so quickly, btw.

---

### Post by taurus on 2007-02-05
Can you post your /etc/apt/sources.list.d/edgy-multiverse.list again?

```
cat /etc/apt/sources.list.d/edgy-multiverse.list
```

---

### Post by crimsonmx on 2007-02-05
# automatically added by gnome-app-install on 2007-02-02 22:43:25.526790
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates multiverse

---

### Post by taurus on 2007-02-05
Try to make the last line to look like this.

```
deb http://archive.ubuntu.com/ubuntu edgy-updates multiverse
```
Save it and run those two commands again.

```
sudo aptitude update
sudo aptitude upgrade
```
And if there is an error,  paste the command and the whole error message here.

---

### Post by crimsonmx on 2007-02-05
$ sudo aptitude update
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.
$sudo aptitude upgrade
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.

---

### Post by taurus on 2007-02-05
Post your /etc/apt/sources.list.d/edgy-universe.list here then.

```
cat /etc/apt/sources.list.d/edgy-universe.list
```
I bet it's the same problem as /etc/apt/sources.list.d/edgy-multiverse.list!

---

### Post by crimsonmx on 2007-02-05
I went ahead and applied the logical changes, and it works!

Thanks a lot for the help, I was in a bit of a bind

---

