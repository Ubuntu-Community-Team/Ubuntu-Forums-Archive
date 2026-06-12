---
title: "Rsync issues with moved files"
date: 2008-05-12
forum: General Help
---

### Post by eeboy on 2008-05-12
I recently got rsync up and running to keep my share synchronized on a remote server. Everything is working great but I've caught one annoying issue. If I re-organize files on the source by moving them to another directory it always copies the moved file to the destination even though it already exists at the destination. What I'd like for it to do is simply perform a move operation. Some of these files are large and this unnecessary copy lengthens the backup time significantly. Any suggestions?

---

### Post by eeboy on 2008-05-12
If it helps... I run with the following options:

```
rsync -av --delete-after --stats --human-readable --modify-window=1 --exclude-from=/home/me/Scripts/rsyncexclude -e ssh /media/Shared/ me@mydomain.com:/home/me/backup/ > /home/me/Scripts/rsync-${TIMESTAMP}.log 2>&1
```

---

### Post by unutbu on 2008-05-12
Unfortunately, I don't think rysnc -- or any backup utility -- is smart enough to detect that a moved file is really the same file. 

Having said that, you could write a script that could record a dictionary hash of (key,value) pairs with the key being the MD5sum of each file and the value being the path of the file.

Then you could tote that dictionary file over to the remote server, and run another script which will move any file with a matching MD5sum to the location indicated by the dictionary file.

This would not be that hard to do. It relies on the belief that in practice MD5sums are unique signatures for any file. The problem is, theoretically, two different files could have the same MD5sum. I don't know how astronomically small this probability is, so I can't say just how dangerous my proposed solution to your problem is. (If a file on the remote server had the same MD5sum as a *different* file on the local machine, then it will be move to the wrong location and would get overwritten the next time you ran rsync.)

Another downside to the above strategy is that it will only work if you *only* move the file. If you both move the file and modify the file, then the MD5sum will be different on the two hard drives, and  so no program on earth could know with certainty that they really are the same.

---

### Post by eeboy on 2008-05-12
unutbu - Thanks for the info. Assuming rsync is not capable of performing the move operation (and I take your word for it), your alternate solution sounds feasible to me. I don't know much about the MD5sum but from what I've read in the last 15 minutes it's unique enough for me and my application.

I think I'll take a shot at implementing your suggestion. I am new to linux in general. This might be easiest for me to complete in c... Unless there is a really clean way of doing the following via shell scripting:

-on the source side piping the ls -R command to the md5sum command while re-directing output to a file to form the key/value pairs 
-reading the key/value pairs on the destination

---

### Post by eeboy on 2008-05-13
If anyone is interested I've taken care of the source script based on a few leads found while googling:

```
find /some/dir -type f -exec md5sum {} \; > md5.lst
```

---

### Post by unutbu on 2008-05-13
Here is a speed-bump you're going to have to get over:
Many files on the local machine may have the same MD5sum. For example, some programs save backups of the file you are working on. If the file is called 'doc.txt' you may have 'doc.txt~' which is identical, hence same md5sum. 

Now on the remote server suppose you run the script to move files around according to their md5sums. How is the script going to decide which location to use if a single md5sum key has two values ('doc.txt' and 'doc.txt~')?

Also, there can be a lot of empty files that you may want to backup anyway. They'll all have the same md5sum too. Run

```
find . -type f -size 0 > empty-files
```

to get a sense of the problem.

---

### Post by eeboy on 2008-05-13
Yeah... that's an issue. By the way... does the ~ appended to the end indicate a temp working file? I've noticed these but they don't disappear after you've closed the file you are working on. 

I was reading a bit more and this may or may not be helpful but what about hard links. As I understand it there is a unique numeric value for each file. Why couldn't this be used? Or does this value change when it's placed on the remote server?

---

### Post by unutbu on 2008-05-13
Yes, files with a ~ appended to their end are backup copies. When I start editing a file, the original is copied to a backup of the same name with the ~ at the end. If at some point I say "revert buffer", my text editor uses the ~ file to revert.

Re: hard links. I think you are referring to inode numbers. Yes, they are unique on any given filesystem, but you can't control the inode that is assigned on the remote server, so they won't be the same on the local and remote machines, and thus they aren't a good way of identifying same files across two file systems.

By the way, we can make an estimate of the probability that two different files have the same md5sum: This is really the same problem as the classic children's betting game "What's the probability 2 kids in the same class of 30 students share the same birthday?" (There are 365 different possible days).

In our case it's "What's the probability that 2 files out of a pool of say 10000 files share the same md5sum?" (There are 16^32 different possible md5sums).

