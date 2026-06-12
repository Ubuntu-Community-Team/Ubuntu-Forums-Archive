---
title: "CPAN Perl Problem Installing Date::Calc"
date: 2007-06-26
forum: General Help
---

### Post by jlr4u on 2007-06-26
I installed some Perl scripts for PPV with MythTV under Edgy, but with the new Festy load, I am having trouble with the CPAN scripts.


```
sudo -i
perl -MCPAN -e shell
```

```
cpan> install Date::Calc
cpan> install WWW::Mechanize
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Tue, 26 Jun 2007 11:09:00 GMT
WWW::Mechanize is up to date.
cpan> install HTML::TokeParser::Simple
HTML::TokeParser::Simple is up to date.
```

Now when I try to load Date::Calc I receive a  multitude of errors

```
install Date::Calc
```

The errors scroll off of the terminal -- 
Calc.c:2284: error: invalid type argument of ‘unary *’

Any Ideas on how to fix this.

---

### Post by tr333 on 2007-06-26
firstly, it's easier to start the cpan shell by using "sudo cpan" at the terminal prompt.  you might also want to consider installing the cpanplus shell (newer, and more features) with the "Bundle::CPANPLUS" package.

if you can't install a module via cpan, download the tgz archive from [http://search.cpan.org/~stbey/Date-Calc-5.4/Calc.pod]("http://search.cpan.org/~stbey/Date-Calc-5.4/Calc.pod") and install with:
```
$ perl Makefile.pl
$ make
$ make test
$ make install
```

don't forget about the "make test" as it will tell you any dependencies you have missing.

---

### Post by mohamedadaly on 2007-06-28
I had the same problem, but found on another forum that you can easily install this library using apt-get:


```
sudo apt-get install libdate-calc-perl
```

---

### Post by jlr4u on 2007-06-28
Thank You

```
sudo apt-get install libdate-calc-perl
```

Worked For me Also

---

