---
title: "How to run simple web page from Apache (Ubuntu 16.04, Apache2)"
date: 2016-07-20
forum: General Help
---

### Post by hezy2 on 2016-07-20
Hello,
I've created a simple web page but couldn't understand how to access it from the explorer and I've been told to use Apache. The network is not connected to the internet (LAN). Thanks,
Hezy.

---

### Post by SeijiSensei on 2016-07-20
Call the file "index.html" and replace the version currently in /var/www/html. (You'll need to use sudo to do this.)  Then point a browser at [http://ip.addr.of.server/](http://ip.addr.of.server/).  Your page should appear.

---

### Post by yancek on 2016-07-20
I'm not sure what you mean by "the explorer", are you referring to a file manager?  You need to access it with a web browser such as firefox, chrom, opera, etc. If it's on a local machine, replace 'ip.addr.of.server" in the example above with localhost or 127.0.0.1.

---

### Post by hezy2 on 2016-07-24
I'ts firefox. Thanks.

---

### Post by CantankRus on 2016-07-25
If apache2 is installed and running...
```
service apache2 status
```

then entering in firefox... 
```
localhost
```
should show the web page from **/var/www/html/index.html**

You should see the same page by entering in firefox...
```
/var/www/html/index.html
```

Eg
First pic shows default.
Second pic shows when I have replaced **/var/www/html/index.html** with my
own maintenance page.

---

