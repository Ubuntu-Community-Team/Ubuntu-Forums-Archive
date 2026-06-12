---
title: "Cannot get any more packages due to Apache Module errors"
date: 2005-04-23
forum: General Help
---

### Post by tommy04 on 2005-04-23
Okay, so I'm trying to uninstall some apache modules. However, here's the problem:

> 
Removing libapache-mod-mono ...
dpkg: error processing libapache-mod-mono (--remove):
 subprocess pre-removal script returned error exit status 1
Removing libapache-mod-jk ...
dpkg: error processing libapache-mod-jk (--remove):
 subprocess pre-removal script returned error exit status 1
Removing libapache-mod-encoding ...
dpkg: error processing libapache-mod-encoding (--remove):
 subprocess pre-removal script returned error exit status 1
Removing libapache-mod-auth-kerb ...
dpkg: error processing libapache-mod-auth-kerb (--remove):
 subprocess pre-removal script returned error exit status 1
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Removing libapache-mod-auth-pam ...
dpkg: error processing libapache-mod-auth-pam (--remove):
 subprocess pre-removal script returned error exit status 1
Removing libapache-mod-auth-pgsql ...
dpkg: error processing libapache-mod-auth-pgsql (--remove):
 subprocess pre-removal script returned error exit status 1
Removing libapache-mod-auth-radius ...
dpkg: error processing libapache-mod-auth-radius (--remove):
 subprocess pre-removal script returned error exit status 1
Removing libapache-mod-auth-shadow ...
dpkg: error processing libapache-mod-auth-shadow (--remove):
 subprocess pre-removal script returned error exit status 1
Removing libapache-mod-gzip ...
dpkg: error processing libapache-mod-gzip (--remove):
 subprocess pre-removal script returned error exit status 1
Removing libapache-mod-iptos ...
dpkg: error processing libapache-mod-iptos (--remove):
 subprocess pre-removal script returned error exit status 1
Removing libapache-mod-php4 ...
dpkg: error processing libapache-mod-php4 (--remove):
 subprocess pre-removal script returned error exit status 1
Removing libapache-mod-witch ...
sed: -e expression #1, char 35: invalid reference \1 on `s' command's RHS
dpkg: error processing libapache-mod-witch (--remove):
 subprocess post-removal script returned error exit status 1
Removing apache2 ...
Removing apache2-mpm-worker ...
 * Stopping web server (Apache2)...                                      [ ok ]
Removing apache2-common ...
dpkg: mono-apache-server: dependency problems, but removing anyway as you request:
 libapache-mod-mono depends on mono-apache-server (>= 0.15); however:
  Package mono-apache-server is to be removed.
Removing mono-apache-server ...
dpkg: apache: dependency problems, but removing anyway as you request:
 libapache-mod-encoding depends on apache | apache-ssl | apache-perl; however:
  Package apache is to be removed.
  Package apache-ssl is not installed.
  Package apache-perl is not installed.
 libapache-mod-jk depends on apache | apache-perl | apache-ssl; however:
  Package apache is to be removed.
  Package apache-perl is not installed.
  Package apache-ssl is not installed.
 libapache-mod-mono depends on apache (>= 1.3.31).
Removing apache ...
Stopping web server: apache.
dpkg: apache-common: dependency problems, but removing anyway as you request:
 libapache-mod-encoding depends on apache-common (>= 1.3.28-1); however:
  Package apache-common is to be removed.
 libapache-mod-jk depends on apache-common (>= 1.3.29.0.1).
Removing apache-common ...
Removing apache2-utils ...
Errors were encountered while processing:
 libapache-mod-mono
 libapache-mod-jk
 libapache-mod-encoding
 libapache-mod-auth-kerb
 libapache-mod-auth-pam
 libapache-mod-auth-pgsql
 libapache-mod-auth-radius
 libapache-mod-auth-shadow
 libapache-mod-gzip
 libapache-mod-iptos
 libapache-mod-php4
 libapache-mod-witch
E: Sub-process /usr/bin/dpkg returned an error code (1)


I cannot get any new packages due to both Apt-Get and Synaptic wanting me to remove these. Any help?

