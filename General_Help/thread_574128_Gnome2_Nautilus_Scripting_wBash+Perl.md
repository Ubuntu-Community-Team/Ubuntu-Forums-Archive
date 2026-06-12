---
title: "Gnome2 Nautilus Scripting w/Bash+Perl"
date: 2007-10-12
forum: General Help
---

### Post by Xiaoren on 2007-10-12
I have a perl script (~/tests/hearpdf.pl) needs to take a PDF fullpath/filename as an argument. In gnome2, ~/.gnome2/nautilus-scripts is the mouse right-click context menu scripts dir. If I right click select a *.pdf file in nautilus, what environmental variables will be set? 

I am aware (gnome2) nautilus sets certain environmental variables like $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS. I am trying to use this for path/name. I have even tried launching nautlius from the same terminal as I test from.

And I want to pass it to hearpdf.pl as it's first argument. Example: perl /home/superkuh/tests/hearpdf.pl /home/superkuh/Library/imagine-long-name-here.pdf

My naive bash script first attempts to pass arguments like so: ~/.gnome2/nautilus-scripts/hearpdf.sh

It seems like my code is being censored with **** for some reason? I have this post here too:
[http://69.180.166.50/index.html#005](http://69.180.166.50/index.html#005)

```

#!/bin/bash
#	perl /home/superkuh/tests/hearpdf.pl "$*"

	echo "ARGS: $*"
	NAUTILUS_SCRIPT_CURRENT_SHIT=HELLO.
	echo 1. NAUTILUS_SCRIPT_CURRENT_URI
	echo 2. $NAUTILUS_SCRIPT_CURRENT_URI
	echo 3. NAUTILUS_SCRIPT_CURRENT_****
	echo 4. $NAUTILUS_SCRIPT_CURRENT_****
	echo 5. $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS

	perl /home/superkuh/tests/hearpdf.pl "$NAUTILUS_SCRIPT_CURRENT_URI"
	perl /home/superkuh/tests/hearpdf.pl "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
	perl /home/superkuh/tests/hearpdf.pl "$NAUTILUS_SCRIPT_CURRENT_****"

```

I right click a pdf. It fails silently from the context menu. From the command line I find it is calling the program, but not getting anything from $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS while showing proper perl script failure with "HELLO." Not that I expected any nautlius environmental variables to be set.
```

superkuh@epimetheus:~/.gnome2/nautilus-scripts$ ./hearpdf.sh
ARGS: 
1. NAUTILUS_SCRIPT_CURRENT_URI
2.
3. NAUTILUS_SCRIPT_CURRENT_****
4. HELLO.
5.

0: 
Error: Couldn't open file ''
Can't open .

0: 
Error: Couldn't open file ''
Can't open .

0: HELLO.
Error: Couldn't open file 'HELLO.'
Can't open .

```

So, basically, I want to know why when I am selecting a file in nautilus and using the context menu (~/.gnome2/nautilus-scripts) that NAUTILUS_SCRIPT_SELECTED_FILE_PATHS isn't getting set; ie. what I am doing or assuming incorrectly that causes this failure.

When a file is selected via cursor in gnome2 nautilus do the environmental variables get exported to all shells? If so, how? Or is this implicit?

I have tried to get the Gnome::URL module from CPAN, but I am having issues with that too! [http://69.180.166.50/index.html#003](http://69.180.166.50/index.html#003) (detailed output log here)

This is ~/tests/hearpdf.pl
Yes, I know it's clunky, probably stinky, perl. But it works if called manually.
```

#!/usr/bin/perl
# requires festival text to speech and cepstral swift voices
use Parallel::ForkManager;
my $manager = new Parallel::ForkManager( 2 );

unless ($manglefilename = getnautiluspath()) {
	$manglefilename = $ARGV[0];
	foreach $num (0 .. $#ARGV) { 		
		print "\n$num: $ARGV[$num]\n";
		if ($num != 0) {
			$mostargs .= $ARGV[$num] . " "; #arguments for regex
			print "MOSTARGS: $mostargs\n";
		}
	}
}

`pdftotext \"$manglefilename\"`; 

if ($ARGV[1]) {
	if ( $mostargs =~ /(\d+)\s(\d+)/i ) { # to specify pages
		my ($start, $stop) = ($1, $2);
		print "start: $start || stop: $stop\n";
		`pdftotext -nopgbrk -f $start -l $stop $manglefilename`;	
	} else {
		print "\nNormal: \"perl $0 pdf_file.pdf\"\n";
		print "\nPage to Page: \"perl $0 pdf_file.pdf 3 40\" (an example)\n";
	}
}


if ($manglefilename =~ /(.+)\.\w+/) {
	$filename = $1;
	print "\nFilename: $filename\n";
	$realfileext = "$filename" . '.txt'; 
	print "RealExt: $realfileext\n";	
}

open (PDFTEXT, "$realfileext") or die "Can't open $realfileext.\n";
	while () {
		$pdftotal .= $_;
	}
close(PDFTEXT);

print "\n";
print "\_" x 40;  
print "\n$pdftotal\n";
print "\_" x 40; 
print "\nReading...slowly, with lag.\n";

@commands = ("evince \"$manglefilename\"", "swift -f \"$realfileext\"");
foreach my $command (@commands) {
	my $pid = $manager->start and next;
	exec( $command );
	push (@procid,$pid);
	$manager->finish;	
};

sub getnautiluspath {
	# debug
	while (($key, $value) = each(%ENV)){
		if ($key =~ /NAUTILUS/) {
			print $key.", ".$value."\n";
		}
	}
	# path
	$_ = $ENV{'NAUTILUS_SCRIPT_CURRENT_URI'};
	if ($_ and m#^file:///#) {
		s/%([0-9A-Fa-f]{2})/chr(hex($1))/eg;
		s#^file://##;
		$nautiluspath = $_;
	}
	return $nautiluspath;
}

print "Don't press enter until finished.\n";
$meh = ;
`killall swift.bin`;

```

---

