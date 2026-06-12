---
title: "Difference between 'test' and '[[ ]]'"
date: 2012-12-30
forum: General Help
---

### Post by hughh on 2012-12-30
When I run the following on a *Terminal* command line, it works as I expect—

```
~$ if [[ 0 -eq 0 ]]; then touch /tmp/commandline-if; fi
~$ ls -alF /tmp/commandline-if
-rw-rw-r-- 1 hugh hugh 0 Dec 30 17:43 /tmp/commandline-if
```When I add the following as a one-time *cron* job via the *Scheduled tasks* application, it does ***not*** work as I expect—

```
if [[ 0 -eq 0 ]]; then touch /tmp/cron-if; fi
```This does ***not*** result in the specified file being created—

```
~$ ls -alF /tmp/cron-if
ls: cannot access /tmp/cron-if: No such file or directory
```But if I change all occurrences of '[[ ]]' to a *test* command, everything works as expected. Adding

```
if test 0 -eq 0; then touch /tmp/cron-if; fi
```as a one-time *cron* job ***does*** indeed create the specified file—

```
ll /tmp/cron-if
-rw-rw-r-- 1 hugh hugh 0 Dec 30 20:31 /tmp/cron-if
```Is this a bug?  Or am I missing something?

---

### Post by steeldriver on 2012-12-30
maybe because the [[ ... ]] extended test is a bashism, and cron jobs are run in /bin/sh which is symlinked to the dash shell by default?

The single bracket form [ 0 -eq 0 ] should work I think - in fact since you are using the -eq integer test operator it would be more natural, imho (people tend to use ==, !=, < > operators with [[ ... ]] since it supports them) 

[http://mywiki.wooledge.org/Bashism](http://mywiki.wooledge.org/Bashism)

---

### Post by hughh on 2012-12-30
> **steeldriver said:**
> maybe because the [[ ... ]] extended test is a bashism, and cron jobs are run in /bin/sh which is symlinked to the dash shell by default?

Ah, good point!  I didn't think about that.

> The single bracket form [ 0 -eq 0 ] should work I think - in fact since you are using the -eq integer test operator it would be more natural, imho (people tend to use ==, !=, < > operators with [[ ... ]] since it supports them)'[ ... ]' does work.  Also '==' works as a test for integer equality with both *bash* and *sh*. I guess I've always used '-eq' (and similar variants) because that's what 'help test' shows as the way to do it.

> [http://mywiki.wooledge.org/Bashism](http://mywiki.wooledge.org/Bashism)Good: I'll use this to make my scripts more POSIX compliant.

Thanks for answering my question and clearing up my confusion!

---

### Post by HomelandSecurity on 2012-12-30
> **steeldriver said:**
> maybe because the [[ ... ]] extended test is a bashism, and cron jobs are run in /bin/sh which is symlinked to the dash shell by default?

The single bracket form [ 0 -eq 0 ] should work I think - in fact since you are using the -eq integer test operator it would be more natural, imho (people tend to use ==, !=, < > operators with [[ ... ]] since it supports them) 

[http://mywiki.wooledge.org/Bashism](http://mywiki.wooledge.org/Bashism)

I disagree:
-eq is used to compare number
== and = is used to compare strings!

---

### Post by HomelandSecurity on 2012-12-30
there is a huge dif between [] and [[]]

[http://tldp.org/LDP/abs/html/testconstructs.html#DBLBRACKETS](http://tldp.org/LDP/abs/html/testconstructs.html#DBLBRACKETS)

try to change the first part of the comparison with a variable (with an integer value added to it). and repeat the condition.

---

### Post by Derek Karpinski on 2012-12-31
if it works in bash, then just create a bash script that gets called by cron.

---

