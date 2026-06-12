---
title: "This should be an easy one: what is &quot;$home&quot;"
date: 2008-07-07
forum: General Help
---

### Post by lukethered on 2008-07-07
What is "$home", where is it located?  I've found it difficult to do a search on this, since a search for "$home" actually searches for "home".  Thanks for the help

---

### Post by ibutho on 2008-07-07
$HOME is the environmental variable that represents your home directory e.g. /home/someuser.

---

### Post by artir on 2008-07-07
$Home is a term ( like ~) that refers to your /home/yourusername.

Its useful in guides to make them more clear.

---

### Post by rogier.de.groot on 2008-07-07
You can find out the value on the command line by doing "echo $HOME"; usually it is indeed /home/(your_user_name) but I've set it can be set to something different.

---

### Post by andrew.46 on 2008-07-09
Hi,

As has already been suggested you can check each individual environmental variable by using:

```
$ echo $HOME
```

and to see them all simply use:

```
$ printenv
```

To show off your skills try:

```
$ printenv | grep ^HOME
```

   Andrew

---

### Post by Vivaldi Gloria on 2008-07-09
> **andrew.46 said:**
> and to see them all simply use:

```
$ printenv
```

Note that

```
env
```

also works.

---

