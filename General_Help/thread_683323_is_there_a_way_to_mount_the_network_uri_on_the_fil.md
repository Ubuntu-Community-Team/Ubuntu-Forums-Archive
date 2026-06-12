---
title: "is there a way to mount the network:// uri on the filesystem?"
date: 2008-01-30
forum: General Help
---

### Post by musheno on 2008-01-30
I noticed that nautilus supports a "network://" uri.
I was just wondering how one would go about mounting this, so that for example...
If there is a machine "X" running samba on it, I could simply goto something like /media/network/X and see all of its shares using the "ls" command?
If this is not available, it should be, and I am willing to do some work to make it happen, assuming I can be pointed in the right direction.
[Todd_Musheno@yahoo.com]("mailto:Todd_Musheno@yahoo.com?subject=ubuntuNetMount")

---

### Post by imtheguru on 2008-01-31
> **musheno said:**
> If there is a machine "X" running samba on it, I could simply goto something like /media/network/X and see all of its shares using the "ls" command?Research the usage of smbmount.

Cheers.

---

### Post by musheno on 2008-02-03
It is my understanding that smbmount is only for shares...
My example shows network:// as the uri, not smb://X so unless I am missing something from man smbmount
This will not work, as it only deals with individual shares, not all available shares like the network:// url.
I hope this is clear, if not please ask for clarification.
Todd

---

### Post by imtheguru on 2008-02-03
> **musheno said:**
> It is my understanding that smbmount is only for shares...
My example shows network:// as the uri, not smb://XNetwork:/// is a Nautilus-specific URI.
[http://safari.oreilly.com/9781593271527/Iusing_nautilus_as_a_network_browser](http://safari.oreilly.com/9781593271527/Iusing_nautilus_as_a_network_browser)

Nautilus has its own implementations of samba client browsing and share mounting... the limitation being it is point and click.

To integrate with the shell, use smbclient and smbmount.

Cheers.

---

