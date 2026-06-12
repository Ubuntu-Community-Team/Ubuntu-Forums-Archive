---
title: "half configured perl breaking apt and dpkg"
date: 2007-06-07
forum: General Help
---

### Post by moshy on 2007-06-07
Hello,
basically my problem is that for some reason perl is unconfigured - I think. I've got a bunch of dependency errors and ```
sudo apt-get install -f
``` results in
```

Do you want to continue [Y/n]? y
debconf: Perl may be unconfigured (Can't locate FileHandle.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
(Reading database ... 119817 files and directories currently installed.)
Unpacking gimp (from .../gimp_2.2.13-1ubuntu4.1_i386.deb) ...
Can't locate Exporter.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl . /usr/lib/dpkg) at /usr/share/perl/5.8/Carp.pm line 37.
Compilation failed in require at /usr/share/perl/5.8/warnings.pm line 11.
BEGIN failed--compilation aborted at /usr/share/perl/5.8/warnings.pm line 11.
Compilation failed in require at /usr/lib/dpkg/dpkg-gettext.pl line 3.
BEGIN failed--compilation aborted at /usr/lib/dpkg/dpkg-gettext.pl line 3.
Compilation failed in require at /usr/sbin/update-alternatives line 7.
dpkg: error processing /var/cache/apt/archives/gimp_2.2.13-1ubuntu4.1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/gimp_2.2.13-1ubuntu4.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
so I figure the problem is with perl being unconfigured, supported by
```

~$ dpkg -s perl
Package: perl
Status: install ok half-configured

```
and doing this won't work
```

~$ sudo dpkg --configure perl
Setting up perl (5.8.8-7build1) ...
Can't locate Exporter.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl . /usr/lib/dpkg) at /usr/share/perl/5.8/Carp.pm line 37.
blah..

```

So it seems I'm stuck in a state where because perl is unconfigured I can't fix my apt nor fix perl, and I have no idea.
I tried booting into recovery mode and doing fsck, which i know did something regarding all these *.pm files it can't seem to find in perl, but I can't remember what - sorry.


Does anyone have any ideas on how to fix this? Am I completely off the mark?

---

### Post by PointSource on 2007-06-07
Just a suggestion:
If you have an alternate install CD it has a repair option which allows a person to execute a shell in their broken system. I know your system isn't that far gone, but that environment may patch over the problems with your perl package allowing you to download and reinstall. Its worth a shot anyhow.

---

### Post by moshy on 2007-06-07
hey thanks, i didn't know anything about executing a new shell, but I ended up just manually copying the files it was after from the live cd to my system, which was a pain but did the trick.

---

