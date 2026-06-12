---
title: "Firefox add-ons"
date: 2008-05-24
forum: General Help
---

### Post by Elena678 on 2008-05-24
Hello, i just updated my system to the Ubuntu 8.04.

My Firefox is also updated now, and i was trying to install a add on, but i have all the time an annoying error:

```
"application name" will not be installed because it does not provide secure updates 
```

okej, i know it is something to hold the computer save, but i am sure the prog is ok, i use it for a long time now.

do somebody know how i can install my add-on?

thanks for the help

greetings

---

### Post by latna on 2008-05-25
I just ran across this while searching for something else: [http://kb.mozillazine.org/Firefox_:_Issues_:_Can't_Install_Themes_or_Extensions]("http://kb.mozillazine.org/Firefox_:_Issues_:_Can't_Install_Themes_or_Extensions")

Type about:config in the address bar and look for the value extensions.checkupUpdateSecurity and change it's value to false.

---

### Post by Elena678 on 2008-05-27
I don't have a extensions.checkupUpdateSecurity in that config

---

### Post by latna on 2008-05-27
Try creating it. In the about:config window, right click and select new -> boolean. Give it the name extensions.checkupUpdateSecurity and set it's value to false.

Keep in mind that I haven't tried it. I don't have any extensions that require it. But this is coming from the mozilla knowledge base so hopefully it works.

---

### Post by Elena678 on 2008-06-05
a pitty, but that is not working..

---

