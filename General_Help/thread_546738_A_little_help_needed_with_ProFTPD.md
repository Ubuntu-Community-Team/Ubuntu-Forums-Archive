---
title: "A little help needed with ProFTPD"
date: 2007-09-09
forum: General Help
---

### Post by prodigal on 2007-09-09
Hi guys,

Well I'm having a bit of a problem with ProFTPD. Before I moved over to Ubuntu I was always more used to Gentoo and FC so the apt package manager is a new thing to me. As much as it really is great and a god send at times I've now come a cropper with it. I installed ProFTPD with it, it didn't work so I uninstalled it again and then re-installed it. This still didn't work so I decided to clean my system a little, I did 

```

apt-get remove proftpd
apt-get clean
apt-get update
apt-get upgrade

```

I also did 

```

whereis proftpd

```

and then manually deleted any files it found. Unfortunately now whenever I try to install Proftpd from the apt package manager it fails with 

```

proftpd is already the newest version.

```

If I then try to uninstall it with apt since there are no files on my system at the moment I get a fail with 

```

apt-get remove proftpd

invoke-rc.d: unknown initscript, /etc/init.d/proftpd not found.
dpkg: error processing proftpd (--remove) :
subprocess pre-removal script returned error exit status 100
Errors were encountered while processing:
proftpd
E: Sub-Process /usr/bin/dpkg returned an error code (1)

```

Now if I do a 

```

whereis proftpd

```

I get 

```

proftpd:

```

I'm a little confused to say the least although I assume that the package manager thinks it's still installed somewhere. Can anyone shed some light? Any and all help appreciated guys, thanks in advance.

---

### Post by TommyMann on 2007-09-10
sudo dpkg --remove --force-remove-reinstreq

that seems to help my lingering packages go away

---

### Post by prodigal on 2007-09-10
Thanks for the suggestion but unfortunately still getting

```

root@acs-ubuntu:/# dpkg --remove --force-remove-reinstreq proftpd
(Reading database ... 22436 files and directories currently installed.)
Removing proftpd ...
invoke-rc.d: unknown initscript, /etc/init.d/proftpd not found.
dpkg: error processing proftpd (--remove):
subprocess pre-removal script returned error exit status 100
Errors were encountered while processing:
proftpd

```

Anyone else got any clues? Could really do with not having to re-install this just to get rid of one rogue program. Got the server all setup and ready to install ispconfig except for proftpd and it's taken me about 2 days to get it setup to the point it's at now.

I really hope someone can help.

Thanks in advance

---

### Post by prodigal on 2007-09-11
Nobody got any ideas on this? Please don't make me format just for one program :confused:

---

### Post by dotCOM41799 on 2007-09-18
Anyone have an answer for this?  I'm having the same problem and have been searching the forums but all the "solutions" i've tried, still haven't worked :/


I upgraded to 7.04 from the Update Manager within Ubuntu ... it upgraded fine but now anytime I try to get proFTPd, I get the same type of errors.

---

### Post by cleishy on 2007-09-18
Hi,

don't know if this is much help.... tried for hours last night to install the same package and kept failing with dependency errors. Tried again this morning and everything worked fine, can only assume something has been fixed. 

cheers.

---

