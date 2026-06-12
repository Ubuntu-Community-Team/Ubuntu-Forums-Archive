---
title: "Access openvpn file over samba"
date: 2019-10-10
forum: General Help
---

### Post by maxfrai on 2019-10-10
Hello, I have two ubuntu notebooks in one local network. One of them shares folder with ovpn file. On second I want to run openvpn with ovpn file from network.
So I found shared folder in nautilus and mounted it. The mounted path is something like: `/run/user/1000/gvfs/smb-share:server=name,share=folder/`.
When I try to edit ovpn file with vim, for example, it works okay, but when I run openvpn with config parameter from mounted folder, I see error:
Error opening configuration file: path/to/file.ovpn

---

### Post by TheFu on 2019-10-10
I don't know, but a GVFS mount isn't a real mount, like what the fstab or mount command would provide.  I'd try switching to a non-GVFS method of access.

---

