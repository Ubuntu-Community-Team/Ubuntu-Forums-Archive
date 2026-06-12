---
title: "ssh + nohup + bash script = Permission Denied"
date: 2015-03-15
forum: General Help
---

### Post by peridian on 2015-03-15
Hi,

I can't get my head around why nohup results in the following behaviour.

Using the below command works fine:

```

ssh -p 9999 -t user@hostname "sudo /path/to/script"

```

Using the below command results in the first two commands in the script working fine, but the last one gets a permission denied error in the auth.log:

```

ssh -p 9999 -t user@hostname "sudo -b nohup /path/to/script > /dev/null 2>&1 &"

```

Script:

```

#!/bin/bash
rsync -a /path1/ /path2/
sync
pm-suspend

```

At first I thought it was a user permissions problem, but I have tried this with three valid users now, and they all exhibit the same behaviour.

It's as though the permissions are valid for a period of time, and then by the time it tries to run the last command, it can no longer authenticate.

I can keep this working on the first command, but I had figured I should close the ssh connection properly, hence tried the second command.

Any ideas?

Regards,
Rob.

---

### Post by peridian on 2015-03-16
Well, I don't know what's going on, but for some reason adding the user account that runs this script to the admin group instead of the sudo group has sorted this out.  The script is now working as expected.

Regards,
Rob.

---

