---
title: "which packages install files in /usr/local?"
date: 2019-10-03
forum: General Help
---

### Post by Skaperen on 2019-10-03
i'd like to get a list of which packages install files in [COLOR=#0000cd][FONT=courier new]**/usr/local**[/FONT][/COLOR].  does anyone know a way to do that?

---

### Post by SeijiSensei on 2019-10-03
If you compile GNU and other compliant software, it will install to /usr/local by default.  "sudo make install" will put the binaries in /usr/local/bin/ or /usr/local/sbin/ depending on the type of program it is.  Libraries will end up in /usr/local/lib/ and configuration files in /usr/local/etc/.  ldconfig looks in /usr/local/lib/ for libraries by default.

No packages installed from the repositories will install anything to /usr/local.  That's true on RedHat-flavored systems as well.

I put administrative scripts that I write in /usr/local/sbin/.

---

### Post by TheFu on 2019-10-03
+1 to what SeijiSensei said.

/usr/local/ is maintained by the local admin of the system.  Anything the local admin wants there can go there.  I put scripts, locally compiled stuff, backup/restore procedures there.  I always backup /usr/local/ and it is one of the first places restored to a new system that is meant for the same purpose.  Of course, the CPU architecture matters for binary compatibility.  Scripts are almost always safe. I install local perl modules from outside the package manager, but compatible with the OS perl into /usr/local/lib/perl5/  My PERL5LIB environment variable includes that dir.

---

### Post by Skaperen on 2019-10-04
many package files do show up there.  i will have to figure out what i have for now.  at least some came from [COLOR=#006400][FONT=courier new]**PyPi**[/FONT][/COLOR], maybe all.

i formerly put files i developed into [COLOR=#0000cd][FONT=courier new]**/usr/local**[/FONT][/COLOR].  but my install system needs directories of its own so it can start empty.  so i have created a new branch (and a spare for backup) named [COLOR=#0000cd][FONT=courier new]**/usr/host**[/FONT][/COLOR] and use [COLOR=#0000cd][FONT=courier new]**/usr/host/bin**[/FONT][/COLOR], [COLOR=#0000cd][FONT=courier new]**/usr/host/lib**[/FONT][/COLOR], and [COLOR=#0000cd][FONT=courier new]**/usr/host/sbin**[/FONT][/COLOR] a lot.  the spare is [COLOR=#0000cd][FONT=courier new]**/usr/site**[/FONT][/COLOR] which, for now, is a replica of [COLOR=#0000cd][FONT=courier new]**/usr/host**[/FONT][/COLOR].

there have been some funny things going on in [COLOR=#0000cd][FONT=courier new]**/usr/local**[/FONT][/COLOR] and i have been on the watch.

```

lt2a/forums /home/forums 18> ls -1 /usr/host/bin|wc -l
589
lt2a/forums /home/forums 19>

```

---

### Post by SeijiSensei on 2019-10-04
I don't use PyPi, but I'm nearly certain that no packages from the Ubuntu repositories ever install anything in /usr/local/.

---

### Post by Skaperen on 2019-10-04
that could be, but quite a while back, before i ever used PyPi, i broke something when my script removed a directory in [COLOR=#0000cd][FONT=courier new]**/usr/local**[/FONT][/COLOR].  i have since changed the script to apply to [COLOR=#0000cd][FONT=courier new]**/usr/host**[/FONT][/COLOR] and move the directory to its name with ".old" appended.  i will try to figure out what all is installed in [COLOR=#0000cd][FONT=courier new]**/usr/local**[/FONT][/COLOR] tonight.

---

### Post by mc4man on 2019-10-04
No Ubuntu repo packages ever installed to /usr/local
Browse /usr/local/, easy to see what's installed..

---

