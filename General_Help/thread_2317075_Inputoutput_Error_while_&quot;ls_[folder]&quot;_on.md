---
title: "Input/output Error while &quot;ls [folder]&quot; on a virtual server"
date: 2016-03-13
forum: General Help
---

### Post by ole7 on 2016-03-13
Hello everybody,

I have rented a virtual server -running 14.04- where I tried to install the latest updates. The process stalls with:

```
dpkg: error processing archive /var/cache/apt/archives/perl-base_5.18.2-2ubuntu1.1_amd64.deb (--unpack):
 unable to stat `./usr/share/perl/5.18.2/unicore/lib/Hex' (which I was about to install): Input/output error
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)

```

Upon closer look, the folder to-be-installed is pretty much screwed:

```
ls /usr/share/perl/5.18.2/unicore/lib/Hex
d?????????  ? ?    ?        ?            ? Hex
ls: cannot access Hex: Input/output error
```

I cannot run [FONT=courier new]fsck[/FONT], since I don't have access to the underlying root file system on the virtual server.

Are there any ways I can fix this?

Best regards,
Ole

---

### Post by SeijiSensei on 2016-03-13
I'd submit a ticket to customer support.

---

### Post by ole7 on 2016-03-13
I did. We tried a few things, nothing worked. "Ask in the Ubuntu Forums", they said then. :-/

---

### Post by SeijiSensei on 2016-03-14
Can you reinstall, or will that cause too much disruption?

Usually I've seen the type of error you report when there's a problem with the drive or the filesystem.  

I use [Linode]("http://www.linode.com/") where I can spin up a server pretty quickly at minimal cost.  Can you create a new VM and see if the problem persists there?  If it doesn't, you might consider copying over whatever you need from the old server and migrating.

---

