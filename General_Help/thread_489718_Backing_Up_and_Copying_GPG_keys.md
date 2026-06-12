---
title: "Backing Up and Copying GPG keys"
date: 2007-07-01
forum: General Help
---

### Post by boredandblogging.com on 2007-07-01
On my Feisty laptop, I've got my GPG keys. I would like to wipe it and install Gutsy on it, but first, I want to back up my GPG keys. 

What is the best way of doing this? Should I export my keys somehow in Feisty and then import them in Gutsy?

Or do I simply copy over my ~/.gnupg directory from Feisty to Gutsy and restart gpg-agent in Gutsy?

---

### Post by dreadlord_chris on 2007-07-02
> **boredandblogging.com said:**
> On my Feisty laptop, I've got my GPG keys. I would like to wipe it and install Gutsy on it, but first, I want to back up my GPG keys. 

What is the best way of doing this? Should I export my keys somehow in Feisty and then import them in Gutsy?

Or do I simply copy over my ~/.gnupg directory from Feisty to Gutsy and restart gpg-agent in Gutsy?

you could probably copy over the folder - just check the permissions after, make sure that everything is **owned** by you and **not** writable by *others*

---

