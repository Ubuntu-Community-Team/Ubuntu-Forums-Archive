---
title: "WinSCP alternate for ubuntu 16.04"
date: 2016-09-12
forum: General Help
---

### Post by ferronica on 2016-09-12
dear siers,

im looking for application which support SSH/SFTP like windows Os WinSCP.

any application which works like WinSCP for accessing openwrt files and folders easily from my ubuntu/lubuntu system?

[https://postimg.org/image/48a5xxkcb/](https://postimg.org/image/48a5xxkcb/)

---

### Post by TheFu on 2016-09-12
Every file linux manager with a GUI supports sftp/scp (almost).  Just use sftp:// or ssh:// in the URL.  Caja, Thunar, Nautilus, are examples. Also, if you setup ssh-keys and/or ~/.ssh/config for authentication, those will be honored, as expected.

For ssh, open any terminal you like and use **ssh remoteID@remote-server**.  If you setup aliases, per-server settings and/or keys in ~/.ssh/config, those will be honored too.

Oh ... and don't use root. Use a normal userid.  Blocking remote root access is a standard Unix security technique.

---

### Post by ferronica on 2016-09-13
@TheFu,

not the same case here. via terminal SSH working fine when i do file manager getting error in connection as i posted screen shot above


[[img]https://s11.postimg.org/9k08el5m7/Screen_Shot_2016_09_12_at_11_37_44_PM.png[/img]](https://postimg.org/image/9k08el5m7/)

---

### Post by mastablasta on 2016-09-13
you can try Filezilla

---

### Post by anglican on 2016-09-13
> **ferronica said:**
> @TheFu,

not the same case here. via terminal SSH working fine when i do file manager getting error in connection as i posted screen shot above



Probably because you're trying to use root - a really bad idea, which is why, by default, most ssh configurations don't allow it. Try using the file browser with a different user name.

H

---

### Post by TheFu on 2016-09-13
Did you try ssh:// in the URL too?  Tried caja, thunar, and/or nautilus?  I don't remember exactly which (ssh/sftp) is used for each of the file managers.  Know the file managers I've listed work with sftp/ssh in the URLs - though I don't use file managers much (perhaps once a quarter).  Tested with **caja** before posting initially - it worked fine.  I've used thunar with it before and know that works too (but didn't install it to check in the last day).  Just tested **pcmanfm** - that works with ssh:// OR sftp:// in the location/URL.

Cannot remember trying to use root ever for something like this.  Tried a different userid?  Blocking remote root access is a normal thing.

Lastly, does the target system have a firewall running and blocking?  If ssh works, this is unlikely - I'm assuming openssh-server is providing the sftp service, not some other package like vsftp or proftp.

If you have bash-completion loaded and type sftp <tab> ... it will look through your ~/.ssh/config and /etc/hosts for systems to connect with. Don't think it looks much farther until after the server/ip is entered, then it will send the tab request to the remote system for completion.  That's handy when I don't remember the entire path for a file I'd like to sftp back or push to a non-default location on the remote box.

Sorry, but that's all I got.

---

### Post by Habitual on 2016-09-13
gigolo perhaps?

---

### Post by ferronica on 2016-09-14
> **TheFu said:**
> Did you try ssh:// in the URL too?  Tried caja, thunar, and/or nautilus?  I don't remember exactly which (ssh/sftp) is used for each of the file managers.  Know the file managers I've listed work with sftp/ssh in the URLs - though I don't use file managers much (perhaps once a quarter).  Tested with **caja** before posting initially - it worked fine.  I've used thunar with it before and know that works too (but didn't install it to check in the last day).  Just tested **pcmanfm** - that works with ssh:// OR sftp:// in the location/URL.

Cannot remember trying to use root ever for something like this.  Tried a different userid?  Blocking remote root access is a normal thing.

Lastly, does the target system have a firewall running and blocking?  If ssh works, this is unlikely - I'm assuming openssh-server is providing the sftp service, not some other package like vsftp or proftp.

If you have bash-completion loaded and type sftp <tab> ... it will look through your ~/.ssh/config and /etc/hosts for systems to connect with. Don't think it looks much farther until after the server/ip is entered, then it will send the tab request to the remote system for completion.  That's handy when I don't remember the entire path for a file I'd like to sftp back or push to a non-default location on the remote box.

Sorry, but that's all I got.


Sir,


from same machine lubuntu using pacman file manager accessing SSH/SFTP (browsing all files) ipfire and pfsense router without any issue.

when i try access openwrt from it no luck :( as i posted screenshot error..... above

Do i need to install openssh server in my openwrt router to work?

---

### Post by TheFu on 2016-09-14
Thanks for your patience.  Missed that this was a router running openwrt AND you were trying to sftp into it, not through it.

openwrt doesn't run the normal openssh-server. It is using a trimmed down version, which may not support sftp at all. Google found this: [https://wiki.openwrt.org/doc/howto/sftp.server](https://wiki.openwrt.org/doc/howto/sftp.server)

---

### Post by ferronica on 2016-09-19
> **TheFu said:**
> Thanks for your patience.  Missed that this was a router running openwrt AND you were trying to sftp into it, not through it.

openwrt doesn't run the normal openssh-server. It is using a trimmed down version, which may not support sftp at all. Google found this: [https://wiki.openwrt.org/doc/howto/sftp.server](https://wiki.openwrt.org/doc/howto/sftp.server)

yes thanks even i found same url installing open ssh server and worked like charm thanks for assistance :)

---

