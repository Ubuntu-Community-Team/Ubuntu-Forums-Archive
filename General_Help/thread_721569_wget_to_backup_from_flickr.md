---
title: "wget to backup from flickr"
date: 2008-03-11
forum: General Help
---

### Post by engberg on 2008-03-11
Is it possible to use wget to download images from flickr to a directory on ubuntu?

I've tried:
wget -P Slides -r -p -nd -t5 -H [http://www.flickr.com/photos/24610379@N06/](http://www.flickr.com/photos/24610379@N06/) -erobots=off

This gives me a lot of files (too many), and only the 3 real images in a crappy resolution...

What can I do?

---

### Post by unutbu on 2008-03-11
```

wget -P Slides --no-parent -A .jpg -p -nd -t5 -H http://www.flickr.com/photos/24610379@N06/ -erobots=off

```

---

### Post by engberg on 2008-03-11
Thanx for the effort.

That does give me only the images I want - but the resolution is merely 500x300..

One of the images I would like is here:
[http://www.flickr.com/photos/24610379@N06/2327328898/sizes/l/](http://www.flickr.com/photos/24610379@N06/2327328898/sizes/l/)
- in a much higher resolution.

---

### Post by unutbu on 2008-03-11
Can you tell me the direct url of the three images you are looking for?

(e.g.
[http://www.flickr.com/photos/24610379@N06/2327328898/sizes/l/](http://www.flickr.com/photos/24610379@N06/2327328898/sizes/l/)
and what two other url?)

---

### Post by engberg on 2008-03-11
Yes, but that would be no fun...

It's:
[http://farm3.static.flickr.com/2063/2327328898_95df01ae90_b.jpg](http://farm3.static.flickr.com/2063/2327328898_95df01ae90_b.jpg)
[http://farm3.static.flickr.com/2143/2327327480_a64a9df781_b.jpg](http://farm3.static.flickr.com/2143/2327327480_a64a9df781_b.jpg)
[http://farm3.static.flickr.com/2113/2326510999_e8da5ce72b_b.jpg](http://farm3.static.flickr.com/2113/2326510999_e8da5ce72b_b.jpg)

- but what I want is to do this dynamically - for a DIY photoframe, that I'm making..

So it's only right now, that it is these urls - tomorrow it might be new ones...

But the page:
[http://www.flickr.com/photos/24610379@N06/](http://www.flickr.com/photos/24610379@N06/)
- stays the gathering point..

---

### Post by unutbu on 2008-03-11
Put this in a file. I'll call it 'gf.pl'.

```

#!/usr/bin/perl
use strict;
use warnings;

my $url=shift @ARGV;
my ($pat)=($url=~m|www.flickr.com/(.*)|);
if (!($pat=~m|/$|)) {
    $pat.='/';
}
system("wget -O tmp.html $url");
open(FILE,"<","tmp.html") || die;
my %dir;
while (<FILE>) {
    if (/$pat/) {
	my $line=$_;
	my ($sub_url)=($line=~m|$pat([^/"]*)|);
	next unless ($sub_url=~m|\d+|);
	$sub_url="${pat}${sub_url}";
	$dir{$sub_url}=1;
    }
}
close(FILE);
foreach (keys %dir) {
    my $new_url="http://www.flickr.com/$_/sizes/l/";
    print "$new_url\n";
    my $cmd="wget -r -P Slides --no-parent --accept .jpg -nd -t5 -H -erobots=off $new_url";
    print "$cmd\n";
    system($cmd);
}

```

Run
```

chmod 755 gf.pl
./gf.pl http://www.flickr.com/photos/24610379@N06

```

Not perfect, but better?

---

### Post by engberg on 2008-03-11
Great work!!
You're some kind of wizzard? :-)

That works really well, besides the fact, that I seem to get 2 files of the same kind - only the filename is diferent - ex.:

2327328898_95df01ae90_b.jpg
2327328898_95df01ae90_b_d.jpg

The duplets all end in _d so perhaps one could delete those ending in _d?

---

### Post by unutbu on 2008-03-11
Enjoy:

```

#!/usr/bin/perl
# Usage: ~/bin/get-flickr.pl http://www.flickr.com/photos/24610379@N06
# Warning: This script will create/overwrite tmp.html.

use strict;
use warnings;

my $url=shift @ARGV;
my ($pat)=($url=~m|www.flickr.com/(.*)|);
if (!($pat=~m|/$|)) {
    $pat.='/';
}
system("wget -O tmp.html $url 2>/dev/null");
open(FILE,"<","tmp.html") || die;
my %dir;
while (<FILE>) {
    if (/$pat/) {
	my $line=$_;
	my ($sub_url)=($line=~m|$pat([^/"]*)|);
	next unless ($sub_url=~m|\d+|);
	$sub_url="${pat}${sub_url}";
	$dir{$sub_url}=1;
    }
}
close(FILE);
foreach (keys %dir) {
    my $new_url="http://www.flickr.com/$_/sizes/l/";
    system("wget -O tmp.html $new_url 2>/dev/null");
    open(FILE,"<","tmp.html") || die;
    while (<FILE>) {
	if (/"(http[^"]+\.jpg)"/) {
	    my $direct_url=$1;
	    next if ($direct_url=~m|_d\.jpg$|);
	    next if ($direct_url=~m|buddyicon\.jpg$|);
	    my $cmd="wget -P Slides $direct_url 2>/dev/null";
	    print "$cmd\n";
	    system($cmd);
	}
    }
    close(FILE);
}
unlink("tmp.html");

```

---

### Post by engberg on 2008-03-12
Alright..

So here is the full solution for my DIY photoframe..
I named the above script GetFlickr.pl and placed it in my homedirectory:
/home/engberg/

Then I called the following script opdater.sh and placed it in the same home-dir.:
```

#!/bin/sh
echo “Opdaterer”
wget -P Slides -r -p -nd -t5 -H --domains=.blogger.com,kaspere.blogpost.com http://kaspere.blogspot.com/ -A.jpg,.jpeg,.jpg.1,.jpg.2,.jpeg.1,.jpeg.2 -erobots=off
find /home/engberg/Slide/* -size -100k -type f -exec rm -f {} \;

```

Then I edited my crontab by typing: gedit /etc/crontab - and inserted the following:
```

00 * * * * engberg export DISPLAY=:0 && /home/engberg/opdater.sh
05 12 * * * engberg export DISPLAY=:0 && /home/engberg/GetFlickr.pl http://www.flickr.com/photos/24610379@N06
00 23 * * * root halt

```

To start it all I use the command:
feh --hide-pointer -qrzZFD 20 /home/engberg/Slides/
added to System\Preferences\Sessions\Startup

Hope this can inspire others.. Thanx for all the help from this community..

---

### Post by atoc on 2008-03-12
While these techniques are awesome, why not just download [FlickrEdit]("http://sunkencity.org/flickredit")?
Unless these photos are not from your own account...if that's the case don't mind me, it's the medication.

---

