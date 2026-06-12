---
title: "How do I setup iptables so tor and privoxy will work?"
date: 2006-10-10
forum: General Help
---

### Post by Malakia on 2006-10-10
I installed Tor and Privoxy through apt-get and I have iptables installed. Tor works when iptables is stopped but if I let start iptables back up it just keeps timing out. Does anybody have any suggestion on how to fix this or why it is happening.](*,)

---

### Post by Malakia on 2006-10-11
You guys suck, I see I will have to find help elsewhere considering I came here because I figured somebody would have the brains to help me but I guess not.:twisted: :twisted: :twisted:

---

### Post by John.Michael.Kane on 2006-10-12
This may help.[http://linuxreviews.org/man/tor/](http://linuxreviews.org/man/tor/) have a look in your tor settings. you may need to adjust the setting listed below

KeepalivePeriod NUM
    To keep firewalls from expiring connections, send a padding keepalive cell every NUM seconds on open connections that are in use. If the connection has no open circuits, it will instead be closed after NUM seconds of idleness. (Default: 5 minutes)

---

