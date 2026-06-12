---
title: "Postfix header"
date: 2008-02-14
forum: General Help
---

### Post by kenmiles on 2008-02-14
When I send mail in the received field in the header unknown is in brackets as in the example below.-
Received: from kenneth-desktop (unknown [86.132.173.43])
     by kmiles.co.uk (Postfix) with SMTP id 09A0610781A4
Can anyone tell me if this is correct or should something missing here.
Regards, Kenneth.

---

### Post by kidders on 2008-02-15
Hi there,

That seems fine.

The address you posted doesn't resolve to anything (it looks like a domestic UK BT broadband address), so "unknown" is what you'd expect other SMTP servers to see you as. "kenneth-desktop" is who your server *said* it was. I suppose the fact that they don't match will contribute to outgoing messages' spam rating, but it's probably pretty high anyway.

---

