---
title: "How to fix owner/group to default settings ubuntu"
date: 2008-03-06
forum: General Help
---

### Post by BlackDex on 2008-03-06
Hello there,

A friend of mine has messedup his owner/group permissions of the / folder.

All root:root have been changed.

Is there a way to change this back to the original settings?
Also, the same is for the permissions (chmod).

Now things like sudo etc.. arn't working anymore.

Thx in advance.

---

### Post by kuja on 2008-03-06
Easier said than done!!!

There is no automated way to do it. You could opt to try to try the shotgun approach (chown -R root:root /usr /bin /sbin .....) and then manually fix things as they come up but there will likely be things you miss and problems resultant, in addition to it taking time.

You're better off reinstalling ........   and remember - sudo is not a toy. I hope the /home folder is stored on a seperate partition, if not, I recommend you put it there if you do decide to reinstall - it's very worthwhile to do so, for situations like this.

---

