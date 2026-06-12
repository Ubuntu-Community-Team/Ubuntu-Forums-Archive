---
title: "How can I totally remove Samba?"
date: 2016-03-12
forum: General Help
---

### Post by yoshii on 2016-03-12
I am getting tired of having to wait for upgrade downloads to services that I don't use and would prefer to have removed.  
One such thing is Samba.  I am never going to use that.  How I can totally remove it?

---

### Post by v3.xx on 2016-03-12
```
sudo apt-get remove samba
```

I just tried this and seems to be ok.  Not removing any major packages.  I guess you need to test it out on your version, I run mate 16o4.  Also there are other samba packages that this command did not remove.  Open up synaptic package manager and have a look.

---

### Post by yoshii on 2016-03-14
sudo apt-get remove samba didn't work for me.  
but I will look at synaptic like you mentioned.

---

### Post by yoshii on 2016-03-14
Ah, synaptic was helpful for getting rid of more of it, but not all of it.  There are some really weird dependencies.  I really don't know why stuff like VLC media player needs samba.  
Sigh, oh well.

---

### Post by vasa1 on 2016-03-14
> **yoshi2 said:**
> ... I really don't know why stuff like VLC media player needs samba.  ...
How do you conclude that? I don't see samba as a dependency, recommend, or suggest when looking at vlc.

---

### Post by mc4man on 2016-03-14
> **vasa1 said:**
> How do you conclude that? I don't see samba as a dependency, recommend, or suggest when looking at vlc.

vlc has a samba plugin package that is a recommend, it deps on libsmbclient. One is free to uninstall the plugin though generally most users don't want to remove libsmbclient. Leaving libsmbclient installed should present no undue downloads waits or whatever..

---

### Post by vasa1 on 2016-03-16
> **mc4man said:**
> vlc has a samba plugin package that is a recommend, it deps on libsmbclient. One is free to uninstall the plugin though generally most users don't want to remove libsmbclient. Leaving libsmbclient installed should present no undue downloads waits or whatever..
Ah!```
Conf vlc-plugin-samba (2.2.1~trusty2 Ubuntu Multimedia for Trusty:14.04/trusty [amd64])

```I didn't see that in the output of *apt-cache show vlc*. Thanks!

---

