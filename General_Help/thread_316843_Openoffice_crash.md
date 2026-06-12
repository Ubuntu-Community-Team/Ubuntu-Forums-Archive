---
title: "Openoffice crash"
date: 2006-12-11
forum: General Help
---

### Post by eg-maverick on 2006-12-11
When I copy text that has any formatting (such as bullets, numbers, any autoformatting) from OpenOffice writer and paste it in either Evolution or Thunderbird, Openoffice crashes. It is 100% reproducible. I am running 6.10. I opened a bug with Openoffice ([http://www.openoffice.org/issues/show_bug.cgi?id=71672](http://www.openoffice.org/issues/show_bug.cgi?id=71672)) but they say it is an ubuntu issue. They recommend I uninstall the ubuntu pre-installed version and install OO directly from their website. Any help or advice on this tact?
Thanks,
Craig

---

### Post by claypole on 2006-12-13
I have a similar problem and it only started occurring after a synaptic update last week to OpenOffice.

---

### Post by sudonim on 2006-12-13
I've been having a lot of problems since the open office update. Originally I thought it was just when trying to open .xls format files but now I've downloaded and attempted to install oo 2.1 from oo.org and that does even less. I'm going to try and go back to an older version and see if that works.

I installed 2.1.0 by taking the rpm's and using alien to turn them into debian packages, then attempted to use dpkg to install the newly created packages. Didn't seem to work that well...

Is anyone else experiencing problems?

---

### Post by nix4me on 2006-12-13
The text pasting problem is a known bug.  Hasn't been fixed yet.  This bug is well documented and nothing has been done about it for edgy.  There are some openoffice packages that have been fixed, however you have to use a third party repository to get them.

nix4me

---

### Post by eg-maverick on 2006-12-14
> **nix4me said:**
> The text pasting problem is a known bug.  Hasn't been fixed yet.  This bug is well documented and nothing has been done about it for edgy.  There are some openoffice packages that have been fixed, however you have to use a third party repository to get them.

nix4me

nix4me,
well documented where? The OO guys didn't seem to know about it. I'd like to know so I can track its progress.
Thanks.
Craig

---

### Post by nix4me on 2006-12-14
There are several posts on this forum about it. 

Also, there are probably at least 20 duplicate bugs on launchpad about this problem.

Here is the official bug report, a fix is proposed, should enter repositories soon.

[https://launchpad.net/bugs/62432](https://launchpad.net/bugs/62432)

nix4me

---

### Post by jrjazzman on 2006-12-15
This bug combined with the bad fonts makes OO.o just about unusable for me.  I don't understand how this got released, and why Ubuntu put such garbage in the official repository.

---

### Post by eg-maverick on 2006-12-15
> **nix4me said:**
> There are several posts on this forum about it. 

Also, there are probably at least 20 duplicate bugs on launchpad about this problem.

Here is the official bug report, a fix is proposed, should enter repositories soon.

[https://launchpad.net/bugs/62432](https://launchpad.net/bugs/62432)

nix4me

Thanks.
Craig

---

### Post by KaiO on 2006-12-16
I had a similar problem and "fixed" it by disabling *Klipper* (clipboard tool).
Copy/cut and paste still works, but you lose the extra functions in Klipper.
Might be worth a try.

---

