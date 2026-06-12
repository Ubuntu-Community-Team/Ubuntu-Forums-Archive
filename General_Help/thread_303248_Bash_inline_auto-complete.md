---
title: "Bash inline auto-complete"
date: 2006-11-19
forum: General Help
---

### Post by CrapHouse on 2006-11-19
How do i setup bash auto-complete to do inline completions?

ie:
apt-<tab> would successively show
apt-cache
apt-cdrom
...

without listing all the choices at once

Thanks

---

### Post by dcstar on 2006-11-20
> **CrapHouse said:**
> How do i setup bash auto-complete to do inline completions?

ie:
apt-<tab> would successively show
apt-cache
apt-cdrom
...

without listing all the choices at once

Thanks

Not sure that is possible, I use the "!" feature to run the last command that matches, ie:

!dpk

may run the command "dpkg -i something.deb" that I had used previously and is in the BASH history.

---

### Post by pandu.rs on 2006-11-20
[http://dailyburrito.com/blog/2005/09/](http://dailyburrito.com/blog/2005/09/)

---

### Post by CrapHouse on 2006-11-20
> **pandu.rs said:**
> [http://dailyburrito.com/blog/2005/09/](http://dailyburrito.com/blog/2005/09/)

This worked great, thanks

also i like the history auto-complete functions as well

---

### Post by munkar on 2006-12-26
this is awesome. i like "Steve's approach":

> add the following lines to “.profile” or “.bashrc”:

# make bash autocomplete with up arrow
bind '"\e[A":history-search-backward'
bind '"\e[B":history-search-forward'

# make tab cycle through commands instead of listing
bind '"\t":menu-complete'

---

