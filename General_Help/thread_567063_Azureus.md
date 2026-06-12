---
title: "Azureus"
date: 2007-10-04
forum: General Help
---

### Post by liquidfunk on 2007-10-04
Azureus opens, then closes shortly after? 

 I've tried removing, reinstalling all that. 

 Here is the output from a Terminal - > liquidfunk@liquidfunk-desktop:~$ azureus
DEBUG::Thu Oct 04 12:49:15 GMT+01:00 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,ConfigurationChecker::setSystemProperties::145,ConfigurationManager::initialise::138,ConfigurationManager::getInstance::71,LoggerImpl::init::90,Logger::<clinit>::48,Class::initializeClass::-1,StartServer::<init>::70,Main::<init>::56,Main::main::162
DEBUG::Thu Oct 04 12:49:15 GMT+01:00 2007::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::140:
  No SSL provider available
    SESecurityManager::initialise::52,CryptoManagerImpl::<init>::73,CryptoManagerImpl::getSingleton::60,CryptoManagerFactory::getSingleton::33,AzureusCoreImpl::<init>::155,AzureusCoreImpl::create::92,AzureusCoreFactory::create::46,Main::<init>::143,Main::main::162
Aborted (core dumped)


 Using the Gutsy Beta.

---

### Post by jarocooke on 2007-10-05
Same here!!!

I am also using Gutsy Beta (64bit version).  Right after Azureus (Vuze) starts, it crashes.

Anyone have any idea how to work round this (or even what is causing the problem)?

---

### Post by liquidfunk on 2007-10-05
Tis weird, it worked to begin with? 

 Interesting how it is in the Repo's but it doesn't work.

 hmmmm.. nice.

---

### Post by Dropknee on 2007-10-05
just delete in .azureus the log folder, this is just a temporary solucion, and do know the permanent fix to this, sorry.

---

### Post by eternalperson on 2007-10-05
Azureus is extremely buggy on Linux at the moment.  Use "Deluge". It's much better and is a Linux-Native bittorrent application. Get it at: [http://deluge-torrent.org]("http://deluge-torrent.org")

---

