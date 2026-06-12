---
title: "need to install SSI in my apache server..."
date: 2008-06-09
forum: General Help
---

### Post by Mia_tech on 2008-06-09
I have an .shtml web page in my ubuntu apache server, which is not displaying nothing, the code is ver simple just to test SSI

```
<!--#echo var="DATE_LOCAL" -->
```

I named the page test.shtml, but it's not displaying anything, how could I get SSI installed?

thanks

---

### Post by RealPSL on 2008-06-09
Did you add "Options +Includes" to the directory options in the httpd.conf file? It is not there by default if you you might want to look at the link below for more details. If you run into trouble post the httpd.conf of the file it references with the relevant syntax

[http://httpd.apache.org/docs/2.0/howto/ssi.html]("http://httpd.apache.org/docs/2.0/howto/ssi.html")

---

