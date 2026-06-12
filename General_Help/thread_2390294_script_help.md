---
title: "script help"
date: 2018-04-27
forum: General Help
---

### Post by zergling on 2018-04-27
Hello everyone,

I am trying to run the following script in background but I am unable to do so...
The script works as it should if I run it via terminal such as

```

./myScript.sh

```

but, if I try to execute it lets say, via a custom application launcher, as soon as I enter my password, the terminal window close instantly and with that, it will also close my sshfs connection.

```

#!/bin/bash

sshfs -o IdentityFile=/home/$USER/remote.key USER@XXX.XXX.XXX.XXX:/media/server_data /home/$USER/server_data/ -p 63

```

What I would love is to be able to execute the script, insert my password and even though the terminal window closes, my sshfs would still running in background.

Is that possible? If so, how do I accomplish that?

Thank you in advance ^_^

---

### Post by TheFu on 2018-04-27
If you use ssh-keys, then you won't be prompted for a password, provided they've been unlocked.  I have no idea how to unlock them outside a terminal, sorry.

ssh with keys is one of those few things in this world that are both, more convenient AND more secure.
All ssh-based tools honor ssh-keys and the ~/.ssh/config file, which makes using both really excellent. You won't need to specify the key file or port on the sshfs line.

Of course, somehow, you'll need to unlock the keys BEFORE point-n-click will work. Lots of ways to do that and you can set the amount of time allowed for the ssh-key to be unlocked to control the security risks you allow.  Might consider placing your keys on a USB stick or use a crypto-card to keep them locked.

IMHO.

---

