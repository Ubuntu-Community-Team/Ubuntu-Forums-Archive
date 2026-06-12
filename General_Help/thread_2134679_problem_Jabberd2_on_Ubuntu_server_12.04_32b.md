---
title: "problem Jabberd2 on Ubuntu server 12.04 32b"
date: 2013-04-11
forum: General Help
---

### Post by Tres_Iqus on 2013-04-11
Users can't login on my server, install jabber2 with apt-get (apt-get install jabberd2) and configure host and mysql user and password

any idea from my problem

Log  file

c2s.xml:
```

hu Apr 11 21:21:43 2013 [notice] [9] SASL authentication succeeded: mechanism=DIGEST-MD5; authzid=user@domain
Thu Apr 11 21:21:43 2013 [notice] [9] bound: jid=user@domain/Gajim

```

sm.log:
```

Thu Apr 11 21:21:43 2013 [notice] user not found, can't start session: jid=user@domain/GAJIM

```

---

### Post by Tres_Iqus on 2013-04-12
Solved insert on mysql table **active**

```

INSERT INTO `active` (`collection-owner`, `object-sequence`, `time`) VALUES
('< user >@< realm >', 1, NULL),

```

I'm not sure this is the right solution but the server is running and users can enter the chat

---

