---
title: "Samba &quot;Read Error: Connection reset by peer&quot;"
date: 2007-10-17
forum: General Help
---

### Post by abrichr on 2007-10-17
I'm trying to mount a remote network share.  I managed to determine that I need to use Samba, but I'm still unable to mount:

```

$ sudo mount -t smbfs -o username=<username>,password=<password>,port=443 //carei.webexone.com/~docs /media/shared/documents/esct/webex
read_socket_with_timeout: timeout read. read error = Connection reset by peer.
Receiving SMB: Server stopped responding
15085: session request to CAREI.WEBEXONE.C failed (Read error: Connection reset by peer)
read_socket_with_timeout: timeout read. read error = Connection reset by peer.
Receiving SMB: Server stopped responding
15085: session request to CAREI failed (Read error: Connection reset by peer)
read_socket_with_timeout: timeout read. read error = Connection reset by peer.
Receiving SMB: Server stopped responding
15085: session request to *SMBSERVER failed (Read error: Connection reset by peer)
SMB connection failed

```

No idea what to do at this point.  Any help would be appreciated.

---

