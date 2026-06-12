---
title: "Stop Nvidia drivers from &quot;upgrading&quot;"
date: 2006-11-08
forum: General Help
---

### Post by drewtown on 2006-11-08
Is there anyway to stop auto updates from finding the Nvidia drivers and wanting to downgrade my beta drivers to the correct packaged drivers?  I installed beryl and had to upgrade the Nvidia drivers and I don't see anyway from stopping apt from trying to downgrade my drivers besides ignoring the updates.

---

### Post by dannyboy79 on 2006-11-08
there's a way to lock it through aptitude, did you do man apt-get or man aptitude?

---

### Post by dannyboy79 on 2006-11-08
according to man aptitude: remove, purge, hold, keep, reinstall
These  commands  are  the  same as ââinstallââ, but apply the named action to all packages given on the command line for which it is not
              overridden. The difference between hold and keep is that hold will cause a package to be ignored by future upgrade commands, while  keep
              merely cancels any scheduled actions on the package.

              For instance, ââaptitude remove â~ndeityâââ will remove all packages whose name contains ââdeityââ.
 

and then according to man apt-get
OPTIONS
       All command line options may be set using the configuration file, the descriptions indicate the configuration option to set.  For  boolean  opâ
       tions you can override the config file by using something like -f-,--no-f, -f=no or several other variations.

 --no-upgrade
Do not upgrade packages; When used in conjunction with install, no-upgrade will prevent packages on the command line from being upgraded
              if they are already installed. Configuration Item: APT::Get::Upgrade.

---

### Post by drewtown on 2006-11-08
Thanks a lot.

I'm on my laptop right now (doing laundry) but I'll let you know how it goes when I get a chance to run it thorugh.

---

