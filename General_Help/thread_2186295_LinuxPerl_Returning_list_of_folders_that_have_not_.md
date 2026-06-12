---
title: "Linux/Perl Returning list of folders that have not been modified for over x minutes"
date: 2013-11-06
forum: General Help
---

### Post by AshPat on 2013-11-06
I have a directory that has multiple folders. I want to get a list of the names of folders that have not been modified in the last 60 minutes.
The folders will have multiple files that will remain old so I can't use -mmin +60.

I was thinking I could do something with inverse though. Get a list of files that have been modified in 60 minutes -mmin -60 and then output the inverse of this list.

Not sure to go about doing that or if there is a simpler way to do so?


This is what I have so far to get the list of folders

'find /path/to/file -mmin -60 | sed 's/\/path\/to\/file\///' | cut -d "/" -f1 | uniq'

Above will give me just the names of the folders that have been updated.

---

### Post by drmrgd on 2013-11-06
I'm probably being dense here, but if you look for files that have been modified less than 60 minutes ago and select those that don't match, isn't that going to be the same as just matching those that have been modified more than 60 minutes ago directly?  Also, I'm a little unclear on whether you want files that have been modified more than 60 minutes ago or directories that have been modified less than 60 minutes ago; you seem to go between the two in your question.

At any rate, since you asked about a perl solution, here's a quick and dirty script that will give you a list of files that have been modified less than 60 minutes ago:

```

#!/usr/bin/perl
use warnings;
use strict;


my $search_dir = shift;
opendir( my $dir, $search_dir ) || die "Can't read the directory '$search_dir': $!";
my @files = readdir($dir);


my $now = time;


my @recent_files;
for my $file ( @files ) {
    next if $file =~ /^\.+/;
    my $mtime = ( stat $file )[9];
    push( @recent_files, $file ) if ( ($now-$mtime) < 60 );
}


print "Files modified less than 60 minutes ago:\n";
print "\t$_\n" for @recent_files

```

Just run it like:

```

perl recently_mod_files.pl <directory to look in>

```

I haven't considered checking whether or not the target is a directory or a file with that script (that logic can be added), and I haven't considered recursion (i.e. this will only query the directory that's been passed in and not go any deeper).  

Hope that helps put you on the right track.

---

