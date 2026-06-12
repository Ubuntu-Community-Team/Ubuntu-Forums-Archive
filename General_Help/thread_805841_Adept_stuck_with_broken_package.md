---
title: "Adept stuck with broken package"
date: 2008-05-24
forum: General Help
---

### Post by Zoso183 on 2008-05-24
I'm having an issue uninstalling cdemu and adept can't seem to get around it.

Removing cdemu-daemon ...
 * Stopping CDEmu userspace daemon                                               * Stopping cdemud daemon...                                             [ OK ]
 * Removing kernel module (vhba)...                                      [fail]
                                                                         [fail]
invoke-rc.d: initscript cdemu-daemon, action "stop" failed.
dpkg: error processing cdemu-daemon (--remove):
 subprocess pre-removal script returned error exit status 1
 * Starting CDEmu userspace daemon                                               * Inserting kernel module (vhba)...                                     [fail]
                                                                         [fail]
invoke-rc.d: initscript cdemu-daemon, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cdemu-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

And now adept is useless since it can't ignore the broken package.  Any ideas?

---

### Post by Zoso183 on 2008-05-25
I was able to work around the problem by editing /var/lib/dpkg/status and removing the entry for cdemu.  As far as adept is concerned, the package is not installed and does not exist.  For some reason cdemu is not showing up in the list which it used to, maybe a release is not available for hardy.  If anyone has a solution to truly fix this, I would like to know!

---

### Post by tosoth on 2008-05-27
Hello.
After today ubuntu updates cdemu stopped to work, so i tried to uninstall it and I stuck with the same problem you had. I used your method to get rid of error message, thnx :).
You are right that there's no hardy packages right now, I think they were deleted and I hope there soon will be new ones.
[https://launchpad.net/cdemu/trunk/](https://launchpad.net/cdemu/trunk/)

I got peek of new cdemu svg pixmap :), Maybe it's not beautiful but at least it will be scalable now :P.

---

