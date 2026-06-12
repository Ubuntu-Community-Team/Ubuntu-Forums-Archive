---
title: "how do I repair /var/lib/dpkg/status?"
date: 2007-06-15
forum: General Help
---

### Post by cd-r80 on 2007-06-15
Cannot install or fix nothing. How do I repair packages "cache"? Dpkg, apt-get, synaptic?

dpkg: parse error, in file `/var/lib/dpkg/status' near line 1688 package `libdbus-1-2':
 field name `
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/status' near line 1688 package `libdbus-1-2':
 field name `

---

### Post by mannheim on 2007-06-15
The system automatically keeps backups of the file /var/lib/dpkg/status. You can find the backups in the directory /var/backups/ with names like dpkg.status.*.

(EDIT: And there's another one at /var/lib/dpkg/status-old.)

Assuming what is wrong is that your /var/lib/dpkg/status is corrupted, I'd first make a copy of the present version in your home directory for safekeeping. Then you could copy one over one of the backups, e.g.

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

It might be an idea to compare the present one with the backup first, using diff. None of this addresses the question of why the file is corrupted in the first place.

---

### Post by linas on 2008-01-07
So is there no way to rebuild this file from scratch? In my case, both this and the
backup have random bytes that got corrupted somehow, for example:


Packsge: gpal
Status: purge ok not-i,stalled
Priority: optional
Section: non-US

Package: libgarbo-dgv
Status: purge ok not-installe$
Priority: optional
Section: de4el

Package: dvi2ps-fontdata-rrk
Status: purge ok not-installed^PPriority: optional
Section: tex^B
Package: libgstreamer-plugins-base0.10-0
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 740
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>

I am trying to manually fix these, but there seems to be a *lot* of them.

---

### Post by capink on 2008-01-07
Using the script below will generate a new status file in your current directory (usually your home dir). Use this file in place of your status file ***[I]_after backing it up_*[/I]**:

```
#!/bin/bash

get_control_info ()
{
	for i in /var/lib/apt/lists/*_Packages
	do
		sed '/Package: '"$1"'$/,/^$/!d' $i
	done
}

for i in /var/lib/dpkg/info/*.list
do
	package_name=`basename $i | sed 's/.list$//'`
	get_control_info $package_name >> status-new
done

sed -i -e '/^Filename: .*/d' -e '/^MD5sum:/d' -e '/^SHA1:/d' -e '/^SHA256:/d' status-new
sed -i '/^Package: /a\Status: install ok installed' status-new


```

The new status file will not be prefect but it is a place to start from. Two problems I am aware of are:

1. The new status file will have all the packages marked as installed including those you uninstalled. This can be corrected later using your original status file.

2. The new status file will miss the field of Confiles. While not absolutely essential, it is very important field. Again this can be corrected using your old status file. But this will need some manual editing.

Note: The script will take long time to complete. On my machine it took about one hour.

---

### Post by kfor on 2008-05-07
Through idiocy I lost my whole /var partition, so one of my problems
is that /var/lib/dpkg/status is missing.

Using the [script Karsten M. Self provided]("http://linuxmafia.com/faq/Debian/package-database-rebuild.html") I was able to get some of the files in
/var rebuilt.

Using capink's shell script as a model, I wrote a perl script that
does the same thing, but takes only a couple of seconds to run - it
passes over the input files only once each.

One minor technical difference is that capink's script uses files in
/var/lib/dpkg/info/ to work out which packages are installed, whereas
my own uses the subdirs of /usr/share/doc, as per Karsten's
suggestion.  Both ways should work, but I didn't have any files in
/var/lib/dpkg/info/ to work with ;-)

Thanks go to capink for showing /how/ it's done!

(As an aside, I'm running Debian Etch, but Ubuntu seems to be the same
 for this purpose)



```

#!/usr/bin/env perl

#
# A script to build a new dpkg status file.  Relies on an assumption
# that /usr/share/doc is intact, and that each subdir of that
# indicates an installed package.
#
# This script can be run as a non-root user and creates output files,
# in an unsecure fashion, in /tmp.
#
# Thanks to capink on ubuntuforums.org, and Karsten M. Self.
#

use strict;
use warnings;


my @installed_packages;
my %package_control_info;  # By package, then by file.
my $new_status_file = "/tmp/new-status";
my $new_dpkg_selections_file = "/tmp/new-dpkg-selections";


##
##  Here we populate @installed_packages by examining /usr/share/doc,
##  as suggested by Karsten M. Self.
##
opendir DOC, "/usr/share/doc" or die "failed opening doc dir";
foreach ( grep { -d "/usr/share/doc/$_" } readdir( DOC )) {
    next if ( m/^\./ );
    next if ( m/[A-Z]/ );
    next if ( $_ eq 'texmf' );
    next if ( $_ eq 'debian' );
    push @installed_packages, $_;
}
closedir DOC;


##
##  Now we hash the contents of the control files.
##
my ($package, $control_file);
opendir LISTS, "/var/lib/apt/lists" or die "failed opening lists dir";
while (my $control_file = readdir( LISTS )) {
    next unless ( -f "/var/lib/apt/lists/$control_file" );
    next unless ( "/var/lib/apt/lists/$control_file" =~ m/_Packages$/ );

    open CONTROL_FILE, "/var/lib/apt/lists/$control_file"  or die "failed opening control file '$_'";
    while (my $line = <CONTROL_FILE>) {
        if ( $line =~ m/^(Package:\s)(.*$)/ ) {
            my $package_name = $2;
            push @{ $package_control_info{$package_name}->{$control_file} }, $line;
            $line = <CONTROL_FILE>;
            while ($line !~ m/^\s*$/ ) {
                push @{ $package_control_info{$package_name}->{$control_file} }, $line;
                $line = <CONTROL_FILE>;
            }
        }
    }
    close CONTROL_FILE;
}
closedir LISTS;


##
## Here we create the new status file by printing all the control info
## we have for all the installed packages, as suggested by 'capink' on
## ubuntuforums.org.
##
open NEW_STATUS_FILE, ">", $new_status_file   or die "this sucks";
foreach my $package ( @installed_packages ) {
    while (my ($control_file, $control_info_ref) = each( %{ $package_control_info{$package} } ) ) {
        my @status_info;
        foreach my $line ( @{ $control_info_ref } ) {
            next if ( $line =~ m/^Filename:/ );
            next if ( $line =~ m/^MD5sum:/ );
            next if ( $line =~ m/^Size:/ );
            next if ( $line =~ m/^SHA1:/ );
            next if ( $line =~ m/^SHA256:/ );
            push @status_info, $line;
            if ( $line =~ m/^Package:/ ) {
                push @status_info, "Status: install ok installed\n";
            }
        }
        push @status_info, "\n";
        print NEW_STATUS_FILE @status_info;
    }
}
close NEW_STATUS_FILE;


##
## Here we create a dpkg selections file containing a list of the
## packages we think are installed.
##
open NEW_SELECTIONS_FILE, ">", $new_dpkg_selections_file   or die "this also sucks";
foreach my $line ( @installed_packages ) {
    print NEW_SELECTIONS_FILE "$line install\n";
}
close NEW_SELECTIONS_FILE;


print "\n";
print "New status file created: '$new_status_file'.\n";
print "If it looks right, then:  mv  '$new_status_file'  '/var/lib/dpkg/status'\n";
print "\n";
print "New dpkg selections file created: '$new_dpkg_selections_file'.\n";
print qq|run 'dpkg --get-selections < "$new_dpkg_selections_file"'  to re-create deselect's selections.\n|;
print "\n";


```

---

