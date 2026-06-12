---
title: "How do I identify running web servers?"
date: 2008-01-16
forum: General Help
---

### Post by artnz on 2008-01-16
When start Xampp I get the message " Another web server daemon is already running"

How can I identify what it is and turn it off?

---

### Post by PilotJLR on 2008-01-16
Try a:
```

netstat -tap

```

And see what is listening on the http (80) port.

You can also guess that it's apache, and shut it down: sudo /etc/init.d/apache2 stop

---

### Post by artnz on 2008-01-16
Thanks. Apache isn't running because some other server is.

The only thing I couldn't identify when I ran your command was;

376/java           
tcp6       0      0 *:ssh                   *:*                     LISTEN     -

Could this be the problem?

---

