---
title: "bash script rsync sshpass jump host - No such file or directory"
date: 2020-10-22
forum: General Help
---

### Post by seawasp on 2020-10-22
Hi,
I have an rsync command that works perfectly from the command line, but fails with "rsync: No such file or directory" when I try to run it from a bash script.
If I echo the command from the bash script and then cut and paste it into the command line, it again works.

Original command as typed into the command line (edited for security):

```
rsync -aPv --delete -e 'sshpass -p pw_for_source ssh -o ProxyCommand="sshpass -p pw_for_jump ssh -W %h:%p userjump@ip.add.of.jump -p 22" usersource@ip.add.of.source -p 22' :/directory_ on_ source/ /media/username/"Seagate Desktop Drive"/backup
```

As it appears in the bash script
```

#!/bin/bash

command=(rsync -aPv --delete -e \'sshpass -p pw_for_source ssh -o ProxyCommand=\"sshpass -p pw_for_jump ssh -W %h:%p userjump@ip.add.of.jump -p 22\" usersource@ip.add.of.source -p 22\' :/directory_ on_ source/ /media/username/\"Seagate Desktop Drive\"/backup/);

"${command[@]}";
```

Background
The command is run from a remote machine and used to backup an internal server to a remote external drive using rsync. It uses ssh to connect, via a jump server, to the internal network server and uses sshpass to automate passwords. The fact that it works fine from the CLI and the bash output can be used on the CLI makes me think that it is something to do with how the bash script interprets it.

PS I know it isn't the most secure solution and I will be going about it differently in future, but it's become more of a challenge to solve/discover why. 

**[Solution]**
So, it was that bash wasn't seeing what was being echoed.
By using:
```

bash -x filename

```
I was able to output exactly what bash was seeing and I had too many escapes.
Revised code...
```

#!/bin/bash

command=(rsync -aPv --delete -e 'sshpass -p pw_for_source ssh -o ProxyCommand="sshpass -p pw_for_jump ssh -W %h:%p userjump@ip.add.of.jump -p 22" usersource@ip.add.of.source -p 22' :/directory_ on_ source/ /media/username/"Seagate Desktop Drive"/backup/);

"${command[@]}";
```

Easy when you know how :D
Thank you col48 for your input.
Chris

---

### Post by col48 on 2020-10-23
Could it be something to do with permissions?  Does interposing bash affect it?  Maybe you->rsync can see more than you->bash->rsync?
Finding out what rsync *can* see might shed some light.

---

### Post by seawasp on 2020-10-23
Thank you col48,
Permissions didn't turn out to be the problem, but it got me thinking and I learnt a bit on the way.
I'll edit the solution into my original post
Thanks again 
Chris

---

