---
title: "Why Ubuntu specific packages?"
date: 2005-08-01
forum: General Help
---

### Post by eeried on 2005-08-01
I'm a new user of ubuntu and I have  a few questions 

Why does Ubuntu makes its own packages?

Doesn't this entail some problems (not to mention quite a lot of extra work for the Ubuntu maintainers and developers!)? 

For example I read about the annoucement about the faulty Firefox package. In this package you have an extension which casues some problems.

Extensions aren't necessarily safe (actually they may be a vehicule for security problems because they are unchecked by he Mozilla Foundation) for  and the one in question "browser tab" is rather unnecessary now since Firefox has other ways of giving your control over tabs (from Firefox 1.0 I think).

Cheers,

---

### Post by adwait on 2005-08-01
I don't think Ubuntu has a different version of the browser...its just a matter of being included in the repositories.

---

### Post by craigevil on 2005-08-01
I think the question is asking why Ubuntu specific packages instead of just Debian ones. Why repackages apps that already work under Debian ? 

Why not keep it simple like MEPIS and use straight Debian packages and repositories?


Don't get me wrong I love Ubuntu, I think it is great.  It works great on my laptop.

---

### Post by az on 2005-08-01
Because Canonical contribute to development.  They take packages from Sid which do not work together yet and make them work together.  Then they contribute these patches back to debian.

Is it a lot of work to do?  Well, that is why people who use Ubuntu do not use debian.

Ubuntu has autobuilders just like debian.  Ubuntu developers upload their changed (patched) source to the archive.  Every day (or more often, I think) the autobuilders compile the source and spit out binar packages.

It is the same system as debian.  Developers work on the source and do not have to make binary packages by hand themselves.

---

### Post by Juergen on 2005-08-01
> They take packages from Sid
I think this is the reason, because Sid keeps on changing after Ubuntu takes the snapshot.

So you need packages that are built against the libs that were in Sid whe the snapshot was taken.

If you'd just continue to use Debian's Sid packages, you'd have to update the libs - with no promises of it being stable, in the sense of 'working'.

Yes, it is the same with Debian, why do they need seperate packages for 'Sarge'?
Only that Ubuntu's 'stable' snapshots are taken more often...

---

### Post by craigevil on 2005-08-01
Holy cow batman! That makes sense. The whole Sid and libraries/ snapshot. Thanks.

I run both Ubuntu and Debian Sid/Testing so I understand completely. The Ubuntu way gives you stable up to date packages without the worry of having an unstable system like Sid. Never really thought about it that way.


Keep up the good work, can't wait til Breezy is released.


The only question I have is it safe to use a Debian repository(say one from apt-get.org) for a package not in the Ubuntu repositories?

---

### Post by az on 2005-08-01
[QUOTE=craigevil]
The only question I have is it safe to use a Debian repository(say one from apt-get.org) for a package not in the Ubuntu repositories?[/QUOTE]

No.  Use the backports repository.  The same version of the Debian package may not be built with the same libc6, for example.  Backports are the source for that package compiled in an ubuntu environment.

---

### Post by Takis on 2005-08-02
I wonder. Would it be an idea to have a footprint on Ubuntu repositories that identifies them as Ubuntu-specific, and have Synaptic warn you if you've included a repo that could cause problems? Obviously it'd have the "yes, I know what I'm doing" checkbox but just as a reminder for a question that's come up more than a couple of times on these forums.

My two cents.

---

### Post by az on 2005-08-02
You do get a warning the first time you enable a non-main repository.

---

### Post by Takis on 2005-08-02
Oh. We're in agreement then.

...

(climbs back into tiny box in the corner)

---

### Post by eeried on 2005-08-02
many thanks for all the replies that have made things clearer for me.

I still have a question though concerning the latest problem with Mozilla-Firefox: Was this a problem with the package or with the new version of Firefox by the Mozilla Foundation? I read the annoucement on this forum but it wasn't very clear to me. 

Actually I installed the tar.gz binary from mozilla.org which works fine in Ubuntu!

I know the Mozilla suite straight from the Mozilla Foundation was quickly replaced by 1.7.11 after  1.7.10 was found faulty.

Cheers

---

### Post by az on 2005-08-02
[QUOTE=craigevil] The Ubuntu way gives you stable up to date packages without the worry of having an unstable system like Sid. Never really thought about it that way.
[/QUOTE]


Wait.  Mepis does not support their packages?  They just use unstable Sid packages?

---

