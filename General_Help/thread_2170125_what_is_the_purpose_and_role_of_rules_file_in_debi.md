---
title: "what is the purpose and role of rules file in debian packaging"
date: 2013-08-25
forum: General Help
---

### Post by satyagowtham-k-gmail on 2013-08-25
I've asked this question here [http://askubuntu.com/questions/336253/what-is-the-purpose-and-role-of-rules-file-in-debian-packaging](http://askubuntu.com/questions/336253/what-is-the-purpose-and-role-of-rules-file-in-debian-packaging). As @andrewsomething said I executed 
```
$ dh binary-arch --no-act
dh: No packages to build.
```

And in ```
debian/install
``` file I want to use variables as I did in Makefile. I want the install file something like this

```
config.xml /etc/${APPNAME}.conf.xml
devices.rules /etc/udev/rules.d/${APPNAME}.rules
error.log /var/log/${APPNAME}.log
init.conf /etc/init/${APPNAME}.conf
init.d /etc/init.d/${APPNAME}
${CND_ARTIFACT_NAME_${CONF}} /usr/local/bin/${APPNAME}

```

---

