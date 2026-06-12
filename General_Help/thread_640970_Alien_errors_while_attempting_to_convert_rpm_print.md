---
title: "Alien errors while attempting to convert rpm printer drivers"
date: 2007-12-14
forum: General Help
---

### Post by bchandonnet on 2007-12-14
I am attempting to install drivers for my new Canon Pixma MP160.  Others have gotten it to work, but when I try to run the rpms through alien using this command:

** sudo alien -c cnijfilter-mp160-2.70-1.i386.rpm **

I get this error:

[B]Unpacking of 'cnijfilter-mp160-2.70-1.i386.rpm' failed at /usr/share/perl5/Alien/Package/Rpm.pm line 153.
[/B]
This is my first encounter with alien, and I'm not sure what to do.  I have tried another rpm and get the same error.

Any Ideas?

---

### Post by bchandonnet on 2007-12-15
If it helps anyone to know what the problem is, here are lines 153 and 154 from the rpm.pm script referenced in the error message.

[B]$this->do("rpm2cpio ".$this->filename." | (cd $workdir; cpio --extract --make-directories --no-absolute-filenames --preserve-modification-time) 2>&1")
		or die "Unpacking of '".$this->filename."' failed";[/B]

I hope someone else has had this issue and can help me, I need to get my printer running.

---

### Post by zvacet on 2007-12-15
```
sudo alien -d cnijfilter-mp160-2.70-1.i386.rpm
```

or you can do it without puting d

```
sudo alien cnijfilter-mp160-2.70-1.i386.rpm
```

---

