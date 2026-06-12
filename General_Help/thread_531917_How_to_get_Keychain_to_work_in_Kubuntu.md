---
title: "How to get Keychain to work in Kubuntu"
date: 2007-08-22
forum: General Help
---

### Post by toucan on 2007-08-22
Hi,

I'm trying to get Keychain to work correctly under Kubuntu Feisty and I'm not having much success. I'm running:

```

steve@CARTMAN:~$ uname -a
Linux CARTMAN 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

```

and my *.bash_profile* looks like:

> # .bash_profile

# Initialize keychain if needed
if [ -r $HOME/.ssh/identity -o -r $HOME/.ssh/id_dsa -o -r $HOME/.ssh/id_rsa ]; then
        if [ ! -d $HOME/.keychain ]; then
                keychain ~/.ssh/id_dsa
                . ~/.keychain/$HOSTNAME-sh
        fi
fi


When I login to the desktop it then requests the password via an X ssh-askpass program but it seems to have no effect - if I then try to login to other systems I'm asked for the password again. If I run the *.bash_profile* script interactively everything is OK - it asks for the password and I can then login to other systems without further password requests as expected.

So it seems it's nearly working, but not quite.

Any ideas?

Steve

---

### Post by coxy on 2007-08-22
I have no idea on using Keychain but why don't you use KWallet?

---

### Post by Mortuis on 2007-11-12
You have any luck getting this to work?  I used to have it working on my server, but when I switched to a different machine (setting it up exactly as the other one was as best I could tell) it refuses to work!  It's aggravating! :-)


> **toucan said:**
> Hi,

I'm trying to get Keychain to work correctly under Kubuntu Feisty and I'm not having much success. I'm running:

```

steve@CARTMAN:~$ uname -a
Linux CARTMAN 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

```

and my *.bash_profile* looks like:



When I login to the desktop it then requests the password via an X ssh-askpass program but it seems to have no effect - if I then try to login to other systems I'm asked for the password again. If I run the *.bash_profile* script interactively everything is OK - it asks for the password and I can then login to other systems without further password requests as expected.

So it seems it's nearly working, but not quite.

Any ideas?

Steve

---

