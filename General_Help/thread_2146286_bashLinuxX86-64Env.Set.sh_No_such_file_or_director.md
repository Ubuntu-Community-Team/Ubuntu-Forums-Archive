---
title: "bash:LinuxX86-64Env.Set.sh: No such file or directory"
date: 2013-05-17
forum: General Help
---

### Post by IT Researcher on 2013-05-17
i  needed to run the code 

source LinuxX86-64Env.Set.sh


but it says bash: LinuxX86-64Env.Set.sh: No such file or directory


how can i solve this ...any suggestion
the code is used for Including  the configured environment(i configured it just prior to this step)

---

### Post by oldos2er on 2013-05-18
Is LinuxX86-64Env.Set.sh executable? ```
chmod +x LinuxX86-64Env.Set.sh
``` What directory is LinuxX86-64Env.Set.sh in? You need to run the source command in the same directory, or give the absolute path to LinuxX86-64Env.Set.sh, for example ```
source /home/user/Downloads/LinuxX86-64Env.Set.sh
```

---

