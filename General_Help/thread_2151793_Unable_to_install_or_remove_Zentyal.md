---
title: "Unable to install or remove Zentyal"
date: 2013-06-05
forum: General Help
---

### Post by andrewgerm on 2013-06-05
Good evening all

I have been receiving a lot of great advice from this forum, and need to ask yet another question.
At least the server is beginning to work great.

I have been trying to install Zentyal on Ubuntu Server 13.04.
The initial install of zentyal-core and zentyal-common seemed to go well, but I started noticing errors when installing additional modules.

What I think happened (but can't be too sure) is that the initial common and core installs missed some dependencies.
When I try reinstall or remove Zentyal now, I get the following.

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
zentyal-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up samba4 (4.0.0+dfsg1-1ubuntu1) ...
ERROR(<class 'samba.provision.ProvisioningError'>): Provision failed - ProvisioningError: guess_names: Workgroup 'HOME-LAN' in smb.conf must match chosen domain 'WORKGROUP'!  Please remove the /etc/samba/smb.conf file and let provision generate it
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/domain.py", line 398, in run
    use_rfc2307=use_rfc2307, skip_sysvolacl=False)
  File "/usr/lib/python2.7/dist-packages/samba/provision/__init__.py", line 1892, in provision
    sitename=sitename, rootdn=rootdn)
  File "/usr/lib/python2.7/dist-packages/samba/provision/__init__.py", line 548, in guess_names
    raise ProvisioningError("guess_names: Workgroup '%s' in smb.conf must match chosen domain '%s'!  Please remove the %s file and let provision generate it" % (lp.get("workgroup").upper(), domain, lp.configfile))
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 255
Setting up zentyal-core (2.3.21+quantal1) ...
Could not open the config file /etc/zentyal/core.conf.dpkg: error processing zentyal-core (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 samba4
 zentyal-core
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any tips, advice or assistance would be greatly appreciated.
I have searched all over for a solution to this, but yet again have come up empty.

Zentyal looks like a great way to remotely administer the server (from other areas in the building).

Thank you in advance.

---

### Post by Cheesemill on 2013-06-06
Zentyal is designed and written to be used with Ubuntu Server 12.04, I don't think you'll be able to get it to work on any other version of Ubuntu.

---

### Post by andrewgerm on 2013-06-06
Cheesemill
Thank you again for all your responses.
I eventually installed 13.04, as 12.04 would not install on the new system I had (hanging half way through the install).

I was able to install Zentyal from the repository. But any sort of GUI interface (similar to webmin) would be fine.
Although, from browsing this forum, I've learnt to do a ton of things just from the command line.

Thanks again :)

---

