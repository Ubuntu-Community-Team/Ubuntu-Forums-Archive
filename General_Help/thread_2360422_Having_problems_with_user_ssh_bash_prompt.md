---
title: "Having problems with user ssh bash prompt"
date: 2017-05-04
forum: General Help
---

### Post by trexmax on 2017-05-04
using Ubuntu 16.04 LTS. 

I'm using putty and when I login in as a user I created in Ubuntu, I get the bash prompt instead of the hash prompt.  Also, when I press the back key or up key I get the following text displayed instead the cursor moving: "^[[[A" or "^[[[D".  In addition, when I press the tab key to autocomplete it does not do anything; instead, it just tabs over.  I don't have these problems when I'm logged in as root user. I get the hash prompt also with the root user.  What do I have to do to make this work with the user I created?

Also, I can't even delete a folder without typing sudo before the command and every time I'm asked for the password. Is there anyway to supply the password automatically?

Thanks.

---

### Post by QIII on 2017-05-04
Hello!

Hopefully you will get a direct answer soon.  I haven't one for you because I don't use PuTTY.  Are you aware that PuTTY is not necessary when running Linux and that allowing root login remotely is an extremely unsafe practice?

---

### Post by trexmax on 2017-05-04
Hi Q, :)

Thanks for the warning, but still stumped as to my issue.

---

### Post by steeldriver on 2017-05-04
Sounds like you are in the dash shell not the bash shell - what happens if you type

```

bash

```

Does it work after that?

---

### Post by trexmax on 2017-05-04
> **steeldriver said:**
> Sounds like you are in the dash shell not the bash shell - what happens if you type

```

bash

```

Does it work after that?

Yes, this works and fixes all the problems I described in the first post.  Before applying this fix the prompt was "$" but afterwards it is "user@localhost:/$".  How can I make it so that the bash command is always run when I login or how can I make it so that I get this prompt everytime I login: "user@localhost:/$"?

Thanks.

---

### Post by steeldriver on 2017-05-04
Most likely it's just a matter of setting your login shell on the remote host - but let's check. What are the outputs of the following:

```

echo $SHELL

getent passwd $USER | awk -F: '{print $NF}'

```

---

### Post by trexmax on 2017-05-04
> **steeldriver said:**
> Most likely it's just a matter of setting your login shell on the remote host - but let's check. What are the outputs of the following:

```

echo $SHELL

getent passwd $USER | awk -F: '{print $NF}'

```

After typing "bash" and hitting the enter key I typed the commands:

**echo $SHELL** returns this: "/bin/sh"

**getent passwd $USER | awk -F: '{print $NF} **returns a blank/empty line.

---

### Post by steeldriver on 2017-05-04
OK let's try

```

chsh -s /bin/bash

```

Then start a new PuTTY session

---

### Post by trexmax on 2017-05-04
> **steeldriver said:**
> OK let's try

```

chsh -s /bin/bash

```

Then start a new PuTTY session

After typing bash and pressing enter key

**chsh -s /bin/bash** returns an error message: "you may not change the shell for user"

So, I typed sudo in front of the command like so:

**sudo chsh -s /bin/bash **returns no error message, but with a new putty session, I still get the $ dash prompt instead of the bash prompt and the original problems still persist without manually changing to a bash prompt. How can I make it permanent?

---

### Post by steeldriver on 2017-05-04
Hmm... is the remote system actually Ubuntu? AFAIK users should be permitted to change their own shells

Anyhow, **sudo chsh -s /bin/bash** would have changed root's login shell - **if** it is necessary to use sudo to run chsh, then you must add the target **user**:

```

sudo chsh -s /bin/bash LOGIN

```

where LOGIN is replaced by the actual login name of your user account.

---

### Post by trexmax on 2017-05-04
> **steeldriver said:**
> Hmm... is the remote system actually Ubuntu? AFAIK users should be permitted to change their own shells

Anyhow, **sudo chsh -s /bin/bash** would have changed root's login shell - **if** it is necessary to use sudo to run chsh, then you must add the target **user**:

```

sudo chsh -s /bin/bash LOGIN

```

where LOGIN is replaced by the actual login name of your user account.

I added the following at the end of the .profile file which is located in the user directory /home/user: "bash" without the quotes -- saved and started a new putty session and viola! bash shell automatically at login. :) Not sure if there is a better solution to this but I suppose this will have to do for now. 

Thanks for the help guys.

---

### Post by steeldriver on 2017-05-04
The better solution is to change your login shell to bash, using the chsh command . . .

---

### Post by trexmax on 2017-05-04
> **steeldriver said:**
> Hmm... is the remote system actually Ubuntu? AFAIK users should be permitted to change their own shells

Anyhow, **sudo chsh -s /bin/bash** would have changed root's login shell - **if** it is necessary to use sudo to run chsh, then you must add the target **user**:

```

sudo chsh -s /bin/bash LOGIN

```

where LOGIN is replaced by the actual login name of your user account.

OK, that modified command worked and it is actually a better solution as you said.  The bash shell is persistent with new putty sessions too. Thanks.

---

