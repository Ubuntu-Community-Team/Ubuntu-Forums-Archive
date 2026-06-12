---
title: "Searching apt repositories"
date: 2008-05-22
forum: General Help
---

### Post by slacker9876 on 2008-05-22
I never had a need before now, but as I am installing RT, a help desk ticketing system on my Ubuntu 8.04 server, I have many unsatisfied dependencies. There is no GUI on this system (no synaptic) and I need to search for the version numbers via wildcard. After a review of the man files for apt-get I could not locate what I needed. In a side question what are "super-cow powers?" I am told many of the repos have this.

Thanks

---

### Post by forestpixie on 2008-05-22
I use apt-cache search

```
apt-cache search package
```

with * - not sure about any other wildcards - look in the man page

man apt-cache

On the other note

```
apt-get moo
```

---

### Post by kerry_s on 2008-05-22
you can make your life easier by adding alias's to bashrc
mine:
```
alias su='sudo -i'
alias update='sudo apt-get update;sudo apt-get -u dist-upgrade'
alias install='sudo apt-get install'
alias remove='sudo apt-get remove --purge'
alias search='apt-cache search'
alias show='apt-cache show'
alias clean='sudo apt-get clean'
alias fix='sudo apt-get -f install'

```

then you just use:

search name
show name
install name
etc...

also you can use aptitude, its like synaptic for the console, a bit of learning though
to launch:

sudo aptitude

---

