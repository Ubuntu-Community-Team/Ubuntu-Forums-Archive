---
title: "non-empty ENV environment variable causing problems with ksh and bash --posix"
date: 2018-08-04
forum: General Help
---

### Post by jvdh on 2018-08-04
I login sporadically to a (l)ubuntu server currently running 18.04. at some point/update in the recent past (some months, at most) I started to note that my default shell (ksh) did no longer process the initialisation file (.kshrc) in my home directory.

I finally could identify the reason for this: during the login procedure ubuntu now defines and exports the ENV environment variable which has the value 

ENV=/usr/share/modules/init/profile.sh

(even for subshells...).

according to the ksh and bash manpages, this causes the shells *only* to process the file pointed to by $ENV and skip all other (notably user-specific) resource files *if* run in POSIX mode.

the difference between ksh and bash is,  that ksh is always running in posix mode and there is no way to change this behaviour that I know of.

bash o.t.o.h. by default still processes .bashrc and only stops doing this (due to the non-empty ENV variable) if run as "bash --posix". so the problem usually does not manifest itself for bash users....

I am aware that using bash as shell is the default and ksh might be considered esoteric, but it should be possible to use it as a login and interactive (sub)shell, which right now it is not (since all means of customization through .kshrc are lost: I have to explicitly source it in each and every newly opened shell right now due to the situation described above** .**..

questions:

1. is there a way for me (or the sysadmin) to configure the login process such that ENV is not used (remains undefined) in the first place?

2. in view of the documented consequences of defining ENV when running the shell in posix mode: is it really desirable that this approach is used in ubuntu in order to enforce processing of the stuff reached through /usr/share/modules/init/profile.sh?

---

### Post by steeldriver on 2018-08-04
The file you refer to appears to be part of the environment-modules package:

```

Description-en_CA: Modular system for handling environment variables
 The Modules package provides for the dynamic modification of a user's
 environment via modulefiles.  Each modulefile contains the information
 needed to configure the shell for an application. Once the Modules package
 is initialized, the environment can be modified dynamically on a per-
 module basis using the module command which interprets modulefiles.
 Typically modulefiles instruct the module command to alter or set shell
 environment variables such as PATH, MANPATH, etc. modulefiles may be
 shared by many users on a system and users may have their own collection
 to supplement or replace the shared modulefiles.  The modules environment
 is common on SGI/Crays and many workstation farms.

```

I don't think it's installed by default so presumably it is something that the system administrator has added?

---

### Post by jvdh on 2018-08-04
> **steeldriver said:**
> The file you refer to appears to be part of the environment-modules package:

```

Description-en_CA: Modular system for handling environment variables
 The Modules package provides for the dynamic modification of a user's
 environment via modulefiles.  Each modulefile contains the information
 needed to configure the shell for an application. Once the Modules package
 is initialized, the environment can be modified dynamically on a per-
 module basis using the module command which interprets modulefiles.
 Typically modulefiles instruct the module command to alter or set shell
 environment variables such as PATH, MANPATH, etc. modulefiles may be
 shared by many users on a system and users may have their own collection
 to supplement or replace the shared modulefiles.  The modules environment
 is common on SGI/Crays and many workstation farms.

```

I don't think it's installed by default so presumably it is something that the system administrator has added?

ok... I see. thanks a lot for this hint. I will talk to the admin about this again (I asked him already but he wasn't aware of explicitly activating anything new recently...).

still, the main observation, it seems, is the fact that while bash users never will notice anything special (presuming they don't use `bash -- posix') even if this modular system is active since their .bashrc is processed just fine, it really interferes massively with ksh which insists on POSIX compliance regarding handling of ENV. I wonder whether this does not qualify as a "bug": it seems the difference in default behaviour between ksh and bash should be dealt with adequately...

---

