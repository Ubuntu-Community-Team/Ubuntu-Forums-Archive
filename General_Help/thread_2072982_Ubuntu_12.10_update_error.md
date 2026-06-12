---
title: "Ubuntu 12.10 update error"
date: 2012-10-18
forum: General Help
---

### Post by Hungry Man on 2012-10-18
I installed 12.10 and restarted. I tried running apt-get update and apt-get upgrade

```
Setting up libgtk2.0-cil (2.12.10-4) ...
W: removing assembly:  failed!

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly '/usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.gtk-dotnet.dll' or one of its dependencies. The system cannot find the file specified.
File name: '/usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.gtk-dotnet.dll'
  at (wrapper managed-to-native) System.Reflection.Assembly:LoadFrom (string,bool)
  at System.Reflection.Assembly.LoadFrom (System.String assemblyFile, System.Security.Policy.Evidence securityEvidence) [0x00000] in <filename unknown>:0 
  at System.Reflection.Assembly.LoadFile (System.String path, System.Security.Policy.Evidence securityEvidence) [0x00000] in <filename unknown>:0 
  at System.Reflection.Assembly.LoadFile (System.String path) [0x00000] in <filename unknown>:0 
  at GetAssemblyName.Main (System.String[] args) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.IO.FileNotFoundException: Could not load file or assembly '/usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.gtk-dotnet.dll' or one of its dependencies. The system cannot find the file specified.
File name: '/usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.gtk-dotnet.dll'
  at (wrapper managed-to-native) System.Reflection.Assembly:LoadFrom (string,bool)
  at System.Reflection.Assembly.LoadFrom (System.String assemblyFile, System.Security.Policy.Evidence securityEvidence) [0x00000] in <filename unknown>:0 
  at System.Reflection.Assembly.LoadFile (System.String path, System.Security.Policy.Evidence securityEvidence) [0x00000] in <filename unknown>:0 
  at System.Reflection.Assembly.LoadFile (System.String path) [0x00000] in <filename unknown>:0 
  at GetAssemblyName.Main (System.String[] args) [0x00000] in <filename unknown>:0 
Use of uninitialized value $_ in scalar chomp at /usr/share/cli-common/runtimes.d/mono line 141.
Use of uninitialized value $fullname in concatenation (.) or string at /usr/share/cli-common/runtimes.d/mono line 110.
E: installing Assembly /usr/share/cli-common/policies.d/libgtk2.0-cil/policy.2.6.gtk-dotnet.dll failed
E: Installation of policy.2.6.gtk-dotnet with /usr/share/cli-common/runtimes.d/mono failed
dpkg: error processing libgtk2.0-cil (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libappindicator0.1-cil:
 libappindicator0.1-cil depends on libgtk2.0-cil (>= 2.12.10-1ubuntu1); however:
  Package libgtk2.0-cil is not configured yet.

dpkg: error processing libappindicator0.1-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgtk-sharp-beans-cil:
 libgtk-sharp-beans-cil depends on libgtk2.0-cil (>= 2.12.10-1ubuntu1); however:
  Package libgtk2.0-cil is not configured yet.

dpkg: error processing libgtk-sharp-beans-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblaunchpad-integration1.0-cil:
 liblaunchpad-integration1.0-cil depends on libgtk2.0-cil (>= 2.12.10-1ubuntu1); however:
  Package libgtk2.0-cil is not configured yet.

dpkg: error processing liblaunchpad-integration1.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnotify0.4-cil:
 libnotify0.4-cil depends on libgtk2.0-cil (>= 2.12.10-1ubuntu1); however:
  Package libgtk2.0-cil is not configured yet.No apport report written because MaxReports is reached already
                                                                                                            No apport report written because MaxReports is reached already


dpkg: error processing libnotify0.4-cil (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libgtk2.0-cil
 libappindicator0.1-cil
 libgtk-sharp-beans-cil
 liblaunchpad-integration1.0-cil
 libnotify0.4-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I can't remove package because of this.


edit: ok so I managed to remove libnotify0.4-cil and now when I do update I get to  "reading package lists... done" and it just stays there.

---

### Post by oldos2er on 2012-10-18
Did you upgrade from a previous Ubuntu version, or run a fresh install? Can you post your sources.list? ```
cat /etc/apt/sources.list
```

---

### Post by Hungry Man on 2012-10-18
Upgrade from 12.04.

>  cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Beta amd64 (20110901)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Beta amd64 (20110901)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-proposed restricted main multiverse universe


---

### Post by Hungry Man on 2012-10-18
Ok... it may be working now. I'll give it a few minute sbefore I mark this solved.

---

### Post by oldos2er on 2012-10-19
If you mark it as solved, please post the solution to help others who may have the same problem.

---

