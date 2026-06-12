---
title: "Script won't launch Java app -- where is the Java executable stored??"
date: 2008-03-17
forum: General Help
---

### Post by will103 on 2008-03-17
Hi,

I am trying to launch a Java programme (Aduna Autofocus) from the supplied shell script. Trouble is that the script points to /bin when looking for the Java executable. However The Sun Java install on Ubuntu does not store the Java binary in that directory. On previous versions of Ubuntu I used to create a simlink to /bin for the Java executable, but on the Current Ubuntu I can no longer find the executable. Any ideas where it might be?

To be honest I have been unable to get anything written in Java to launch on the current Ubuntu.

Thanks in advance

will103

---

### Post by imbjr on 2008-03-17
Type
> whereis java
in a Terminal. That will give you a clue as to where Java has been installed.

---

### Post by will103 on 2008-03-17
Thanks for the advice. One question -- how does the whereis command differ from the slocate command? I tried slocate previously and it couldn's 'see' the executable.

Cheers

will103

---

### Post by imbjr on 2008-03-18
I honestly don't know. All I know is whereis has helped me in the past.

---

### Post by kpkeerthi on 2008-03-18
whereis command looks for executable in 'known' PATHs, paths were executables are usually stored, as specified in the $PATH environment variable.

locate searches for files from a indexed database that is usually updated periodically (manually & automcatically via system cron) with **updatedb** command.

---

### Post by will103 on 2008-03-28
Thanks for the update. I am still having problems though. Neither of these commands can find the executable. Bash gives me additional package options if I run:

java

At the Shell prompt. 

I will try one of these.

will103

---

### Post by ayampanggang on 2008-03-28
how about simply trying to execute "java progname" ?

---

### Post by will103 on 2008-03-28
Hi, I tried that, but java cannot be found and I am given a list of packages that contain it. 

Thanks

will103

---

