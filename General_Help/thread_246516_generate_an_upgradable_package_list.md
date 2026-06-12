---
title: "generate an upgradable package list"
date: 2006-08-29
forum: General Help
---

### Post by fergus on 2006-08-29
Does anyone know a command line way to generate a list of upgradable packages?  I am trying to setup some server scripts that will email me when new packages are available for update.  But I can't seem to find the right command to just generate that list.  Any help would be apprciated.

fergus

---

### Post by flankker on 2006-08-29
hi, not sure if this is what u are looking for but maybe it will help: [http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

it tells u how to get a list of all the packages installed in your comp.

---

### Post by nicolai.rostov on 2007-09-16
# apt-get --simulate upgrade
nr

---

### Post by nicolai.rostov on 2007-09-17
This rather cumbersome perl script prints the upgradable packages list.
Wouldn't it be better to just dpkg in a single command line? Any ideas?
nr.

```
#!/usr/bin/perl
# # print an upgradable packages list

use warnings;
use strict;

my $print  = 0;
my $before = 'The following packages will be upgraded:';
my $after  = '^\d.+?upgraded';

open PIPE, 'sudo $(which apt-get) --simulate --verbose-versions upgrade | ';

while (<PIPE>)
{
	/^$before/ and $print = 1 and next;
	last if /$after/;
	next if $print == 0;
	s/^\s+//g;
	s/\s+/\t/;
	print;
}

close PIPE;

exit ;
```

---

