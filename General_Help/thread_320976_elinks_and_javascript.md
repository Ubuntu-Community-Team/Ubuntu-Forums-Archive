---
title: "elinks and javascript"
date: 2006-12-18
forum: General Help
---

### Post by jsmidt on 2006-12-18
Elinks is supposed to be able to support javascript when it is enabled.  How do you enable javascript in elinks in ubuntu?

---

### Post by Micah Elliott on 2007-02-15
It would appear to depend on Mozilla's SpiderMonkey being present, which I would guess already is since Edgy includes FF.  [Here's]("http://elinks.or.cz/documentation/manual.html#ecmascript") an explanation.

From autoconf it appears that the default would be to enable SpiderMonkey:

[INDENT]```
$ ./configure --help |grep -i java
  --without-spidermonkey  disable SpiderMonkey Mozilla JavaScript engine support

```[/INDENT]

*(Yes, I too would really like to see future Ubuntus set up elinks to enable JavaScript.)*

---

