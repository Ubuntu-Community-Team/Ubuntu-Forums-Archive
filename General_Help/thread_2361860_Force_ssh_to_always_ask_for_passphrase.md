---
title: "Force ssh to always ask for passphrase"
date: 2017-05-21
forum: General Help
---

### Post by ronnie.s on 2017-05-21
I have two laptops, one is to be the client, let's call it C and the other to be the host, let's call it H. On both machines I have the userid user@C and user@H. The laptop H uses the wireless network created on the laptop C, and so both are on the same LAN.

I downloaded and installed openssh-server on H, and set up H and C so that they use keys with passphrases. Suppose I switch on both the machines now and try to ssh from user@C to user@H, then I am asked for a passphrase. However, after exiting the connection, if I try connecting again, then I am not asked for a passphrase. Then for the laptop C to forget the passphrase I have to give the command 

```

ssh-add -D

```

or I have to log out from the account user@C and then login back again.

I want that I be prompted for a passphrase every time I try to ssh. I also want to avoid giving the command "ssh-add -D" every time I ssh. Is this possible by changing something in some config file somewhere?

---

### Post by TheFu on 2017-05-21
**AddKeysToAgent = confirm**
doesn't work? I didn't try it.

According to the manpage:
```
SSH_CONFIG(5)               BSD File Formats Manual              SSH_CONFIG(5)

NAME
     ssh_config — OpenSSH SSH client configuration files

SYNOPSIS
     ~/.ssh/config
     /etc/ssh/ssh_config

....
     AddKeysToAgent
             Specifies whether keys should be automatically added to a running
             ssh-agent(1).  If this option is set to “yes” and a key is loaded
             from a file, the key and its passphrase are added to the agent
             with the default lifetime, as if by ssh-add(1).  If this option
             is set to “ask”, ssh will require confirmation using the
             SSH_ASKPASS program before adding a key (see ssh-add(1) for
             details).  If this option is set to “confirm”, each use of the
             key must be confirmed, as if the -c option was specified to
             ssh-add(1).  If this option is set to “no”, no keys are added to
             the agent.  The argument must be “yes”, “confirm”, “ask”, or
             “no”.  The default is “no”.
...
FILES
     ~/.ssh/config
             This is the per-user configuration file.  The format of this file
             is described above.  This file is used by the SSH client.
             Because of the potential for abuse, this file must have strict
             permissions: read/write for the user, and not accessible by oth&#8208;
             ers.  It may be group-writable provided that the group in ques&#8208;
             tion contains only the user.

     /etc/ssh/ssh_config
             Systemwide configuration file.  This file provides defaults for
             those values that are not specified in the user's configuration
             file, and for those users who do not have a configuration file.
             This file must be world-readable.


```
The ssh set of manpages is really very good, BTW.

---

### Post by ronnie.s on 2017-05-22
I've been using linux for several years now. Perhaps, during my initial stages, when there weren't too many articles on the net, explaining with patience to novices, what is going on, I may have developed some fear for man pages, them being too technical. I think a hangover of that still remains, and I usually never bother to check man pages. Perhaps I should try to overcome this "assumption" that man pages will not be helpful. 

Thanks for your response, will check it out and see if things work.

---

### Post by ronnie.s on 2017-05-22
1. I created the file ~/.ssh/config

2. The only line in the above file reads 

```

AddKeysToAgent no

```

I tried with "no" replaced by all other options. None of them seemed to have the desired effect. After deleting all "identities" (the phrase used in the man page for ssh-add) using 

```

ssh-add -D

```

the first time I ssh, I am asked for the passphrase, but for subsequent attempts I am not asked for the passphrase.

---

### Post by TheFu on 2017-05-22
It was a best guess.  Moving on to the next guess ...  a little old, but if you use a GUI, might be the issue?
[http://dtek.net/2012/09/19/how-stop-gnome-keyring-clobbering-opensshs-ssh-agent-ubuntu-1204.html](http://dtek.net/2012/09/19/how-stop-gnome-keyring-clobbering-opensshs-ssh-agent-ubuntu-1204.html)
The file is  /etc/xdg/autostart/gnome-keyring-ssh.desktop
I don't use gnome, so the gnome-keyring doesn't happen here.

---

### Post by ronnie.s on 2017-05-22
The file you mention, /etc/xdg/autostart/gnome-keyring-ssh.desktop exists for me, but I'm not sure what I should do with it. The link that you gave explains how to get gnome-keyring in the list of applications which start on startup. However, this program is already visible there and it is not checked, in other words it does not start up on its own when I login. Perhaps, that is the reason that after I login, the first time I try to ssh, I am asked for my passphrase. 

I am guessing that when I run ssh, it runs the program gnome-keyring which in turn "saves" my passphrase for subsequent use until I logout. 

And I don't use GUI, all my attempts have been using the terminal. 

Any more guesses?

---

### Post by efflandt on 2017-05-24
I think you need a Host section in ~/.ssh./config, but you can use wildcard (*), so try:```
Host *
AddKeysToAgent no
```If you have settings for specific hosts you can insert those specific Host sections before that one and the wildcard section would still apply to all.

Also I believe files in ~/.ssh should only have read permission for you ( chmod 600 ~/.ssh/* ) otherwise some files might not be trusted by sshd (which will still be able to access the files). Or at least that is what I have always done after I had an issue with something not working.

---

