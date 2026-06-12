---
title: "[SOLVED] How do I remove host from gFTP"
date: 2008-04-26
forum: General Help
---

### Post by antmenj on 2008-04-26
How do I remove hosts from the host dropdown in gftp?

I entered some wrong entrys and it wants to remember them just the same as the right ones.

---

### Post by Pettman on 2008-04-26
> **antmenj said:**
> How do I remove hosts from the host dropdown in gftp?

I entered some wrong entrys and it wants to remember them just the same as the right ones.

You go and edit them out of the file ~/.gftp/gftprc , they are at the end of it, the lines starts with hosthistory= and is then followed by the host.

---

### Post by antmenj on 2008-04-27
Tryed to find that file via the places menu with little luck so did:

sudo gedit ~/.gftp/gftprc

via the terminal and it worked:)

Thanks

Now if only I could get gftp not to stop in the middle of an upload:confused:

---

### Post by Pettman on 2008-04-27
> **antmenj said:**
> sudo gedit ~/.gftp/gftprcDon't use sudo to edit that file, it's in your home directory (~ is a shorthand for $HOME). To find it in nautilus you click places ->home directory->press ctrl+h to reveal hidden directories (all file and dir names starting with a dot (.) is usually hidden)-> type some part of .gftp to locate the directory, and open it->you're there.

Try setting the transfere-mode to binary instead of ASCII (found in the FTP menu).

PS. if you like my advise please click the thanks button DS. :)

---

