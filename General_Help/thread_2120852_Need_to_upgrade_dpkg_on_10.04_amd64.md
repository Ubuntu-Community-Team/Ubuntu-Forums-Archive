---
title: "Need to upgrade dpkg on 10.04 amd64"
date: 2013-02-27
forum: General Help
---

### Post by tixetsal on 2013-02-27
Hi, folks. I have encountered a scenario where I need a newer version of dpkg (one that supports xz compression) in order to keep using a certain repository. I've found a PPA that has a .deb of the newer version built. Are there any potential pitfalls to this scenario that I might be overlooking? I've used dpkg countless times to perform a task, but I've never tried to manually upgrade it before. Does anyone have previous experience with this?

---

### Post by TheFu on 2013-02-27
> **tixetsal said:**
> Hi, folks. I have encountered a scenario where I need a newer version of dpkg (one that supports xz compression) in order to keep using a certain repository. I've found a PPA that has a .deb of the newer version built. Are there any potential pitfalls to this scenario that I might be overlooking? I've used dpkg countless times to perform a task, but I've never tried to manually upgrade it before. Does anyone have previous experience with this?

Aren't you patching all the programs on the system weekly using the built-in tool?  Using dpkg directly is not needed.```

$ sudo apt-get update
$ sudo apt-get dist-upgrade
```should be all that you need to stay patched (kernel, OS and applications) until Apr 2015 if this is a server. If this is a desktop, you have until April of this year and **it is time to update to 12.04 LTS** which does get 5 yrs support cycles.

Using dpkg directly when there are other dependencies involved is not safe unless you are an expert.  I only use it directly for programs outside any PPA - perhaps 2 across all the machines that I manage.

OTOH, if you're already doing this, then it is time to get the newer dpkg source code and start compiling yourself.

---

### Post by Sef on 2013-02-27
> Are there any potential pitfalls to this scenario that I might be overlooking?

It could crash your system if there is conflict. Best to back up your system with [Clonezilla]("http://clonezilla.org") before changing anything. Nothing is 100% guaranteed to work.

---

### Post by tixetsal on 2013-02-27
> **TheFu said:**
> Aren't you patching all the programs on the system weekly using the built-in tool?  Using dpkg directly is not needed.```

