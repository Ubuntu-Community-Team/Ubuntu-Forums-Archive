---
title: "'Open in terminal' not working in smb:// nautilus folders"
date: 2024-03-12
forum: General Help
---

### Post by cjbo on 2024-03-12
Hello all,

The contextual menu inside a folder in nautilus allowed me to 'open in terminal' any location, local or remote.
As the title says, this feature was working until a few days ago. Now, this option isn't available in network folders, only on local folders.
My version is 22.04.4
Maybe related, another program that was working a few days ago but it doesn't anymore is 'flameshot'. Now I get :

"Warning: Ignoring XDG_SESSION_TYPE=wayland on Gnome. Use QT_QPA_PLATFORM=wayland to run on Wayland anyway."

What can I try?

Thanks for any help,
Carlos

---

### Post by TheFu on 2024-03-12
Actually mount the CIFS storage to a directory first?  Then try to "open a terminal here" .
I can't test it. Don't use CIFS stuff myself. We're all NFS here.

---

### Post by cjbo on 2024-03-14
Thanks for your suggestion!.

I solved it by doing: sudo apt install --reinstall ubuntu-desktop

---

