---
title: "A bit of Bash scripting help, please?"
date: 2008-03-18
forum: General Help
---

### Post by Phlod on 2008-03-18
I have some very large directories, containing over 32,000 files.  I would like to be able to break this bulk up into folders with only 3000 files in them each.  The kicker is that I need for the files that get put into the directories to be moved in Ascending chronological order, (meaning that it starts moving the oldest files first, and works its way up to the newest.)  It doesn't much matter what the directories are called, as long as they are named in a sequential order.

Any advice, or even a working script would be very appreciated.  Thank you all in advance.

--Phlod

---

### Post by SpaceTeddy on 2008-03-18
it's not really a shell script - but i am more comforable in perl... so here is a script that load all files in the currently active directory, then sorts them ascending by time (oldest first) and moves them into subdirectories. 
there are a few gotchas tho...
1.) call the file move.pl - otherwise it will also move itself !
2.) $threshold needs to be adjusted to the number of files per directory
3.) you wanna test it BEFORE you use it on anything imporant :)

```
#!/usr/bin/perl -w
use File::Copy;
use strict;

# load all files in basedir into the @files array
my @files = <*>;

# sort the files by time (oldest first)
my @timed_files = sort{ -M $b <=> -M $a } @files;

#files per dir
my $threshold = 3;

my $dir_prefix = "car";

#number of starting dir - dirs are called auto%n -so auto1, auto2, auto3 - etc
my $dir = 1;

#counter
my $i = 0;

#first dir
mkdir $dir_prefix.$dir;

#do the moving
foreach my $file (@timed_files) {
  if ($file ne "move.pl"){
    print "moving file to $dir_prefix$dir\n";
    move($file, $dir_prefix.$dir."/".$file);

    $i++;
    #check for overflow - if so, create a new dir and move everything there
    if ($i % $threshold == 0) {
      $dir++;
      mkdir $dir_prefix.$dir;
    }
  }
}
```

let me know if it worked :)

---

