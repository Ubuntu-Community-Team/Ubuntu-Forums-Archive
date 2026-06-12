---
title: "Trying to fix version clash between Ubuntu, Perlmagick, imagemagic"
date: 2013-03-12
forum: General Help
---

### Post by dazz100 on 2013-03-12
Hi
I am developing software in Perl for a webcam application.  I am trying to use imagemagick to add a logo to an image.
Below is the test program that used to run, but doesn't anymore.

From what I have found in the web, it appears I have a clash of versions.  I think this occured as a result of apt-get upgrades. 
To try and fix this I have uninstalled and reinstalled perlmagick and imagemagick using apt-get.  That didn't fix the problem.

So I am now stuck.  I don't know where to turn.  
If I have a clash of incompatible versions, how do I fix that???

```


#!/usr/bin/perl
# ===========================================================
use warnings;
use strict;
use Image::Magick;

my $imageFile = "/var/images/trackcam1/lastsnap.jpg";
my $logoFile = '/home/darren/logo1.jpg';



  my $logo=Image::Magick->New();
  $logo->Read($logoFile);

  my $image=Image::Magick->New();
  $image->Read($imageFile);
  my $webImage = $image->Composite(image=>$logo, gravity=>'NorthWest');
  $webImage->Set(quality=>100);
  $webImage->Write("jpg:/var/images/trackcam1.jpg");


  undef $imageFile;
  undef $logoFile;
  undef $webImage;

exit 1;

```


Running the composite test program with the debugger gave the following error:
		
```
main::(compositeTest.pl:18):      $webImage->Set(quality=>100);
  DB<1>
Can't locate object method "Set" via package "Exception 410: reference is not my type 
`Image::Magick' @ error/Magick.xs/XS_Image__Magick_Mogrify/7505" 
(perhaps you forgot to load 
"Exception 410: reference is not my type 
`Image::Magick' @ error/Magick.xs/XS_Image__Magick_Mogrify/7505"?) at compositeTest.pl line 18.
 at compositeTest.pl line 18
```

The version of perl is: 
```
darren@alpha:~$ perl -v
This is perl 5, version 14, subversion 2 (v5.14.2) built for i686-linux-gnu-thread-multi-64int

```
The imagemagick version is:
```
darren@alpha:~$ composite -version
Version: ImageMagick 6.6.9-7 2012-08-17 Q16 http://www.imagemagick.org
Copyright: Copyright (C) 1999-2011 ImageMagick Studio LLC
Features: OpenMP
```

The Ubuntu server version is:
```
darren@alpha:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:        12.04
Codename:       precise
```

The version of PerlMagick is:
```
precise (perl): Perl interface to the ImageMagick graphics routines
8:6.6.9.7-5ubuntu3.2 [security]: amd64 i386
also provided by: graphicsmagick-libmagick-dev-compat
precise-updates (perl): Perl interface to the ImageMagick graphics routines
8:6.6.9.7-5ubuntu3.2: amd64 i386 
```

---

### Post by dazz100 on 2013-03-13
Hi
I haven't really found a solution but another piece of code.  It also trips up at the bold line below.
Different code and similar error message.

```
sub AddLogo {
# Argument is one or more image file name(s)
# adds logo to image files
# output file overwrites the input file
# no error checking is done on files
# uses Image::Magick;
  my $logoFile = '/home/darren/conwaykarts_logo1.jpg';
  my $logo = Image::Magick->New();
  my $z = $_[0]; # Read the file name parameter
  $logo->Read($logoFile); # read the logo file

    my $image=Image::Magick->New();
    $image->Read($z );
    **my $webImage = $image->composite(image=>$logo, gravity=>'NorthWest');**
    $webImage->write($z ); # overwrite the input file
    undef $image;
    undef $webImage;
  undef $logoFile;  # clean up
}  # AddLogo

```

The error message below indicates that the file "composite.al" can't be found.  Google can't find this either.

```
main::(upload-images.pl:59):        &AddLogo ( $tmpImage);   # add the logo to the image
  DB<1>
**Can't locate auto/Image/Magick/composite.al** in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at upload-images.pl line 114
 at /usr/share/perl/5.14/AutoLoader.pm line 47
        AutoLoader::AUTOLOAD('Image::Magick=ARRAY(0x9cba8e4)', 'image', 'Image::Magick=ARRAY(0x9c84694)', 'gravity', 'NorthWest') called at upload-images.pl line 114

```

Still no closer to finding an answer.

---

### Post by dazz100 on 2013-03-23
Hi

OK.  So I built a new server from scratch. Installed the GraphicsMagick package and got the exact same error message.
I know enough about installing stuff to know my problems are a bug.  I am going to write this up on Lauchpad.

---

### Post by dazz100 on 2013-04-19
Hi
I seem to have had a syntax error.  This code works with Image::Magick.  I haven't tried it Graphic::Magick.  In the fresh installation the version clash dissappeared and the modified code works.  I can't positively identify exactly what caused the initial problem.

I had a similar problem with another section of code.  It turned out to be a uninitialised variable that tripped up the call to Image::Magick.

---

### Post by dazz100 on 2013-04-29
Hello

I fixed the problems with syntax and uninitialized variables.  It was all working.... until I did an apt-get upgrade then deja vu.  
Some part of the upgrade broke the connection between perl and perlmagick.  I am fairly sure that an upgrade on the first server box coincided with the first error messages.

It seems that the autoloader script can't find perlmagick.  Rather than fix the problem I abandoned perlmagick and just made a straight system call to imagemagick.  
I don't consider this problem to be fixed because I still can't use perlmagick.  An upgrade shouldn't break the software.

Dazz

---

