---
title: "error with perl cpan"
date: 2006-11-22
forum: General Help
---

### Post by harm_kabisa on 2006-11-22
Hi all,

I'm having trouble with my Perl installation on Edgy Eft Server:

root@pluton:~# perl -MCPAN -e shell
String found where operator expected at /usr/share/perl/5.8/ExtUtils/MakeMaker.pm line 949, near "push @m, join ""
  (Might be a runaway multi-line "" string starting on line 947)
        (Missing semicolon on previous line?)
String found where operator expected at /usr/share/perl/5.8/ExtUtils/MakeMaker.pm line 951, near "return join ""
  (Might be a runaway multi-line "" string starting on line 950)
        (Missing semicolon on previous line?)
String found where operator expected at /usr/share/perl/5.8/ExtUtils/MakeMaker.pm line 953, near "return ""
  (Might be a runaway multi-line "" string starting on line 951)
        (Missing semicolon on previous line?)
Scalar found where operator expected at /usr/share/perl/5.8/ExtUtils/MakeMaker.pm line 953, near "return "$v"
Global symbol "@m" requires explicit package name at /usr/share/perl/5.8/ExtUtils/MakeMaker.pm line 944.
Global symbol "@neat" requires explicit package name at /usr/share/perl/5.8/ExtUtils/MakeMaker.pm line 944.
Global symbol "@m" requires explicit package name at /usr/share/perl/5.8/ExtUtils/MakeMaker.pm line 944.
syntax error at /usr/share/perl/5.8/ExtUtils/MakeMaker.pm line 945, near "push @m, "["
  (Might be a runaway multi-line "" string starting on line 944)
Global symbol "$elem" requires explicit package name at /usr/share/perl/5.8/ExtUtils/MakeMaker.pm line 945.
Global symbol "@neat" requires explicit package name at /usr/share/perl/5.8/ExtUtils/MakeMaker.pm line 945.
Global symbol "@m" requires explicit package name at /usr/share/perl/5.8/ExtUtils/MakeMaker.pm line 947.
Global symbol "@neat" requires explicit package name at /usr/share/perl/5.8/ExtUtils/MakeMaker.pm line 949.
Global symbol "@m" requires explicit package name at /usr/share/perl/5.8/ExtUtils/MakeMaker.pm line 949.
Global symbol "@m" requires explicit package name at /usr/share/perl/5.8/ExtUtils/MakeMaker.pm line 951.
/usr/share/perl/5.8/ExtUtils/MakeMaker.pm has too many errors.
Compilation failed in require at /usr/share/perl/5.8/CPAN.pm line 16.
BEGIN failed--compilation aborted at /usr/share/perl/5.8/CPAN.pm line 16.
Compilation failed in require.
BEGIN failed--compilation aborted.
root@pluton:~# 

I have tried everything i can think of. 

Can somebody please help?

---

### Post by harm_kabisa on 2006-11-23
Nobody has seen this before?
Do I maybe have to reinstall some packages? I really need some help here.

---

### Post by harm_kabisa on 2006-11-23
Just found it, i had to reinstall my perl modules package:

apt-get install --reinstall perl-modules

Very weird, but now it works...

---

