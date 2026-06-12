---
title: "Messed something up in terminal/synaptic."
date: 2007-11-21
forum: General Help
---

### Post by Blice on 2007-11-21
Hi!

I was following a short how-to on installing activematix I think it was called. It was another add/remove manager type of program; But it had OpenXML so I wanted it. I typed the commands in that the tutorial said to, it didn't do anything, so I shrugged and closed out to find a different method of getting OpenXML. 

One of those commands messed up my Synaptic. It was 'deb' and then a link to the activematix website and some other stuff. 


Here's a screenshot of this error message: [http://img.photobucket.com/albums/v20/Ub3r_n00b/Screenshot-1.png](http://img.photobucket.com/albums/v20/Ub3r_n00b/Screenshot-1.png)


I appreciate any help.

---

### Post by ticopelp on 2007-11-21
I would copy and paste your sources.list file so people can see what line to fix. 

```
sudo gedit /etc/apt/sources.list
```

Then cut and paste everything in that file here, it probably won't be too hard to find the culprit.

---

### Post by Blice on 2007-11-21
> **ticopelp said:**
> I would copy and paste your sources.list file so people can see what line to fix. 

```
sudo gedit /etc/apt/sources.list
```

Then cut and paste everything in that file here, it probably won't be too hard to find the culprit.

I can't find sources.list :[


EDIT: Nevermind, I'm dumb.

I tried to delete that line and save, but I don't have permissions. Should I log in as root to do this?

---

### Post by ticopelp on 2007-11-21
> **Blice said:**
> I tried to delete that line and save, but I don't have permissions. Should I log in as root to do this?

You don't have to be logged in as root, just sudo, like in the line of code I pasted above.

---

