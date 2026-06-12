---
title: "Activating Repos. from terminal"
date: 2007-01-07
forum: General Help
---

### Post by kd7swh on 2007-01-07
Can the Universal and Multiversal repositories be activated from the terminal? (rather that using synaptic)

maybe with an apt string? or with aptitude. 

I am trying to write a script and this would be helpful.

---

### Post by aysiu on 2007-01-07
You activate those repos from the terminal by using the *nano* editor to edit your /etc/apt/sources.list ```
sudo nano -B /etc/apt/sources.list
```

---

### Post by kd7swh on 2007-01-07
I know I can edit the sources with nano or emacs (i like emacs) but I want to add the multiversal and universal repos. to the active software channel. 

in other words I want to run this  script on a fresh install that could go download and install things from the universal repos. and i want to add repos, other than "main" to the software channel without using synaptic before running the script.

---

### Post by jocko on 2007-01-07
Instead of having the script modifying an existing sources.list, why not have it replace it with a new file, with all the repos enabled?

Something like:
```
cp /etc/apt/sources.list /etc/apt/sources.list.bak
cp /path/to/new/sources.list /etc/apt/sources.list
```Otherwise I think the command "sed" can be used to add/remove/replace text in files.
```
 man sed
``` may give you some help.

---

### Post by kd7swh on 2007-01-07
I am just going to copy a custom source list to /etc/apt in the script...


lol I was just a few minutes late to see that post...

---

