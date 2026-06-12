---
title: "Adding a directory to every user's /home"
date: 2006-11-20
forum: General Help
---

### Post by madtinkerer on 2006-11-20
Hi,

I need to add a new directory to the /home dir of every user on my server.  How can I go about doing this without doing it all manually?  I know how to do it with /etc/skel when users are created, but how does one do it after all the accounts have been created?

---

### Post by dcstar on 2006-11-21
> **madtinkerer said:**
> Hi,

I need to add a new directory to the /home dir of every user on my server.  How can I go about doing this without doing it all manually?  I know how to do it with /etc/skel when users are created, but how does one do it after all the accounts have been created?

Create a script that goes through each directory under /Home, creates the directory and then sets the appropriate ownership rights etc.

There may already be some around if you do a search.

---

### Post by hearnden on 2006-11-21
Something like:

```

$ cd /home
$ for d in *; do 
    newdir="$d/DIR"
    sudo mkdir -p "$newdir"
    sudo chmod MODE  "$newdir"
    sudo chown "$d:GROUP" "$newdir"
done

```

sounds easy enough, for adding DIR with permissions MODE and group GROUP to all users.

---