The birthday problem is solved [http://mathforum.org/dr.math/faq/faq.birthdayprob.html](http://mathforum.org/dr.math/faq/faq.birthdayprob.html),
and by the same method I estimate that the probability is around 1.5 * 10^(-31), and that you would need to be backing up somewhere on the order of 10^17 files before the risk of an md5sum collision becomes greater than 1 in 10,000.

---

### Post by eeboy on 2008-05-13
Actually the empy file may not be too big of an issue. What I am focused on is minimizing the put operations which take considerable time. I'll let rsync handle the empty file issue via its normal operation. Also, I can detect an MD5 collision so I can either prompt or ignore this and allow rsync to deal with it. Make sense?

So, now how do I most efficiently handle this process...

I know c fairly well but I don't know shell scripting. I am finding some useful tools to use in the shell so it might just be wothwhile to learn shell scripting. The find command in conjunction with the md5sum command creates a nice listing on both sides. I've found the diff command but I think I'd have to make a lot of assumptions to get it to work correctly. What do you suggest?

---

### Post by unutbu on 2008-05-13
I don't know C or bash well enough to write this program in either language. If you choose to write it in C or bash, I'd be interested in seeing it. Here is a first attempt at the solution in perl:

Save as 'mv-by-md5sum'.

```
#!/usr/bin/perl
use strict;
use warnings;
use File::Find;
use File::Path;
use File::Basename;
use Getopt::Long;

my ($simulate);
GetOptions(
    'simulate'=>\$simulate,
    );


# Load md5.lst into a hash called %md5path.
my %md5path;
open(MD5,"<","md5.lst") || die "Can't open md5.lst";
while (my $line=<MD5>) {
    chomp($line);
    if ($line=~m/^(\S+)\s+(.+)$/) {

	# The (key,value) pairs of %md5path: 
	# key is the md5sum
	# value is an array of paths. I use an array because it is possible for 
	# backup files, hard/soft symlinks, or empty files to share the same md5sum.
	push(@{$md5path{$1}},$2);
    }
}
close(MD5);

# find will call subroutine process once for each file found below ".".
my %options=(
    no_chdir=>1,
    wanted=>\&process,
    );
find(\%options,("."));


sub process {
    my $file=$_; 
    return unless (-f $file);

    # compute the md5sum for $file
    my $md5str=`md5sum $file`;
    my ($md5sum)=($md5str=~m/^(\S+)/);
#    warn "(file,md5sum)=($file,$md5sum)\n";

    # Test that the md5sum found on the remote server is in the hash.
    if (exists($md5path{$md5sum})) {
	# Test that there is only one path corresponding to this md5sum.
	# If there is more than one path, we just ignore this file. 
	if (scalar @{$md5path{$md5sum}} == 1) {
	    # $new_file is the path as defined in md5.lst
	    my $new_file=$md5path{$md5sum}[0];
	    # Break the path into a file name and a path
	    my ($basename,$new_path,$suffix) = fileparse($new_file,//);	    
#	    warn "($new_file: $basename,$new_path,$suffix)\n";
	    if ($simulate) {
		warn "mkpath($new_path)\n" unless (-d $new_path);
		warn "moving $file to $new_file\n" unless ($file eq $new_file);
	    } else {
		# Make the path if it doesn't already exist. This will handle the creation of multiple directories if necessary.
		mkpath($new_path) unless (-d $new_path);
		# Move the file to the new location if $file and $new_file don't match.
		rename($file,$new_file) unless ($file eq $new_file);
	    }
	}
    }
}

```

On the remote server, 

```
mv-by-md5sum --sim
mv-by-md5sum

```

The first line will just print out what it plans to do, the second line actually does it.

Tell me if you don't like how it handles duplicate md5sums in md5sum.lst, or on the remote server.

---

### Post by evithyan on 2009-04-08
unison can do this.  The xferbycopy option controls it (which is turned on by default).

unison is bi-directional, but it can be made to imitate rsync with -force and -batch.

Cheers, -Ryan

---

### Post by kaie on 2009-10-28
I had the same problem.

I couldn't get unison to do what I want, and I don't like the fact that unison creates its own files in order to track the state of the files to process.

rsync is slow and doesn't give progress while analyzing what it will do.

In order to solve the problem I just finished to write a tool myself, MoveSync, which I just published, I'm looking for testers and feedback.

As it's new software, please be careful, and use --dry-run to see what it will do.

[https://sourceforge.net/projects/movesync/#](https://sourceforge.net/projects/movesync/#)

---

