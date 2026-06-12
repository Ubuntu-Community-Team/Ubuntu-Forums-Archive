---
title: "Can get KXDocker to work"
date: 2007-03-11
forum: General Help
---

### Post by mwob on 2007-03-11
Hi all!

I following this guide for installing KXdocker on dapper (it should also work on edgy)

[http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake](http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake)

I can compile the main KXdocker with no problems, but when I try to compile and then make any of the plugins, I get compile errors. Can anyone shed any light on what I need to do about this?

Here's a snippet from a failed compile:

xeplugin_configurator.cpp:277: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:278: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:279: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:280: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:286: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:290: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:293: error: invalid use of undefined type 'struct XSConfigurations'
xeplugin_configurator.h:114: error: forward declaration of 'struct XSConfigurations'
xeplugin_configurator.cpp:294: error: invalid use of undefined type 'struct XSConfigurations'

Also noticed a similar post with no resolution here:

[http://ubuntuforums.org/showthread.php?t=346604](http://ubuntuforums.org/showthread.php?t=346604)

Can anyone help me?

---

### Post by mwob on 2007-03-13
Anyone? Is KSDocker a banned subject? ;)

---

