---
title: "Wordwrap toggle not functioning in less"
date: 2013-12-25
forum: General Help
---

### Post by apollothethird on 2013-12-25
Has anyone noticed that the wordwrap is not functioning in the Ubuntu 13.10 version of less?

The following gives me the same type of listings without chopped lines:

```

$ less -S /var/log/syslog
$ less /var/log/syslog

```

While using both I tried as per the manual to toggle chopping lines using the man page description:

```

-S or --chop-long-lines
              Causes  lines longer than the screen width to be chopped (truncated) rather than wrapped.  That is, the portion of
              a long line that does not fit in the screen width is not shown.  The default is to wrap long lines; that is,  dis&#8208;
              play the remainder on the next line.


```

Having this toggle functionality is a great convenience.  Hopefully someone can help me to identify if something has changed where there might be a different way to enable this functionality.

If it's a glitch in the current version and there is a patch on the developers repository, can someone please share.

Thanks!

-- L. James

-- 
L. D. James
[EMAIL="ljames@apololo3.com"]ljames@apololo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by apollothethird on 2013-12-27
> **apollothethird said:**
> Has anyone noticed that the wordwrap is not functioning in the Ubuntu 13.10 version of less?

The following gives me the same type of listings without chopped lines:

```

$ less -S /var/log/syslog
$ less /var/log/syslog

```

While using both I tried as per the manual to toggle chopping lines using the man page description:

```

-S or --chop-long-lines
              Causes  lines longer than the screen width to be chopped (truncated) rather than wrapped.  That is, the portion of
              a long line that does not fit in the screen width is not shown.  The default is to wrap long lines; that is,  dis&#8208;
              play the remainder on the next line.


```

Having this toggle functionality is a great convenience.  Hopefully someone can help me to identify if something has changed where there might be a different way to enable this functionality.

If it's a glitch in the current version and there is a patch on the developers repository, can someone please share.

Thanks!


For anyone having a problem with LESS or another other linux tool who might discover this thread, I'm sharing the resolution:

[http://www.linuxquestions.org/questions/ubuntu-63/wordwrap-toggle-not-functioning-in-less-4175489153/#post5087452](http://www.linuxquestions.org/questions/ubuntu-63/wordwrap-toggle-not-functioning-in-less-4175489153/#post5087452)

I would like to thank anyone who read this thread and powdered possible culprits.

Hope someone would benefit from this experience.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

