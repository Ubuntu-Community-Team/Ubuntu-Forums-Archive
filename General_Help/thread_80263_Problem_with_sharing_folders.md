---
title: "Problem with sharing folders"
date: 2005-10-21
forum: General Help
---

### Post by evil-boweevil on 2005-10-21
I'm new to ubuntu and just tried to set up networking.  I used the Shared Folders program to set up samba shares at first.  It seemed to work, then I decided they should be NFS shares and installed the NFS kernel server through synaptic.  I then went back to the Shared Folders application and switched the shares to NFS.  That doesn't seem to have worked and now I can't use the Shared Folders application anymore.  It just hangs once it has been opened.

Here is the output if I run it from the terminal:

```
eolson@evil-boweevil:~$ gksudo shares-admin

(shares-admin:9091): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
*** glibc detected *** double free or corruption (fasttop): 0x08244f68 ***
```

I've tried uninstalling SAMBA and NFS but nothing bings the program back.  Is there a way I can try to reinstall this program and start from a fresh slate?  Can't find it in synaptic.  Thanks.

---

### Post by evil-boweevil on 2005-10-22
I fixed it by deleting the entries for the shares in the nfs config file.  I don't know why that would cause that.

So I switched back to samba, but unfortunately there is a bug with Ubuntu's older samba version 3.0.14a.  When I try to connect with my mac there is some sort of problem with the rpc_bin server code and it will not connect.  This is supposedly fixed in version 3.0.20.  Does anybody have any idea when or if Ubuntu will update samba?  Is there a way to install the latest version from a debian repository?

---

### Post by garretjax on 2005-10-22
I don't know about a debian repository, but as a former slacker i can tell you that you could install samba from the source files, or likely there is a tar package wiht an installer off one of sambas mirror sites. ditch it through synaptic.  However, this way will require that you manually keep it up to date, and you may not be able to use all the gui tools for setting up shares etc [Not that this is something that should bother you. usually the gui stuff puts in a lot more trash into the config files that is strictly necessary]


GJ

---

### Post by evil-boweevil on 2005-10-22
Thanks, I was able to just add the debian unstable repository and install all the new samba stuff.  Now running at 3.0.20 and able to share files with my mac.   :p

---

