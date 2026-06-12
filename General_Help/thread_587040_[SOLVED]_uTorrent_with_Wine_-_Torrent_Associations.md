---
title: "[SOLVED] uTorrent with Wine - Torrent Associations"
date: 2007-10-22
forum: General Help
---

### Post by AsoSako on 2007-10-22
I have successfully installed uTorrent under Wine, and I was wondering if anyone has found a way to associate torrent files with uTorrent without having to open uTorrent first.

---

### Post by celettu on 2007-10-22
Create a file /usr/bin/utorrent, with these contents:

```
#!/bin/sh

cd ~/.wine/drive_c/Program\ Files/uTorrent
if [ "$1" != "" ]; then
        var="`echo $1 | sed 's/\//\\\/g'`"
        var="Z:${var}"
        wine utorrent.exe "$var"
else
        wine utorrent.exe
fi

```

make it executable

```
sudo chmod +x /usr/bin/utorrent
```

Rightclick a torrent file, open it with the command "utorrent"

HTH

---

### Post by lnogueir on 2008-04-26
Hi!

I'm getting this error "unable to load "z" acess denied".

Help please! I LOVE UTORRENT!

Thanks!

---

