---
title: "dpkg: error processing samba (--configure) AND mf: error while loading shared lib..."
date: 2006-08-27
forum: General Help
---

### Post by DROP on 2006-08-27
A few days ago I was installing tetex-bin and it's related packages, and the system crashed in the middle of the install. I had to do a "clear available" since that file was corrputed. I am now running into a new set of problems. When I try to install anything I get something similar to the following:

**terminal output:**
```
ian@ionlinux:/etc$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  smbldap-tools
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/2845kB of archives.
After unpacking 7250kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 27684 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.22-1ubuntu3.1_i386.deb) ...
Setting up tetex-bin (3.0-13ubuntu6) ...
Running fmtutil-sys. This may take some time. ...
mf: error while loading shared libraries: /usr/lib/libX11.so.6: invalid ELF header
Error: `mf -ini  -jobname=mf -progname=mf -translate-file=cp227.tcx mf.ini' failed

###############################################################################
fmtutil: Error! Not all formats have been built successfully.
Visit the log files in directory
  /var/lib/texmf/web2c
for details.
###############################################################################

This is a summary of all `failed' messages and warnings:
`mf -ini  -jobname=mf -progname=mf -translate-file=cp227.tcx mf.ini' failed

fmtutil failed. Output has been stored in
/tmp/tetex.postinst.XXUTxvt7
Please include this file if you report a bug.
dpkg: error processing tetex-bin (--configure):
 subprocess post-installation script returned error exit status 1
Setting up samba (3.0.22-1ubuntu3.1) ...
Generating /etc/default/samba...
 * Starting Samba daemons...                                                                 [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 tetex-bin
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by DROP on 2006-08-27
I've narrowed the error down to Samba now:
```
Reading package lists... Done
Building dependency tree... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up samba (3.0.22-1ubuntu3.1) ...
 * Starting Samba daemons...                                                                 [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Wallythander on 2006-08-28
I am having a very similar problem, and no one has answered my Thread yet.  Good thing I am not the only person with this problem.

---

### Post by saphil on 2006-10-05
This is a dependency problem.  **aptitude dist-upgrade** can often get the dependencies sorted out.  Aptitude is a apt front-end that offers solutions to dependency problems.  Have you tried removing the offending packages entirely and then reinstalling them?

---

### Post by rfdeshon on 2007-03-11
I am getting this same problem. It is nto a dep problem (aptitude dist-upgrade tells me I am fully up to date) also, I have tried a number of other solutions from the forums and none have worked. This is getting on my nerves.

---

### Post by juleshernandez on 2007-03-14
Good day!

I'm getting this same message. I was experimenting connecting my Edgy to my WinXP PC, and somehow removed Samba in the process. When I tried to install it again, I get this same error. I googled and saw a potential answer to my problem in [https://answers.launchpad.net/ubuntu/+ticket/3583]("http://https://answers.launchpad.net/ubuntu/+ticket/3583/"). However, it did not work for me. I still get the same error. Somebody, pls. help.

For those with the same problem, you might want to try the solution in the above link.

TIA

---

