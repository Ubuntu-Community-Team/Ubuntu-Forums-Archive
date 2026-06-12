---
title: "simple SSH tunnel"
date: 2007-12-03
forum: General Help
---

### Post by Tex-Twil on 2007-12-03
Hello,
I'd like to create a simple SSH tunnel to redirect **all** the web traffic from "my-pc" through my "tunnel-pc" 

A solution would be to set up a proxy on my  "tunnel-pc"  and then redirect the traffic through it
```

ssh -l my_user -L 7777:localhost:8080 tunnel-pc

```
and then simply set the browser to connect to the 7777 port on my pc. My question is if there is a solution without setting a prox on my "tunnel-pc"
Thanks,
Tex

---

### Post by cdenley on 2007-12-03
I think this will work. Your tunnel can function as a socks proxy. Just configure your browser to use localhost:7777
```

ssh -l my_user -D 7777 tunnel-pc

```

---

### Post by Tex-Twil on 2008-01-22
> **cdenley said:**
> I think this will work. Your tunnel can function as a socks proxy. Just configure your browser to use localhost:7777
```

ssh -l my_user -D 7777 tunnel-pc

```

Ok thanks ! This is exactly what I needed. Now I can redirect any protocol to this SSH tunnel. ;)

---

