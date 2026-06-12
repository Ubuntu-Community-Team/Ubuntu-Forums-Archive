---
title: "Adding a bin folder to bash profile"
date: 2006-12-08
forum: General Help
---

### Post by boz on 2006-12-08
I recently installed the entire gEDA suite from source provided by a CD on their website.  After the installation, I'm instructed to copy and paste the following commands into a terminal window.  

```
export PATH=/home/boz/geda-install/bin:${PATH}
export LD_LIBRARY_PATH=/home/boz/geda-install/lib:${LD_LIBRARY_PATH}

```

This works fine, but it becomes a bit cumbersome and I would like to know if it's possible to permanently add these two lines to my bash profile.

---

### Post by yabbadabbadont on 2006-12-08
Yes, just edit your .bash_profile and add those two commands at the bottom.

---

### Post by po0f on 2006-12-08
boz,

It'd probably be better to put those exports in ~/.bashrc instead of ~/.bash_profile.  [This](http://telin.ugent.be/~slippens/drupal/?q=bashrc_and_others) was a quick hit off Google.  Most likely you'll be using gnome-terminal (or some other terminal emulator) in X, and these are (again) most likely not set up to execute Bash as a login shell, so ~/.bashrc will be sourced.

---

### Post by yabbadabbadont on 2006-12-08
> **po0f said:**
> boz,

It'd probably be better to put those exports in ~/.bashrc instead of ~/.bash_profile.  [This](http://telin.ugent.be/~slippens/drupal/?q=bashrc_and_others) was a quick hit off Google.  Most likely you'll be using gnome-terminal (or some other terminal emulator) in X, and these are (again) most likely not set up to execute Bash as a login shell, so ~/.bashrc will be sourced.

Good point.  I forgot to mention that I always create a symbolic link called .profile that points to my .bash_profile.  (.profile is sourced when you login through GDM)  ((I found that out through trial and error... ](*,) ))

---

### Post by boz on 2006-12-08
Thanks, both of you.  That worked perfectly.

---

