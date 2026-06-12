---
title: "Ubuntu hangs at &quot;Enter pass phrase:&quot;"
date: 2007-11-13
forum: General Help
---

### Post by ScottCC on 2007-11-13
I installed Ubuntu on same drive as Vista/Xp no probs there, I got the webserver configured and was using it for about a day.  The first time i rebooted The screen asked me for a pass phrase, which was needed everything apache starts, no prob i knew the pass phrase.  Well when I entered it, prompt froze, I couldn't do anything.  Does anyone know what the problem is, it has to be something simple, I can't find anything online!

---

### Post by ScottCC on 2007-11-13
I'm able to get in if I don't enter a pass phrase 4 times and let it error.  Then I can login and start the websterver and enter the pass phrase with no problems.  This will be quite annoying though, I could stop apache from loading on startup i guess, that doesn't seem right though.

---

### Post by TerryHowe on 2008-05-01
I don't know the exact solution to your problem, but it is caused by giving apache an encrypted RSA key.  It needs to be stored in plain text.

---

### Post by TerryHowe on 2008-05-01
Ah... [http://httpd.apache.org/docs/2.2/ssl/ssl_faq.html#removepassphrase]("http://httpd.apache.org/docs/2.2/ssl/ssl_faq.html#removepassphrase")

```

cd /etc/ssl/private/
cp server.key server.key.org
openssl rsa -in server.key.org -out server.key

```

---

