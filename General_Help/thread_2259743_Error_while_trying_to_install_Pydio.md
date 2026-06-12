---
title: "Error while trying to install Pydio"
date: 2015-01-06
forum: General Help
---

### Post by Andy_Mummau on 2015-01-06
As part of the installation process, mcrypt for PHP needs installed. It finishes, but fails on this package with the following error. I was having some trouble with corrupted packages earlier, but seemed to resolve most of the issues by purging and reinstalling. Any suggestions/insights would be much appreciated.

```
/sbin/ldconfig.real: /usr/lib/i386-linux-gnu/libtalloc.so.2.0.7 is not an ELF file - it has the wrong magic bytes at the start.

```

[IMG]http://i.imgur.com/znoEDQA.png[/IMG]

---

### Post by steeldriver on 2015-01-06
I don't know if it's significant, but libtalloc.so.2.0.7 would appear to be the wrong library version for 14.04, I would have expected it to be 2.1.0

[http://packages.ubuntu.com/trusty/i386/libtalloc2/filelist](http://packages.ubuntu.com/trusty/i386/libtalloc2/filelist)

What does

```

dpkg -l libtalloc2

```

say?

---

### Post by Andy_Mummau on 2015-01-06
Here's the output. Seems like the right version.

```

andy@MummauNet:~$ dpkg -l libtalloc2
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                     Version           Architecture      Description
+++-========================-=================-=================-=====================================================
ii  libtalloc2:i386          2.1.0-1           i386              hierarchical pool based memory allocator
andy@MummauNet:~$
```

---

### Post by steeldriver on 2015-01-06
Hmm... I  think at this point I would be looking at

```

find /usr/lib/i386-linux-gnu/ -name 'libtalloc*'

```
to see exactly which libs are there; and

```

dpkg -L libtalloc2 | grep '/usr/lib'

```
(upper case L) to see what files the package thinks it owns there; and

```

dpkg -S /usr/lib/i386-linux-gnu/libtalloc.so.2.0.7

```
to see which package thinks it owns the problem file

---

### Post by Andy_Mummau on 2015-01-06
This is interesting:

[IMG]http://i.imgur.com/5WGwUhO.png[/IMG]

---

### Post by steeldriver on 2015-01-07
Oops I meant to suggest 

```

find /usr/lib/i386-linux-gnu/ -name 'libtalloc*' [B]-ls
[/B]
```so that you also see which so.x.x.x is actually linked as the main .so

Nevertheless, my suspicion is that libtalloc.so.2.0.7 is a leftover from a previous version that did not get properly removed (and hence is corrupted) - did you upgrade your system from an earlier release (such as 12.04)? 

It may be necessary to manually remove it - not something I'd normally suggest with system files, since it usually messes with the package management system, however in this case it looks like the file is already off the radar as far as dpkg is concerned. Let's just confirm the linkage first though.

---

### Post by Yellow Pasque on 2015-01-07
@steeldriver: did you mean dpkg-**query** -S

---

### Post by steeldriver on 2015-01-07
@Temüjin they are synonymous afaik

```

       dpkg can also be used as a front-end to dpkg-deb(1) and  dpkg-query(1).
       The list of supported actions can be found later on in the ACTIONS sec&#8208;
       tion. [B]If any such action is encountered  dpkg  just  runs  dpkg-deb  or
       dpkg-query with the parameters given to it[/B], but no specific options are
       currently passed to them, to use any such option the back-ends need  to
       be called directly.

```

---

### Post by Yellow Pasque on 2015-01-07
I've learned my fact for the day. I'm going back to bed :)

---

### Post by Andy_Mummau on 2015-01-07
Even still:

Looks like it's pointing to the right, new version. It doesn't seem 2.0.7 is associated with anything.

```

andy@MummauNet:~$ find /usr/lib/i386-linux-gnu/ -name 'libtalloc*' -ls
3409593    0 lrwxrwxrwx   1 root     root           18 Oct 21  2013 /usr/lib/i386-linux-gnu/libtalloc.so.2 -> libtalloc.so.2.1.0
3413498   48 -rw-r--r--   1 root     root        46652 Oct 17  2011 /usr/lib/i386-linux-gnu/libtalloc.so.2.0.7
3409592   44 -rw-r--r--   1 root     root        42416 Oct 21  2013 /usr/lib/i386-linux-gnu/libtalloc.so.2.1.0

```

This "server" has been my machine to experiment with Ubuntu (and Linux), so I'm trying to learn to fix everything when problems come up rather than a fresh install. (Best way to learn!)

It was originally running 12.04, then had a bad hard drive. Replaced the drive and cloned everything over, and repaired many problem spots (and files/packages) afterwards. It's quite possible this is one of the things that got messed with during the upgrade to 14.04.

I didn't remove anything yet.

---

### Post by Yellow Pasque on 2015-01-07
If it doesn't belong to a package, then it should not be in /usr/lib/
I'm guessing it's not only a leftover file, but also a corrupt one based on the message.  I would back it up and move it out of the way:
```
cd /usr/lib/i386-linux-gnu
sudo tar czf oldlibtalloc.tar.gz libtalloc.so.2.0.7
sudo rm libtalloc.so.2.0.7
sudo mv oldlibtalloc.tar.gz ~/
sudo ldconfig -v | grep talloc
sudo dpkg --configure -a
```
You should be good to go after that.

---

### Post by Andy_Mummau on 2015-01-08
That worked: no more errors when installing Pydio and it's dependencies.

No I just have to figure out what else I need to get PHP to detect mcrypt, but that's another adventure.

Thanks much for the help.

---

