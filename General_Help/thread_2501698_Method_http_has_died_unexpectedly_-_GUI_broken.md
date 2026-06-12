---
title: "Method http has died unexpectedly - GUI broken"
date: 2024-10-17
forum: General Help
---

### Post by devpmgeo on 2024-10-17
Hello!

After updating and running out-of-battery, my wife's laptop with Ubuntu 22.04.5 LTS doesn't boot anymore, I get a "Oh no, something went wrong" white screen. When getting the GNU Grub menu and picking the recovery mode, I first tried the dpkg Repair broken packages option but get some logs about dependencies issues.
Next on the root shell, I have tried the following prompts:

[LIST]
[*]sudo apt update
[/LIST]
I get :
/usr/lib/apt/method/http: error while loading shared libraries: libnettle.so.8: cannot shared object file: No such file or directory 8 times before a method http has died unexpectedly / Sub-process http returned an error code (127)


[LIST]
[*]sudo apt --fix-broken install
[/LIST]
Not working, I get the error mentioned above a lot more


[LIST]
[*]dpkg --force-all --configure- a
[/LIST]
Following [this post in the superuser forum that seems close to my issue]("https://superuser.com/questions/1386209/how-to-solve-this-dependencies-apt-fix-broken-install")
[LIST]
[*]dpkg --purge --force-depends libnettles8 which return that the request is ignored since libnettle8 isn't installed.
[/LIST]

The apt seems broken and the --configure doesn't seem to work either, I am at my research's and wits end. I am very much new to the Linux ecosystem and lack very much any solid basis although I'm willing to learn.

Thank you very much for your help!

---

