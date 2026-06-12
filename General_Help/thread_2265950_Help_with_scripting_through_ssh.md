---
title: "Help with scripting through ssh?"
date: 2015-02-18
forum: General Help
---

### Post by Irrationalis on 2015-02-18
Hello all,
I have two scripts on my server machine:

Server Script 1:
sleep.sh

```

#!/bin/bash
sudo pm-suspend

```

Server Script 2:
blank.sh

```

#!/bin/bash
sudo vbetool dpms off

```

I have set the NOPASSWD permissions for both the pm-suspend and vbetool commands in the server's sudoers file.
I need to be able to quickly run these command from a client machine.
I accomplished the first command by creating a script on the client machine. I also had to setup a password-less key for ssh.

Client Script 1:

```

#!/bin/bash
ssh user@ipaddr "sh /home/user/sleep.sh"

```

This works perfectly, it puts the server in a sleep state, waiting for a WOL request.

Client Script 2:

```

#!/bin/bash
wakeonlan -f WOL
ssh user@ipaddr “sh /home/user/blank.sh”

```

This script is half working. I need this script to send a WOL packet to the server, and then blank the server's monitor. It's an iMac running Ubuntu 12.04 LTS, so I can't remove the display.

I gave this script the same syntax for the ssh command as the first script. 
The wakeonlan command works, but the ssh command returns the error:

```
bash: $'\342\200\234sh': command not found
```

What am I doing wrong here?

---

### Post by steeldriver on 2015-02-18
The specific error seems to be because the “ quotes in your Client Script 2 are non-ascii characters: start by replacing those with plain "

---

### Post by Irrationalis on 2015-02-18
#-oWow. That was the problem! My text editor keeps autoformatting quotes, I need a new one. Thanks, steel.

---

