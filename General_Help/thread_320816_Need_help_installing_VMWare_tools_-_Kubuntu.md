---
title: "Need help installing VMWare tools - Kubuntu"
date: 2006-12-17
forum: General Help
---

### Post by Ub3r-L33ch on 2006-12-17
So I installed VM Workstation 5.5.3, got Kubuntu 6.06 installed and now I'm trying to install VMWare tools via an RPM because its supposed to make the interface and everything more smooth or whatever.

I got alien installed but when I try this command;
sudo alien -i <RPM Name>
I get this:
Warning: Skipping conversion of scripts in package VMwareTools: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
mkdir: cannot create directory `VMwareTools-5.5.3': Read-only file system
chmod: cannot access `VMwareTools-5.5.3': No such file or directory
sh: line 0: cd: VMwareTools-5.5.3: No such file or directory
mkdir: cannot create directory `VMwareTools-5.5.3/debian': No such file or directory
VMwareTools-5.5.3/debian/changelog: No such file or directory at /usr/share/perl5/Alien/Package/Deb.pm line 330, <GETPERMS> line 3686.
find: VMwareTools-5.5.3: No such file or directory

Now what?

---

### Post by LaLLi on 2006-12-19
Have you tried using the tar.gz installer? I'd recommend installing sofware from source instead of converting rpm->deb and then installing.
[http://www.vmware.com/support/ws5/doc/ws_newguest_tools_linux.html](http://www.vmware.com/support/ws5/doc/ws_newguest_tools_linux.html)

---

