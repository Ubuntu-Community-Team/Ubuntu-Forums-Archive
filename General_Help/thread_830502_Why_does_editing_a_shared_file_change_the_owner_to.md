---
title: "Why does editing a shared file change the owner to &quot;nobody&quot;?"
date: 2008-06-15
forum: General Help
---

### Post by ddixonr on 2008-06-15
Why does editing a shared file change the owner to "nobody"?

Details:

1. I created html files on my web server (desktop).
2. Rather than spend all my time confined to the desktop, I opted to share the necessary files/folders so that I can work from the laptop throughout the house.
3. After editing each file from the shared www folder, the files & folders appear with locks (looking at them from the desktop). The owner says "nobody."

Now, I can ONLY edit those locked files from the laptop. I know that I can change the owner with the chown command, but I'd have to do it after every edit (which can be several times a day).

---

### Post by HalPomeranz on 2008-06-15
Sounds like you're sharing the files via NFS.  The default behavior for NFS is to map root to nobody when you're accessing files as root from the client machines.  You can turn off this behavior with the no_root_squash option in /etc/exports.

---

### Post by ddixonr on 2008-06-15
Here is the export file you referred to:

# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#

Where/How do I add this option?

---

### Post by HalPomeranz on 2008-06-15
Hmmm, is that the entirety of your /etc/exports file?  Because it doesn't look like there are any shared file systems configured there.  

If you run "sudo exportfs" what output (if any) do you get?  This command should display information about any currently exported file systems.

---

### Post by ddixonr on 2008-06-15
No output, no error messages, just nothing.

---

### Post by HalPomeranz on 2008-06-15
Odd.  So how exactly did you configure sharing on this directory?  I must be mistaken in my original assumption that you were using NFS.

---

### Post by ddixonr on 2008-06-15
All I did was right-click on the folder then sharing options. Checked the boxes and that was it. Both computers are on the same network with the same workgroup so it wasn't hard. I guess this is the price I pay for thinking it was too easy.

---

### Post by ddixonr on 2008-06-15
I found another way to get the job done- by using ssh. I can connect to the web server and login using the username I want. What are the benefits and drawbacks to doing it this way?

BTW, thanks for the help so far. The people over in Networking category didn't help very much.

---

### Post by HalPomeranz on 2008-06-15
I guess I don't use the GUI sharing stuff enough to know what's happening there.  Looks like Windows SMB type sharing.  I'm thinking that if you unclicked the "Guest user access" box then the server would force you to log in as a valid user and thus the files would end up getting written with that user's privileges rather than as "nobody".

Anyway, using SSH for access is probably better anyway.  Aside from forcing you to actually log in, SSH encrypts all data between client and server and so is generally more secure.  If you're going to stick with SSH then I recommend you go back to the sharing menu and turn off the other kind of sharing (you don't need to have this enabled if you're just using SSH for access).

---

### Post by ddixonr on 2008-06-15
Great! Thanks a lot!

---

