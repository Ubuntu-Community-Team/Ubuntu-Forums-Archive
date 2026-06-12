---
title: "Backup script not working in Edgy (dash related?)"
date: 2006-11-23
forum: General Help
---

### Post by chpts on 2006-11-23
Hi everyone:

I recently upgraded to Edgy and one of my scripts for backing up in the previous release (namely this one: [http://gentoo-wiki.com/TIP_Backup_using_cron_(simple)](http://gentoo-wiki.com/TIP_Backup_using_cron_(simple)) ) stopped working with the following errors:

backup.sh: 7: source: not found
backup.sh: 26: [[: not found
backup.sh: 29: Syntax error: "(" unexpected

This didn't happen before, could it be related to the now default usage of /bin/dash instead of bash?

Thanks a lot,

Juan.

---

### Post by Junx on 2006-11-23
Change the shebang from "#!/bin/sh" to "#!/usr/bin/env bash"

---

### Post by chpts on 2006-11-23
Thanks for your reply, I changed the line "#!/bin/bash" (there was no #!/bin/sh line in the original scripts) to "#!/usr/bin/env bash" unfortunately it still throws the same errors.

Any ideas?

Thanks.

---

### Post by 454redhawk on 2006-12-14
> **Junx said:**
> Change the shebang from "#!/bin/sh" to "#!/usr/bin/env bash"

Whats the deal with that? Why cant edgy see the normal #!/bin/sh ?


Some of my scripts dont work unless I do as you suggested but scripts I have downloaded have the #!/bin/sh and work.

Whats up?

---

### Post by po0f on 2006-12-14
454redhawk,

They don't use Bash-specific features like cooler scripts do.

To get Bash to be the default shell interpreter instead of Dash (/bin/sh by default on Edgy is a symlink to /bin/dash, we want it to be /bin/bash :)):
```
[FONT="Courier New"]$ sudo dpkg-reconfigure dash[/FONT]
```

---

