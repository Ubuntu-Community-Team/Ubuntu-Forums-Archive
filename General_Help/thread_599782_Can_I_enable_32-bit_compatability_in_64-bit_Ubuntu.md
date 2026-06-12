---
title: "Can I enable 32-bit compatability in 64-bit Ubuntu 7.10 ?"
date: 2007-11-01
forum: General Help
---

### Post by adamh128 on 2007-11-01
Hi,

I have just jumped ship from Mandriva to Ubuntu and I must say I do like it :-)

However, I have installed the 64-bit edition (7.10), but I'm having problems running some of my old 32-bit apps. So I was wondering, is there a way of enabling 32-bit compatability within 64-bit editions of linux (like Sun did back in the days when they first introduced Solaris, they supported the old SunOS binaries too)?

Thanks.

---

### Post by rsambuca on 2007-11-01
The apps in the repositories have been compiled to run on 64-bit, and 'some' others can be --force installed and still work.  What programs are you having problems with?

---

### Post by aidanr on 2007-11-01
sudo apt-get install ia32-libs

---

### Post by rsambuca on 2007-11-01
> **aidanr said:**
> sudo apt-get install ia32-libs

That won't work for every package, by the way.

Here is [another thread]("http://ubuntuforums.org/showthread.php?t=563838") on the exact same topic.

---

### Post by jshanks on 2007-11-01
This is from memory, but I think it's just linux32 <appname>.

---

### Post by adamh128 on 2007-11-01
> **rsambuca said:**
> The apps in the repositories have been compiled to run on 64-bit, and 'some' others can be --force installed and still work.  What programs are you having problems with?

They are specialist formal methods tools and unfortunatly I do not have access to the source :-(

I'm hoping I can get them to work, otherwise I'll have to re-install the 32-bit edition.

---

### Post by adamh128 on 2007-11-02
wahoo, it's working 8)

First I tried [FONT="Courier New"]linux32 <appname>[/FONT] which didn't work at all. Then I installed ia32-libs and everything worked.

Many thanks for all the help, I'm a happy man now.

---

### Post by Rog-Mahal on 2007-11-05
apparently by installing linux32 you have to remove the ubuntu-minimal package, which seems pretty fundamental. Isn't that dangerous? anybody have any recommendations?

---