$ sudo apt-get update
$ sudo apt-get dist-upgrade
```should be all that you need to stay patched (kernel, OS and applications) until Apr 2015 if this is a server. If this is a desktop, you have until April of this year and **it is time to update to 12.04 LTS** which does get 5 yrs support cycles.

Using dpkg directly when there are other dependencies involved is not safe unless you are an expert.  I only use it directly for programs outside any PPA - perhaps 2 across all the machines that I manage.

OTOH, if you're already doing this, then it is time to get the newer dpkg source code and start compiling yourself.

I am not trying to upgrade the entire operating system. I'm curious about manually upgrading dpkg. I administer many servers which are more in need of a refresh than this particular box. I don't want to migrate to 12.04 just yet, given that I have another year before I must be concerned with EOL. Also, doing dist-upgrade from one release to another in a production server environ is just plain frightening; there are too many unknowns. I'll backup all of my configs and DB stuff and do a clean install when the time comes.

> **Sef said:**
> It could crash your system if there is conflict. Best to back up your system with [Clonezilla]("http://clonezilla.org") before changing anything. Nothing is 100% guaranteed to work.

Ha! It's funny that you mention this because this problem was brought on by using DRBL from the SF repos. This machine is a helpdesk / ftp / imaging server / chat server / swiss army knife. I will definitely take an image before I try to upgrade dpkg.

---

### Post by TheFu on 2013-02-27
dist-upgrade does not cause a distribrution to be updated from 10.04 to 12.04.  It only installs any libc and kernel updates ... which is usually a good idea, but not always.  To do a real distribution update, there is a different tool ... **do-release-upgrade**.

How every server is patched is extremely personal. In highly secure environments (private networking with air-gaps), I don't know that I'd patch much at all. But if a machine is on the internet, I'd patch religiously - weekly.  If the machine is that critical, then I'd have an identical server that was patched every other week, so that 1 was always running and happy.  

For production servers inside a corporate environment, patching becomes a more complicated.  If it were really critical, I'd try it out on the test box.  I'd make a good backup first, of course.  Lacking a test box, I'd use a VM configured as close to production in the ways that mattered, and try it out.

Since you are manually considering doing this, why not manually make a copy of the older dpkg.deb file and everything under /var/lib/dpkg/, /etc/apt and give it a try with the newer dpkg?  If the differences are so great that the DBs are not compatible, you can roll back with the backup or force an install of the older version (unless the APT DB changed).

This plan is a little out of the ordinary.  Interesting and I can see where this would be useful.

---

### Post by schragge on 2013-02-27
You probably mean [Lucid-bleed](https://launchpad.net/~lucid-bleed/+archive/lucidbleed-exp) PPA. I guess you only need two debs from there: dpkg itself and tar (dpkg 1.16 depends on tar>=1.23, but lucid contains tar 1.22). Does it warrant adding a PPA that contains lots of packages? If you're not comfortable with apt-pinning ([uhelp]community/PinningHowto[/uhelp]) then downloading just [these](http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/pool/main/d/dpkg/) [two](http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/pool/main/t/tar/) packages from there, and installing them with *dpkg -i* seems better option to me.

Alternatively, you can try to request an official backport of dpkg as described in [uwiki]UbuntuBackports[/uwiki].

---

### Post by schragge on 2013-02-27
> **TheFu said:**
> If the differences are so great that the DBs are not compatible, you can roll back with the backup or force an install of the older version (unless the APT DB changed).AFAIK, dpkg DB doesn't changed in incompatible way since lucid. Nothing prevents using the dpkg from precise with the APT from lucid. As said, you only need to install the newer tar first.

However, building the new dpkg from source on lucid is another story. Some build dependencies like *gettext* and *po4a* cannot be satisfied by the versions present in lucid. That's why you're better off using ready-built debs from the PPA or waiting for an official backport.

---

### Post by tixetsal on 2013-02-28
> **TheFu said:**
> dist-upgrade does not cause a distribrution to be updated from 10.04 to 12.04.  It only installs any libc and kernel updates ... which is usually a good idea, but not always.  To do a real distribution update, there is a different tool ... **do-release-upgrade**.

How every server is patched is extremely personal. In highly secure environments (private networking with air-gaps), I don't know that I'd patch much at all. But if a machine is on the internet, I'd patch religiously - weekly.  If the machine is that critical, then I'd have an identical server that was patched every other week, so that 1 was always running and happy.  

For production servers inside a corporate environment, patching becomes a more complicated.  If it were really critical, I'd try it out on the test box.  I'd make a good backup first, of course.  Lacking a test box, I'd use a VM configured as close to production in the ways that mattered, and try it out.


You're absolutely right about dist-upgrade. I was mistaken. I also agree with everything that you said about patching. After reading the responses to this thread I had decided to mock up the scenario either on different physical hardware or in a VM.

> **schragge said:**
> You probably mean [Lucid-bleed](https://launchpad.net/~lucid-bleed/+archive/lucidbleed-exp) PPA. I guess you only need two debs from there: dpkg itself and tar (dpkg 1.16 depends on tar>=1.23, but lucid contains tar 1.22). Does it warrant adding a PPA that contains lots of packages? If you're not comfortable with apt-pinning ([uhelp]community/PinningHowto[/uhelp]) then downloading just [these](http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/pool/main/d/dpkg/) [two](http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu/pool/main/t/tar/) packages from there, and installing them with *dpkg -i* seems better option to me.

Alternatively, you can try to request an official backport of dpkg as described in [uwiki]UbuntuBackports[/uwiki].

> **schragge said:**
> AFAIK, dpkg DB doesn't changed in incompatible way since lucid. Nothing prevents using the dpkg from precise with the APT from lucid. As said, you only need to install the newer tar first.

However, building the new dpkg from source on lucid is another story. Some build dependencies like *gettext* and *po4a* cannot be satisfied by the versions present in lucid. That's why you're better off using ready-built debs from the PPA or waiting for an official backport.

Thank you for the input. You were correct about the Lucid-bleed PPA and pinning, and your point about just manually installing dpkg and tar made a great deal of sense. I was going to mock this up and give it a trial run in a test environ, but the DRBL devs updated their repo (in less than 24 hours even!) after I filed a bug report. [http://sourceforge.net/p/drbl/bugs/5/](http://sourceforge.net/p/drbl/bugs/5/) I appreciate both of you brainstorming this with me. I'm going to mark this as solved.

---

