---
title: "Slow internet and IP 6"
date: 2004-11-05
forum: General Help
---

### Post by hdo781 on 2004-11-05
Hello.  I would like to begin by saying I love Ubuntu.  The only problem I have is that it is using the new Internet Protocol 6, which slows down my internet surfing.  Is there a way for me to disable IP6 and go to using IP4?

---

### Post by p!=f on 2004-11-05
[QUOTE=hdo781]Hello. I would like to begin by saying I love Ubuntu. The only problem I have is that it is using the new Internet Protocol 6, which slows down my internet surfing. Is there a way for me to disable IP6 and go to using IP4?[/QUOTE]  Easy as pie.
  ```

  sudo nano -w /etc/modutils/aliases
  
  # Aliases to tell insmod/modprobe which modules to use
  
  # Uncomment the network protocols you don't want loaded:
  # alias net-pf-1 off			# Unix
  # alias net-pf-2 off			# IPv4
  # alias net-pf-3 off			# Amateur Radio AX.25
  # alias net-pf-4 off			# IPX
  # alias net-pf-5 off			# DDP / appletalk
  # alias net-pf-6 off			# Amateur Radio NET/ROM
  # alias net-pf-9 off			# X.25
  alias net-pf-10 off		   # IPv6
  # alias net-pf-11 off		   # ROSE / Amateur Radio X.25 PLP
  # alias net-pf-19 off		   # Acorn Econet
  
  [snip]
  
```

---

### Post by jdong on 2004-11-05
That may not be all... Do search the HOWTO forum, this has been brought up a number of times. It only affects the Mozilla browsing engines. Perhaps the best fix is to disable ipv6 via about:config (search)

---

