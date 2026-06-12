---
title: "XMMS to SHOUTcast"
date: 2007-07-15
forum: General Help
---

### Post by Swab on 2007-07-15
I'm trying to steam from XMMS to a SHOUTcast server on the same machine.  The SHOUTcast log shows that the connection between the two appears to be made but SHOUTcast is not receiving any data.

```

<07/15/07@11:49:01> [SHOUTcast] DNAS/Linux v1.9.8 (Feb 28 2007) starting up...
<07/15/07@11:49:01> [main] pid: 8592
<07/15/07@11:49:01> [main] loaded config from sc_serv.conf
<07/15/07@11:49:01> [main] initializing (usermax:10 portbase:8000)...
<07/15/07@11:49:01> [main] No ban file found (sc_serv.ban)
<07/15/07@11:49:01> [main] No rip file found (sc_serv.rip)
<07/15/07@11:49:01> [main] opening source socket
<07/15/07@11:49:01> [main] source thread starting
<07/15/07@11:49:01> [main] opening client socket
<07/15/07@11:49:01> [main] Client Stream thread [0] starting
<07/15/07@11:49:01> [main] client main thread starting
<07/15/07@11:49:01> [source] listening for connection on port 8001
<07/15/07@11:49:22> [source] connected from 192.168.1.10   
<07/15/07@11:49:22> [source] icy-name:Test Stream ; icy-genre:
<07/15/07@11:49:22> [source] icy-pub:0 ; icy-br:24 ; icy-url:
<07/15/07@11:49:22> [source] icy-irc:N/A ; icy-icq:N/A ; icy-aim:N/A
<07/15/07@11:49:54> [source] no data (30s timeout). disconnecting.

```

I have set the following option in the SHOUTcast conf file
```

MaxUser=10
Password = secret
Portbase = 8000

```


I have configured the liveice XMMS plugin with the following settings:
```

Encoder Type: Lame (3.21 and above)
Executable Name: /usr/bin/lame
Server Address: 192.168.1.10
Server Port: 8001
Encoder Password:  same pass I set on SHOUTcast

```

Anyone got an idea where I have gone wrong?

---

### Post by drytear on 2007-07-15
try settin' xmms to port 8000. i know sc_serv says it's listening to 8001 , but that's somehow wrong :)

---

### Post by Swab on 2007-07-15
I think 8001 is right... well, it does nothing on  8000.

---

### Post by Swab on 2007-07-15
bump

---

