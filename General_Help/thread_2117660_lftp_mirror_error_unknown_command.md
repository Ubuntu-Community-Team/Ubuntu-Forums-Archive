---
title: "lftp mirror error unknown command"
date: 2013-02-19
forum: General Help
---

### Post by norjms on 2013-02-19
I'm recieving this error when I try to sync a remote server. I don't know what is causing Unknown command `;'. The script works I'm just trying to get rid of the minor error. 

This is the cli output
```

XXXXX@prime:~# ./downloadremote.sh
source: Is a directory
Unknown command `;'.      

```

This is the script itself
```

#!/bin/bash
HOST='randomhost.com:990'
USER='XXXXX'
PASS='somepassword'
lftp -f "
open $HOST
user $USER $PASS
mirror --Remove-source-files remote/active /media/b85fb27e-e4e3-44c2-821f-bdb11b296c5e/remote/archive
bye
"
```

Thanks for taking a look.

---

### Post by apmcd47 on 2013-02-19
Okay, first I'd like to suggest that you don't include the password in the script. Instead, use the *.netrc* file which would be kept in the home directory and has the format:
```
machine *randomhost.com* login *user* password *somepass*
```Caveat: As I have never used *ftps* I don't know whether it still uses the *.netrc* file. I assume you are using an *FTPS* server as I looked up port 990.

Second, as you are using **lftp** which understands URIs I would change the invocation to something like:
```
lftp "ftps://$USER@$HOST"
```


Third, you are using the wrong switch: -f is to invoke a file which contains the commands you want **lftp** to run. You should be using the -e switch. The final command should look something like:
```

USER=some-user
HOST=randomhost.com
lftp -e "mirror --Remove-source-files remote/active /media/b85fb27e-e4e3-44c2-821f-bdb11b296c5e/remote/archive" "ftps://$USER@$HOST"
```

I hope this helps.

Andrew

---

