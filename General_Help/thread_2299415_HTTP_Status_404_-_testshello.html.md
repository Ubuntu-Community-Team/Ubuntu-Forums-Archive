---
title: "HTTP Status 404 - /tests/hello.html"
date: 2015-10-18
forum: General Help
---

### Post by houmingc on 2015-10-18
on [http://localhost:8080/](http://localhost:8080/), i checked Tomcat working
"If you're seeing this page via a web browser, it means you've setup Tomcat successfully. Congratulations!"

Below HTML is created and drop in /opt/apache/webapps/ROOT/tests

hello.html
<html>
<head><title>Hello World static HTML</title></head>
<body>
Hello World!
</body>
</html>

in ubuntu mozilla, i paste [http://localhost:8080/tests/hello.html](http://localhost:8080/tests/hello.html)
HTTP Status 404 - /tests/hello.html. Why?

---

### Post by Lars Noodén on 2015-10-18
If you set up [Apache according to the server guide](https://help.ubuntu.com/lts/serverguide/httpd.html) then your default virtual host will have its documents in /var/www/html/   If you're looking in /opt, then something went wrong.

---

### Post by houmingc on 2015-10-18
i did an experiment.
I put Hello.html into /opt/apache/webapps/docs
In brower, [http://localhost:8080/docs/Hello.html](http://localhost:8080/docs/Hello.html) no problem showing it. Please kindly explain.

[COLOR=#000000]my html in /var/www/html/, browser 404[/COLOR]

---

### Post by Lars Noodén on 2015-10-18
/opt is not the usual place for web documents.  So a little background information is needed.  Which version of Ubuntu are you using and how did you install Apache?

---

