---
title: "Hardy - disable sharing"
date: 2008-04-27
forum: General Help
---

### Post by Guci on 2008-04-27
Hi, first of all sorry for my bad english.

After upgrade to Hardy i see in my Places -> Networks servers and then Windows network and in context menus options to sharing and....
How can i remove/uninstall/disable it (windows network, network servers, options in menus and ...)? Im not in any local network.

I hope you understand what i meaned.
Thank you for all ideas

---

### Post by ryanhaigh on 2008-04-27
You could try removing smbclient although if you ever do want to access a windows network share you will probably have to reinstall. Can I ask what your reason for doing this is? If its a matter of saving space you may be able to edit the menu so that this item isn't shown by right clicking on Applications and selecting edit menus.

---

### Post by natrixgli on 2008-04-27
Hi,

Just wanted to point out that the menu editor can't modify the 'Places' menu, only Applications, and System.

Not sure how to edit Places, aside from adding bookmarks.

FYI: Your computer can see others on the network, but they can't see you unless you install and configure samba/nfs/etc.


Cheerio,

-n8

---

### Post by Guci on 2008-04-27
I uninstalled smbclient, menu icons disappeared but in nautilus there is still "network servers"...

Im not in any local network (and my computer dont see any other computers or devices). So why there is places - Network Servers ? Why windows network ?

---

### Post by ryanhaigh on 2008-04-27
The reason is that nautilus must work for everyone, having the ability to connect to network servers is obviously important not only in coporate but increasingly in home situtations. Nautilus wouldn't be able to determine whether there are network shares available to you without looking for them first so it is just more efficient to offer the ability to connect to them.

---

### Post by Guci on 2008-04-27
ok ok but how can i get rid of this ? Dont tell me that you are all in some local network and use this functions ... or if not ... you arent bother of this.:confused:

---

### Post by ryanhaigh on 2008-04-27
Well yes I have a local network, as do my parents, my partner, her parents and everyone else I know with a computer. To be honest I can't see what the big deal is if you don't want to use the feature just don't use it. If it bothers you that much there may be a way to disable it in gconf-editor or you may have to recompile nautilus with this option disabled.

---

### Post by Guci on 2008-04-27
> Well yes I have a local network, as do my parents, my partner, her parents and everyone else I know with a computer...

Windows network ;-) ? Ok I have local network too (Unix network, no Windows network, so why i must see in places a place which dont exist ???) but with my desktop computer not with my laptop ;-).

> To be honest I can't see what the big deal is if you don't want to use the feature just don't use it.
 If it bothers you that much there may be a way to disable it in gconf-editor or you may have to recompile nautilus with this option disabled.

If I a remember .... This thread was about "How" :-( :-((for example how can i disable it via gconf-editor).

> ryanhaigh: The reason is that nautilus must work for everyone, having the ability to connect to network servers...

i understand and its very good :-) but ... why i must see "Windows network" if any Windows network dont exist (its normal to see places in nautilus that dont exist ?)... (why nautilus cant do this: after connecting to network nautilus show me "network servers" and network and after disconnect hide it ?)

Gutsy was perfect in this :-(, but Hardy is better in other things
This is neverending discussion. I dont want talk about it anymore
Sorry for my english.
Bye.

---

