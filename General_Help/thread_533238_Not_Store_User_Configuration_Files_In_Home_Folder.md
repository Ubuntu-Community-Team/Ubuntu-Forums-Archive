---
title: "Not Store User Configuration Files In Home Folder"
date: 2007-08-23
forum: General Help
---

### Post by mikaelsnavy on 2007-08-23
Is there a way to only use the home folder to store documents and files and to move all the configuration to some other folder than the home folder? I am trying to help setup a linux lab in a local school. They want to have the home folder to have all the files they made on a windows machine there.
Thanks,
Mikael

---

### Post by dougfractal on 2007-08-23
Am I right in thinking that you a using a samba share, I think you can hide all the . (hidden file with smb.conf.   

If you're not using home as a linux folder you could just delete all the hidden files. Or just create a share folder in the home dir.

---

### Post by mikaelsnavy on 2007-08-23
The problem I am having is the permissions on the NTFS drives, I get lots of login errors. I am currently trying to convince the tech I am help to let me remove the home folder Icon and replace it with a mounted folder with the same name. I am using a 2k3 active directory and domain (I got them to work together), is there a way to make it create a users folder and then auto-mount it when they login?

---

### Post by dougfractal on 2007-08-23
I'm sorry I have'nt used samba for a long time. And I might not be able to help.

So you have 2K3 server with NTFS partiions and you want to host a linux filesytem the the server, with linux file permisions going to a linux box on the network.

My hack way would be to have a linux file (2GB say) like in WUBI which behaves like a partition.

---

### Post by mikaelsnavy on 2007-08-23
hmm, the problem is the users also login into windows machines all over the network and they need their "My Documents" folder. But if I have the home directory mounted, them  I get "User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HoME/.drmc file must be owned by user and not writable to others"

---

### Post by dougfractal on 2007-08-23
from this google seach
[http://search.techrepublic.com.com/search/Microsoft+Windows+Active+Directory+and+samba.html](http://search.techrepublic.com.com/search/Microsoft+Windows+Active+Directory+and+samba.html)

Can Linux Desktops Live in an Active Directory World?[http://reverendted.wordpress.com/2006/09/12/linux-goes-mad/](http://reverendted.wordpress.com/2006/09/12/linux-goes-mad/)

using Suse Linux Enterprise Desktop.

 Is this sort of thing that you are after?

Is this any good?
[http://ubuntuforums.org/archive/index.php/t-5409.html](http://ubuntuforums.org/archive/index.php/t-5409.html)
HOWTO: NT Domain Authentication

[http://swik.net/domain+Ubuntu](http://swik.net/domain+Ubuntu)

---

### Post by mikaelsnavy on 2007-08-24
hmm, I got them to join the active directory. I have a new idea though, if I can find a sync tool or a sync script, I can just do that instead of all the mounting. It will save tons of problems!

---

### Post by eentonig on 2007-08-24
Whu don't you mount "My Documents" like this "/home/<username>/<My Documents>" and then create the required  "My Documents" links?

(Actually, Windows also places the "My documents" below a username-folder).

---

### Post by mikaelsnavy on 2007-08-26
I would, but the IT guys will not stop short of having it in the home folder. I am trying to do a sync script or mount the drive after login.

---

