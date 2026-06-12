---
title: "Problems with installing software"
date: 2013-09-20
forum: General Help
---

### Post by ElfenKiller on 2013-09-20
Somehow **apt-get **got some trouble. When trying to install specific software, I get this error:

Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created
or been moved out of Incoming. The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libpcl-1.7-all-dev : Depends: libpcl-apps-1.7-dev but it is not going to be installed
                      Depends: libpcl-io-1.7-dev but it is not going to be installed
                      Depends: libpcl-outofcore-1.7-dev but it is not going to be installed
                      Depends: libpcl-people-1.7-dev but it is not going to be installed
                      Depends: libpcl-recognition-1.7-dev but it is not going to be installed
                      Depends: libpcl-visualization-1.7-dev but it is not going to be installed

As far as I know all those dependencies are part of libpcl-1.7-all-dev. This error is also happening with other installations.

---

### Post by Bashing-om on 2013-09-20
ElfenKiller; (???)
What in the world are you trying to do that requires development packages ? That is a huge step above average usage !

Be aware " libpcl-1.7-all-dev" is not available within the 13.04 repository, where are you obtaining this source from ?
> 
sysop@1304mini:~$ apt-cache depends libpcl-1.7-all-dev 
E: No packages found
sysop@1304mini:~$ apt-cache search libpcl-1.7-all-dev 
sysop@1304mini:~$ 


This might be an ordeal ....

[INDENT][INDENT][INDENT]Boy, OH Boy
[/INDENT][/INDENT][/INDENT]

---

