---
title: "Edit repositories in Lubuntu"
date: 2013-04-25
forum: General Help
---

### Post by pjalegria on 2013-04-25
Hi

How can i remove/delete third party repositories in Lubuntu after the 13.04 upgrade since i have deactivetd repositories and in synaptic manager dont allow?

---

### Post by pjalegria on 2013-04-25
Problem solved with Ubuntu Tweak....

---

### Post by snowpine on 2013-04-25
For future reference, you can edit /etc/apt/sources.list or the relevant files in /etc/apt/sources.list.d/ with your favorite text editor, using sudo. 

For example:

```
gksu leafpad /etc/apt/sources.list
```

or (on my computer; yours will be different):

```
sudo nano /etc/apt/sources.list.d/ehoover-compholio-quantal.list
```

This method works in all 'buntu family releases and flavors. :)

DISCLAIMER: software source errors are one of the Top 10 causes of support requests here on the forums, so tread lightly---if you aren't sure what/how to edit, then ask here on the forums, post a copy of your sources.list and someone will help you. :)

---

