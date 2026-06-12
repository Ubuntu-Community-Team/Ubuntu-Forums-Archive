---
title: "resize a file?"
date: 2007-04-25
forum: General Help
---

### Post by vaskeli on 2007-04-25
Is there a program that will resize a file to whatever size I specify. For example, a 7MB file becomes exactly 4699979776 bytes.

i think what i'm looking for is an app that preforms a truncate command.

---

### Post by Pox on 2007-04-26
Be easy enough to do in perl... although the example you give isn't truncation, it's extension.  By the way, why are you trying to make a perfectly DVD-sized file? >_>

Anyway, I'd try something like this in perl:

```

#!/usr/bin/perl

use strict;
use warnings;

my ($file, $length, $outfile) = @ARGV;
my $padding = " "; #character to pad extra space with
my $contents;

{
    local $/ = undef;
    open FILE, "<$file";
    $contents = <FILE>; #Read entire file to string
    close FILE;
}

$contents .= $padding while length $contents < $length; # extend
$contents = substr($contents, 0, $length) if length $contents > $length; # truncate
open FILE, ">$outfile";
print FILE, $contents;
close FILE;

exit;

```

Dunno if it'll handle a 4GB string though. ;)

---

### Post by vaskeli on 2007-04-26
thanks. I ended up using a ruby script to do the same thing: truncate(file.iso, 4699979776)

as for why, i needed to burn a setup disc for a modded game console. I had a windows .bat script that used one program to generate an iso, then used another to extend it's file size to 4 gigs. wine was able to run the generator, but it crashed when trying to resize the file, thus my problem. the console only recognizes discs of certain sizes, which is why it had to be a specific length.

---

### Post by az on 2007-04-26
use dd.


man dd

---

