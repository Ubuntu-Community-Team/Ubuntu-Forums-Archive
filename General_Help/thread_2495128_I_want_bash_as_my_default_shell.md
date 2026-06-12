---
title: "I want bash as my default shell"
date: 2024-02-07
forum: General Help
---

### Post by fleshbits on 2024-02-07
I am writing a docker file that will use ubuntu. Google told me this line will make bash my default script:   

FROM ubuntu:22.04
...
    # Use bash by default
ln -sf /bin/bash /bin/sh   

     
However when I start the docket container it still has a sh 5.1  prompt. If I `which sh` it tells me it is out of /usr/bin. So, I guess  the symlink doesn't work. I am not sure why there is one in /usr/bin as  well as regular /bin, as I am not that versed in the ways of linux yet,  but I am trying!   

     
How can I make it always boot up using bash rather than sh?

---

### Post by VMC on 2024-02-07
what does this show:```
cat /etc/passwd
```
Look for your login name, and at the end, it should show you what shell your using

---

### Post by btindie on 2024-02-07
> Google told me this line will make bash my default script:
That's only true if the user you're running it as uses [FONT=tahoma]/bin/sh[/FONT] as their shell.

You haven't mentioned what you're doing in your dockerfile in terms of adding users etc so without additional detail it's hard to say what's wrong.

When you run that image
```
docker run --rm -it ubuntu:22.04
```
it uses the defaults for that container which are to login as *root* and run [FONT=system]/bin/bash[/FONT]

You can use [FONT=system]docker inspect ubuntu:22.04[/FONT] to see what the defaults are.

Have you changed the CMD in the dockerfile?

It may be that the default shell for the user you're running it as is /bin/dash and so that symlink will have no affect.

As mentioned already, /etc/passwd will tell you which is the default shell for the user. You can find out the shell for a specific user with:
```
getent passwd root | cut -d: -f7
/bin/bash
```
replace 'root' with your custom username.

---

