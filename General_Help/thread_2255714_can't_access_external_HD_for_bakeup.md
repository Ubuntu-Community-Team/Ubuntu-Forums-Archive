---
title: "can't access external HD for bakeup"
date: 2014-12-07
forum: General Help
---

### Post by luke40 on 2014-12-07
The backup program told me that I have no permission when I tried to backup using the external HD, but the owner of the external HD is same as my login name. I think it's becase it was created when I was using Fedora. But I can access it (R/W) normally now despite of being unable to backup.

Now the question is, how to make it accessible for backing up without recreating it? Is the reason mentioned above true?

---

### Post by carl4926 on 2014-12-07
Probably just need to chown it

---

### Post by yancek on 2014-12-07
> I think it's becase it was created when I was using Fedora. But I can  access it (R/W) normally now despite of being unable to backup.

Backing up to a partition on an external drive is writing to it so how are you doing it?  If you run ls -l on the mount point which should be under /media/username, who is the owner and what are the permissions?

---

### Post by JKyleOKC on 2014-12-07
As Carl says, probably you just need to change owner on the external HD. Internally, owner and group values are stored as their numeric values, not as strings. Fedora assigns user IDs starting at 500; Ubuntu starts at 1000. Thus even though you used the same user name, the stored value will be different. Doing a "chown" command from Ubuntu will change the stored value and ought to solve your problem. Be sure to prefix the command with "sudo" to overcome the initial permissions issue, though...

---

