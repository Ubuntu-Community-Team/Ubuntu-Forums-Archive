---
title: "ldconfig won't find libs that don't start with 'lib'"
date: 2008-06-19
forum: General Help
---

### Post by MarkHowells on 2008-06-19
Hi.

I've installed an rpm (using alien) and have patched the ld.so.conf file (well, I've created a new file that's included...). 

ldconfig runs fine and scans the required directories but it doesn't find .so files that don't begin with the string "lib". Is this by design or is it something I can control. I'd rather not go round renaming the distrib. files unless I have to...

I'm wondering if there's a flag I can set on ldconfig or in the ld.so.conf... 

Failing that, can I do it on the ldconfig command line somehow (or even individually specify the libraries (using '-l' ? not documented but 'for experts only...' according to man ldconfig)

Thanks

Mark

---

### Post by geirha on 2008-06-19
Seems this is by design, I searched for "lib" in the sources of glibc and found:
glibc-2.7/elf/ldconfig.c:
```

      if (((strncmp (direntry->d_name, "lib", 3) != 0
        && strncmp (direntry->d_name, "ld-", 3) != 0)
       || strstr (direntry->d_name, ".so") == NULL)
      && (
#ifdef _DIRENT_HAVE_D_TYPE
          direntry->d_type == DT_REG ||
#endif
          !is_hwcap_platform (direntry->d_name)))
    continue;

```
Which suggests that the library must start with "lib" or "ld-", and contain ".so" in order for it to be processed as a library.

Also, the manpage of ldconfig and ld-linux specify
```

       lib*.so.version     shared libraries
       lib*.so*            shared libraries

```
respectively in their FILES-sections.

Renaming the libraries sounds like the best solution to me ...

---

### Post by MarkHowells on 2008-06-20
I guess you're right. Rename script coming up ...

Cheers

Mark

---