---

### Post by tommy04 on 2005-04-23
Still need help... sorry for the bump, but it's kind of important, as Alt-Tab switching in openbox gets old and I can't install fspanel...

---

### Post by tommy04 on 2005-04-24
[QUOTE=tommy04]Still need help... sorry for the bump, but it's kind of important, as Alt-Tab switching in openbox gets old and I can't install fspanel...[/QUOTE]
 Still no luck ;_;

Can anyone help? I don't want to have to change distros...

---

### Post by DJ_Max on 2005-04-24
Have you tried:
sudo apt-get -f install

---

### Post by tommy04 on 2005-04-24
[QUOTE=DJ_Max]Have you tried:
sudo apt-get -f install[/QUOTE]
 Yep. Gives the same errors.

---

### Post by XDevHald on 2005-04-24
To get certain packages removed by name type as root:
 
 **apt-get remove "package name"**
 
 and to remove files that the package installed along with it would be:
 
 [b]apt-get --purge remove "package name"

[/b]Also see :[http://lists.debian.org/debian-user/2004/04/msg11344.html](http://lists.debian.org/debian-user/2004/04/msg11344.html)

---

### Post by tommy04 on 2005-04-24
[QUOTE=Doc]To get certain packages removed by name type as root:
 
 **apt-get remove "package name"**
 
 and to remove files that the package installed along with it would be:
 
 [b]apt-get --purge remove "package name"

[/b]Also see :[http://lists.debian.org/debian-user/2004/04/msg11344.html](http://lists.debian.org/debian-user/2004/04/msg11344.html)[/QUOTE]

Okay, I don't care about changing what I use. Those two give me the same error I've been having.

---

### Post by tommy04 on 2005-04-24
*Sigh*

Still not working... if I just delete this stuff is there a way to reset the package list so it doesn't say that it can't delete and stop working? Geez this is stupid...

---

### Post by tommy04 on 2005-04-25
-_-

What is this, triple-post?

bump once more.

---

### Post by tommy04 on 2005-04-25
*May switch distros because of how unhelpful this community is*

---

### Post by dude2425 on 2005-04-25
I'm having the exact same problem. Those particular packages just wont uninstall, or even reinstall. If you ask me, these things should be fixed in the repo's so that they can install and uninstall correctly. I'm thinking of reinstalling Hoary, but I'm gonna wait till I get my CD's in the mail first, just because I don't feel like burning them myself.

---

### Post by az on 2005-04-25
[QUOTE=tommy04]*May switch distros because of how unhelpful this community is*[/QUOTE]

You have mixed apache and apche2 packages.  That is what happends when you use universe packages and do not know what you are doing.  You were suggested to remove the offending packages.  You can try synaptic, you can try the commandline.  Remove anything that says apache.  After that, do an apt-get -f install.

If you want the community to be helpful, help yourself and try to gather as much information as possible before bumping you post.  Give the community something to work with.

Come back if you have further questions.  Somebody will be happy to answer you if you are patient.  If you bump you rposts impatiently and are annoying, goodbye,

Also, why not mention what repositories you have enabled.

---

### Post by tommy04 on 2005-04-25
[QUOTE=azz]You have mixed apache and apche2 packages.  That is what happends when you use universe packages and do not know what you are doing.  You were suggested to remove the offending packages.  You can try synaptic, you can try the commandline.  Remove anything that says apache.  After that, do an apt-get -f install.

If you want the community to be helpful, help yourself and try to gather as much information as possible before bumping you post.  Give the community something to work with.

Come back if you have further questions.  Somebody will be happy to answer you if you are patient.  If you bump you rposts impatiently and are annoying, goodbye,

Also, why not mention what repositories you have enabled.[/QUOTE]

Yeah, my posts were going to be seen on page 70 kajillion. Of course I was going to bump it.

The point is I already tried removing, already tried synaptic, already tried everything I could. Nothing worked. I gave you all the information I had.

---

### Post by tommy04 on 2005-04-26
*Sigh*

Bumped once more. Okay, so I did something wrong, so how do I fix it?

---

