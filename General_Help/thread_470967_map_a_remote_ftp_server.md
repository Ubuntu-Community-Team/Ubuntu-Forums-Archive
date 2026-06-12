---
title: "map a remote ftp server"
date: 2007-06-11
forum: General Help
---

### Post by lukemack on 2007-06-11
Hi,

Is there a way to map a remote ftp server to a mount point in ubuntu? The equivalent on windows is 'map network drive'. What I want is a virtual directory on the ubuntu file system which actually points to a folder on a remote ftp server and handles the authentication seamlessly. 

I'm sure this must be possible in Linux but I'm not sure how? A giu tool would be preferable but command line tools are ok too.

thanks!

<L>

---

### Post by lukemack on 2007-06-11
i figured this out. from the places menu on the desktop, choose connect to server..

---

### Post by cantormath on 2007-06-11
or you can use shfs for ssh connections.....ssh is alot more secure
shfs-source - (secure) SHell File System module source
shfs-utils - (secure) SHell File System mount programs
sshfs - filesystem client based on SSH File Transfer Protocol

look for a howto to do this, its not too hard.

---

### Post by lukemack on 2007-06-11
thanks. any idea why my mapped remote server does not appear in Komodo file dialogs? Komodo is a PHP IDE. It seems to appear everywhere else. Is there a setting somewhere which governs what appears in application file browsers?

thanks,

lukemack.

---

