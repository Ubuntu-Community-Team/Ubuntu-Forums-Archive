---
title: "Problems with perlcc"
date: 2006-12-21
forum: General Help
---

### Post by geek_Man on 2006-12-21
Hi, I'm trying to make a perl file into an exe with perlcc. Whenever I try to, I get this:```
foo@foo-bar:~$ perlcc script.pl
Can't exec "cc": No such file or directory at /usr/bin/perlcc line 313.

```

Any ideas?

---

### Post by taurus on 2006-12-21
Looks like you need to install a gcc compiler...

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by geek_Man on 2006-12-21
A'right, I'll try that...

---

### Post by geek_Man on 2006-12-21
Okay, did that. Now what?

---

### Post by taurus on 2006-12-21
Now compile your perl program again!!!

```
perlcc script.pl
```

---

### Post by geek_Man on 2006-12-21
Okay, seems to work now, but I'm getting this error:```
foo@foo-bar:~$ perlcc script.pl
pcc3eEUe.c: In function ‘perl_init_aaaa’:
pcc3eEUe.c:6234: warning: this decimal constant is unsigned only in ISO C90
/usr/bin/ld: cannot find -lperl
collect2: ld returned 1 exit status

```

Could it be something wrong with the script?

---

### Post by taurus on 2006-12-21
Do you have perl on your machine?

```
whereis perl
```
If you don't, then you need to install it with

```
sudo aptitude install perl
```
and then compile it again...

---

### Post by geek_Man on 2006-12-21
Yeah, I got perl.

Hey, I gotta run, so don't think I gave up. I'll be back! (Hahahahaha!)

---

### Post by geek_Man on 2006-12-22
Okay, I'm back. Here's what I get: ```
techie@ubuntu-desktop:~$ whereis perl
perl: /usr/bin/perl /etc/perl /usr/lib/perl /usr/bin/X11/perl /usr/share/perl /usr/share/man/man1/perl.1.gz

```

---

### Post by taurus on 2006-12-22
What happens if you run these two commands?

```
sudo aptitude update
sudo aptitude install perl-base perl-module
```

---

### Post by geek_Man on 2006-12-22
It says no packages will be installed.

---

### Post by taurus on 2006-12-22
Maybe it's perl-modules!  Fire up synaptic and in the Search field, type **perl**...

---

### Post by geek_Man on 2006-12-22
Perl-modules appears to be installed.

---

### Post by taurus on 2006-12-22
Then it could be the script.pl!  What is it and where did you get it?  you may want to have a look at it...

```
more script.pl | more
(hit the space bar for the next 24 lines...)
```

---

### Post by geek_Man on 2006-12-22
Well, it's any script. But here's the one that I try to convert: ```
#!/usr/bin/perl

use warnings;

exec("xpenguins -s");

```

BTW, it's actually called xpenguins.pl. But, like I said, it gives me the same error with any script.

---

### Post by taurus on 2006-12-22
Hmm...  I tried to compile your script on RedHat Linux Enterprise 4.0 and Edgy and in Edgy, I got the same error message but on the RedHat system, it compiled file with a.out...

---

### Post by geek_Man on 2006-12-22
:-k 

Thought I'd be supportive ;) . But, seriously, that's strange...

---

### Post by wiretapp on 2007-03-01
sudo apt-get install libperl-dev

...enjoy.

---

