---
title: "Script runs manually but not automatically"
date: 2015-01-13
forum: General Help
---

### Post by abasel on 2015-01-13
I have the following script /etc/profile.d/nvm.sh

```

#!/bin/bash
export NVM_DIR=/media/datadrive/nodejs/nvm

export NPM_CONFIG_PREFIX=/media/datadrive/nodejs/node
export PATH="media/datadrive/nodejs/node/bin:$PATH"/

source /opt/nvm/nvm.sh

```

When I login as admin it runs file.

When I login as a new user that I created I get the following:
> -sh: 7: /etc/profile.d/nvm.sh: source: not found


If I then enter  /etc/profile.d/nvm.sh directly at the command-line (logged in as the new user) I get no errors.

What am I missing?

---

### Post by nerdtron on 2015-01-13
When you are logged in as a new user can you run the command: "source /opt/nvm/nvm.sh" ?

---

### Post by abasel on 2015-01-13
Yes, but I think I just fixed it. I noticed that my tab-complete was not working for this user which on digging further revealed that I need to run

> sudo chsh -s /bin/bash <username>

This seemed to fix it.

---

### Post by steeldriver on 2015-01-13
I think what's  happening is that **files in /etc/profile.d are themselves sourced rather than executed** - so the shebang is ignored. So in case the user's login shell is dash (the default, when created via useradd rather than adduser), they shouldn't themselves use bashisms - in this case, a better solution probably be to use 

```

**.** /opt/nvm/nvm.sh

```

(the **.** is a POSIX-compatible synonym for [FONT=courier new]source[/FONT]) and - for the sake of clarity - remove the #!/bin/bash.

---

