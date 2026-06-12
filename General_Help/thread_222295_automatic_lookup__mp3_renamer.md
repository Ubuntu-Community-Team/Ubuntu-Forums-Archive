---
title: "automatic lookup / mp3 renamer"
date: 2006-07-24
forum: General Help
---

### Post by nix4me on 2006-07-24
Is there a program that processes a bunch on mp3 files and goes out to the internet to identify them and then rename them?

I've tried tagtool but it is manual and not automated.

thanks,
nix4me

---

### Post by reacocard on 2006-07-24
try cowbell

---

### Post by nix4me on 2006-07-24
Thanks for the reply.  Cowbell works ok for id3 tags but does not rename files automaticaly.

I am probably looking for something that does not exist. :)

nix4me

---

### Post by soze on 2006-07-25
> **nix4me said:**
> Thanks for the reply.  Cowbell works ok for id3 tags but does not rename files automaticaly.

I am probably looking for something that does not exist. :)

nix4me

Here is a perl script that will rename the files once they are tagged.
Specify the directory with your MP3s as the command line argument and away you go.

(You may want to tweak the resulting filename template)

```

#!/usr/bin/perl
require 5;
use strict;
use Image::ExifTool 'ImageInfo';

my $trackdir = $ARGV[0];
opendir(DIR, $trackdir) || die("unable to open directory $trackdir");
my @tracks = grep { /.mp3/i } readdir DIR;
closedir DIR;
my $exifTool = new Image::ExifTool;

foreach (@tracks) {
    my $filename = "$trackdir/$_";

    $exifTool->ExtractInfo($filename);

    my $title = $exifTool->GetValue('Title');
    my $album = $exifTool->GetValue('Album');
    my $artist = $exifTool->GetValue('Artist');
    my $genre = $exifTool->GetValue('Genre');
    my $track = $exifTool->GetValue('Track');

    $track =~ /[^0-9]*([0-9]+)[^0-9]*/;
    $track = $1;


    print STDERR "$artist $album $title $genre $track\n";   

    $track = sprintf("%02d", $track);
    my $newname = "$artist-$album-$track-$title";
    $newname =~ s/[^A-Za-z0-9\-\.]+/_/g;
    rename("$trackdir/$_","${trackdir}/${newname}.mp3");

}



```

---

