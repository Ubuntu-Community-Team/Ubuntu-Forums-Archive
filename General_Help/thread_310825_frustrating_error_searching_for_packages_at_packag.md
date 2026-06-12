---
title: "frustrating error searching for packages at packages.ubuntu.com"
date: 2006-12-01
forum: General Help
---

### Post by styracosaurus on 2006-12-01
I often get this error when searching for packages at packages.ubuntu.com:

"Error: keyword not valid or missing"

It seems to happen a lot when I use more than one search term, for instance searching for "video editor" without quotes.

Sorry if this has been address a million times.

---

### Post by LLRNR on 2006-12-01
```
apt-cache search *packagename*
```or even```
sudo aptitude install apt-file
apt-file update
apt-file search *filename*
apt-file list *packagename*
```

LLRNR

---

### Post by towsonu2003 on 2006-12-01
> **styracosaurus said:**
> packages.ubuntu.com

it's most useful if you're looking to see if a software (keyword => software's name) is available in the repos... i.e. if I want to find a "standalone player for flv format files", I use synaptic or apt-cache.

---

