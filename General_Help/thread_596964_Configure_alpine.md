---
title: "Configure alpine"
date: 2007-10-30
forum: General Help
---

### Post by ahvargas on 2007-10-30
Anyone know how to configure alpine so i can read my google mail ? or someone know for some faq on the interenet.

---

### Post by igpf on 2008-03-14
did you figure this out?  is it possible to do this?

---

### Post by mali2297 on 2008-03-14
I don't use gmail myself, but...

Edit the *inbox-path* line in **~/.pinerc** into
```

inbox-path={imap.gmail.com/ssl/novalidate-cert/user=igpf@gmail.com}INBOX

```

If you use POP, make it instead
```

inbox-path={pop.gmail.com/pop3/ssl/novalidate-cert/user=igpf@gmail.com}INBOX

```

If you also want to be able to post messages, edit the *smtp-server* line to
```

smtp-server=smtp.gmail.com:587/tls/user=igpf@gmail.com

```

People seem to have had problems with the SMTP settings. If the above doesn't work, try
```

smtp-server=smtp.gmail.com/submit/user=igpf@gmail.com

```

---

