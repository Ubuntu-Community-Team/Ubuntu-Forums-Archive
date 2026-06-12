---
title: "Trouble installing IPTables::IPv4"
date: 2005-06-20
forum: General Help
---

### Post by SodomizedPeanut on 2005-06-20
Hi. I'm having trouble installing IPTables::IPv4, which I want to do in order to use linblock.pl. Please bear in mind I'm quite inexperienced with linux, and that I have a very poor understanding of how Perl works. I've downloaded the .tar from CPAN, and unzipped it. I did 'perl Makefile.PL' and 'make' and then 'make test'. I get the following

> make -C modules/ all INSTALL_DIR=/usr/local/lib/IPTables-IPv4
make[1]: Entering directory `/home/jonathan/IPTables-IPv4-0.98/modules'
Module build complete.
make[1]: Leaving directory `/home/jonathan/IPTables-IPv4-0.98/modules'
PERL_DL_NONLAZY=1 IPT_MODPATH=/home/jonathan/IPTables-IPv4-0.98/modules /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/00save_current_ruleset....Useless use of a variable in void context at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4.pm line 5.
Use of uninitialized value in <HANDLE> at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4/Toplevel.pm line 50.
readline() on unopened filehandle at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4/Toplevel.pm line 50.
Use of uninitialized value in ref-to-glob cast at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4/Toplevel.pm line 52.
skipped
        all skipped: no reason given
t/01simple_manip............Useless use of a variable in void context at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4.pm line 5.
t/01simple_manip............dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED tests 1-14
        Failed 14/14 tests, 0.00% okay
t/03admin...................Useless use of a variable in void context at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4.pm line 5.
t/03admin...................dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED tests 1-45
        Failed 45/45 tests, 0.00% okay
t/03modules.................Useless use of a variable in void context at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4.pm line 5.
t/03modules.................dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED tests 1-11
        Failed 11/11 tests, 0.00% okay
t/04append..................Useless use of a variable in void context at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4.pm line 5.
t/04append..................dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED tests 1-20
        Failed 20/20 tests, 0.00% okay
t/05insert..................Useless use of a variable in void context at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4.pm line 5.
t/05insert..................dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED tests 1-28
        Failed 28/28 tests, 0.00% okay
t/07flush...................Useless use of a variable in void context at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4.pm line 5.
t/07flush...................dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED tests 1-9
        Failed 9/9 tests, 0.00% okay
t/08replace.................Useless use of a variable in void context at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4.pm line 5.
t/08replace.................dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED tests 1-10
        Failed 10/10 tests, 0.00% okay
t/14badtarget...............Useless use of a variable in void context at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4.pm line 5.
Useless use of string in void context at t/14badtarget.t line 23.
t/14badtarget...............dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED tests 1-7
        Failed 7/7 tests, 0.00% okay
t/15manyrules...............Useless use of a variable in void context at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4.pm line 5.
t/15manyrules...............dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED tests 1-29
        Failed 29/29 tests, 0.00% okay
t/16manyrules2..............Useless use of a variable in void context at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4.pm line 5.
t/16manyrules2..............dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED tests 1-20
        Failed 20/20 tests, 0.00% okay
t/18rename..................Useless use of a variable in void context at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4.pm line 5.
t/18rename..................dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED tests 1-17
        Failed 17/17 tests, 0.00% okay
t/19listports...............Useless use of a variable in void context at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4.pm line 5.
t/19listports...............dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED tests 1-7
        Failed 7/7 tests, 0.00% okay
t/24delete..................Useless use of a variable in void context at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4.pm line 5.
t/24delete..................dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED tests 1-19
        Failed 19/19 tests, 0.00% okay
t/56speed...................Useless use of a variable in void context at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4.pm line 5.
Name "main::rules" used only once: possible typo at t/56speed.t line 42.
Name "main::chains" used only once: possible typo at t/56speed.t line 76.
t/56speed...................dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED tests 1-7
        Failed 7/7 tests, 0.00% okay
t/59numberproto.............Useless use of a variable in void context at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4.pm line 5.
t/59numberproto.............dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED tests 1-2
        Failed 2/2 tests, 0.00% okay
t/99restore_ruleset.........Useless use of a variable in void context at /home/jonathan/IPTables-IPv4-0.98/blib/lib/IPTables/IPv4.pm line 5.
Name "main::rules" used only once: possible typo at t/99restore_ruleset.t line 12.
skipped
        all skipped: no reason given
Failed Test        Stat Wstat Total Fail  Failed  List of Failed
-------------------------------------------------------------------------------
t/01simple_manip.t    1   256    14   27 192.86%  1-14
t/03admin.t           1   256    45   89 197.78%  1-45
t/03modules.t         1   256    11   21 190.91%  1-11
t/04append.t          1   256    20   39 195.00%  1-20
t/05insert.t          1   256    28   55 196.43%  1-28
t/07flush.t           1   256     9   17 188.89%  1-9
t/08replace.t         1   256    10   19 190.00%  1-10
t/14badtarget.t       1   256     7   13 185.71%  1-7
t/15manyrules.t       1   256    29   57 196.55%  1-29
t/16manyrules2.t      1   256    20   39 195.00%  1-20
t/18rename.t          1   256    17   33 194.12%  1-17
t/19listports.t       1   256     7   13 185.71%  1-7
t/24delete.t          1   256    19   37 194.74%  1-19
t/56speed.t           1   256     7   13 185.71%  1-7
t/59numberproto.t     1   256     2    3 150.00%  1-2
2 tests skipped.
Failed 15/17 test scripts, 11.76% okay. 245/245 subtests failed, 0.00% okay.
make: *** [test_dynamic] Error 255


I get the same problem when I try to use the CPAN command to install the module. What's going on?

---

### Post by tehbizz on 2005-08-04
I was having the same problem and this is what fixed it for me:

```

$itpables -N bad_tcp_packets // create a fake ruleset to 'trick' IPTables::IPv4
$cpan -i LWP Hi::Res Bundle::CPAN // LWP is needed for a ton of stuff, good to have installed.  Hi::Res seems to be an unstated dep and Bundle::CPAN ensures that CPAN is up-to-date
$cpan -i IPTables::IPv4 // finally install

```

And I finally ended up with:
```

Running make install
make -C modules/ all INSTALL_DIR=/usr/local/lib/IPTables-IPv4
**....output truncated...**
 /usr/bin/make install UNINST=1 -- OK
$root@mastershake:/home # 

```

---

