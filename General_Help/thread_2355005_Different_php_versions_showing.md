---
title: "Different php versions showing"
date: 2017-03-08
forum: General Help
---

### Post by mark114 on 2017-03-08
Hi

I attempted to upgrade my PHP version from 5.3.2 to 5.6.  Everything went according to plan and if I type php --version in the console it shows PHP 5.6 but the server is still using the previous version as phpinfo shows this.  Bit stuck now what else I need to do?

I have 12.04 Ubuntu installed.

---

### Post by TheFu on 2017-03-09
Support for 12.04.5 ends in a month. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) Migrate to a newer supported release ASAP. I wouldn't waste any time on 12.04 stuff. If you have any other version of 12.04, it hasn't been supported for years.

Also, do not replace the system versions of tools. Always setup a sandbox if you need some other specific version. This is a best practice for all web-app scripting languages. You'll need to use the INSTALL/README that comes with the language to set it up, but as a developer, that wouldn't be an issue.  I don't know php, but ruby, perl, python all have ways to have multiple verions of the language installed and used by different webapps. Cannot image that php can't do it as well.

---

### Post by mark114 on 2017-03-11
> **TheFu said:**
> Support for 12.04.5 ends in a month. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) Migrate to a newer supported release ASAP. I wouldn't waste any time on 12.04 stuff. If you have any other version of 12.04, it hasn't been supported for years.

Also, do not replace the system versions of tools. Always setup a sandbox if you need some other specific version. This is a best practice for all web-app scripting languages. You'll need to use the INSTALL/README that comes with the language to set it up, but as a developer, that wouldn't be an issue.  I don't know php, but ruby, perl, python all have ways to have multiple verions of the language installed and used by different webapps. Cannot image that php can't do it as well.

I gave up on the upgrade so decided to back everything up and install 16.10.  Installed without any problems but I should have read the small print as nearly all my sites were not php7 compatible.  Had to turn them all off.  I'm now updating the code so they will run which is a bit of a long haul.  Still, other 'stuff' that wouldn't work before does now so that is something.

---

### Post by dragonfly41 on 2017-03-11
I would explore installing miniconda (part of anaconda) so that you can mix running apps in old or new versions of php.

---

### Post by TheFu on 2017-03-11
Support for 16.10 ends in July - as shown in the link already provided. Really should have installed 16.04, which is an LTS release.  Do not install 17.04 when released in a month on a server. It isn't LTS either.

Don't use the built-in php if you are a developer. Don't.  Use the php equiv of rvm/rbenv or perlbrew so the php you want is the one you have for each app. If you need 20 different PHP installs, that is fine.  With these tools, you can have old versions of php too, but when you do this, you are 100% responsible for patching.

---

### Post by mark114 on 2017-03-11
> **TheFu said:**
> Support for 16.10 ends in July - as shown in the link already provided. Really should have installed 16.04, which is an LTS release.  Do not install 17.04 when released in a month on a server. It isn't LTS either.

Don't use the built-in php if you are a developer. Don't.  Use the php equiv of rvm/rbenv or perlbrew so the php you want is the one you have for each app. If you need 20 different PHP installs, that is fine.  With these tools, you can have old versions of php too, but when you do this, you are 100% responsible for patching.

Darn.  I have a nasty habit of speed reading and end up missing important info.  I have a 2nd server and I think I will install 16.04 on it el pronto.  

Thanks

---

### Post by TheFu on 2017-03-11
> **mark114 said:**
> Darn.  I have a nasty habit of speed reading and end up missing important info.  I have a 2nd server and I think I will install 16.04 on it el pronto.  

Thanks

I hope you have the habit of daily, versioned, backups.  Missing details will kill you on Linux/Unix systems.  You'll need to be able to roll back from the last good backup a bunch .... or have the pain of starting over. Your choice.

---

