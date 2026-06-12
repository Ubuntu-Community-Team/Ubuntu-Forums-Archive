---
title: "configure: error: C++ preprocessor &quot;/lib/cpp&quot; fails sanity check"
date: 2006-11-23
forum: General Help
---

### Post by telovoyagarcar on 2006-11-23
configure: error: C++ preprocessor "/lib/cpp" fails sanity check


I get this error when trying to install kxdocker..

i checked synaptics for CCP and ccp 4.1 is installed... then i also installed 4.0 just in case but still get the same error..

Any ideas?

---

### Post by taurus on 2006-11-23
Maybe you need the build-essential package!!!

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by telovoyagarcar on 2006-11-23
Wow... i don't know what was that... but looks like it works!!
at least the C++ preprocessor stuff...

now it gets stuck with this:


"checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!"


BTW... im trying to follow this guide:
[http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake](http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake)

Thanks again!

---

### Post by Rhaurison Bergamin on 2006-11-29
```
apt-get install xorg-dev
```

---

