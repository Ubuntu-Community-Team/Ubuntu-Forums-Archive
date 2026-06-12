---
title: "Alltray and CrossFTP ( java javaws ) startup problem - HELP"
date: 2008-05-22
forum: General Help
---

### Post by vprasaj on 2008-05-22
At startup I get CrossFTP gui right in the face. Annoying and i can't find any solution. Google and yahoo...nothing. I don't know where to look anymore.

Is it possible to get CrossFTP (works with javaws) running with alltray at startup?

**I can start and run both programs separately and then click on the CrossFTP. All O.K. Minimized to tray. So it is working. **

**BUT...**

At startup... i simply cant get it to tray. It starts maximized without tray icon.

Link command made by installer:
```
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/bin/javaws -offline /home/user/.java/deployment/cache/6.0/24/378c6ad8-3a89e3a4
```

Autostart command offered for session:
```
javaws -Xnosplash -offline http://www.crossftp.com/crossftpserver.jnlp
```

Both start up CrossFTP (maximized).

I have try

```
alltray "both versions from above"
```

with options -an -s, but no luck. I simply can't get it to tray. [Found this... CLICK]("http://ubuntuforums.org/showthread.php?t=434972")

:confused: :(

(Maybe there is a way to run java javaws applications in background? I couldn't find that either.)

Any help would be very, very welcome...

---

### Post by vprasaj on 2008-05-22
Hmm, what to do?

What opens javaws so that alltray can handle it?

Anyone?

---

### Post by vprasaj on 2008-05-23
Anyone?

---

### Post by vprasaj on 2008-05-23
It looks like it cant be done...:^o

---

### Post by vprasaj on 2008-05-23
Tomorrow i'll give up... :(

---

### Post by vprasaj on 2008-05-24
Well, i give up.

---

