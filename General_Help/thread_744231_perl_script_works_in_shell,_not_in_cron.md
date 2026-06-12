---
title: "perl script works in shell, not in cron"
date: 2008-04-03
forum: General Help
---

### Post by vortmax on 2008-04-03
I'm writing a perl script to manage feeds from my security cameras.  The cameras dump the images to the system via ftp, so I have a folder that just collects these jpg files.  Every minute, the script grabs all the files in the dump dir, moves them over to a tmp dir, and converts them into an mpg file in another tmp dir.  Then it deletes all the original and tmp files so it can repeat.

When I run this script from the command line (as root), it works and generates a working mpg file.  When I set it up in (root's) cron, it runs every minute as it should, but spits out a 0 kb mpg file.  

Here is a copy of the script.  Any thoughts as to what is happening.  It might be possible that the script is being called to run again before it is doine the first time, but when I run it on the command line, it doesn't seem to take a full minute to execute.  I've even tried upping the run time to 2 minutes, but it still does the same thing.  I have to run this frequent otherwise convert gets overwhelmed with the number of files and craps out.  It's much faster to make a bunch of small mpgs then merge them later on.

anyway, here's the code:

```

#!/usr/bin/perl

my (@files, @files2, $file, $dir);

my $convert		= "/usr/bin/X11/convert";		# convert binary


###### Some file paths #####################################################################


#### Location FTP server dumps jpegs to ###################
my $west_src = "/home/security/west";
my $ne_src   = "/home/security/ne";

### Tmp dir to hold jpegs being compiled into movie #########
my $west_tmp = "/home/security/west_tmp/jpg";
my $ne_tmp   = "/home/security/ne_tmp/jpg";

### Tmp dir to hold short mpg clips waiting on processing ########
my $west_vid_tmp = "/home/security/west_tmp/mpg";
my $ne_vid_tmp   = "/home/security/ne_tmp/mpg";

### Final resting place of finished video ########
my $west_vids = "/home/security/west_vids";
my $ne_vids = "/home/security/ne_vids";

my ($sec,$min,$hour,$mday,$mon,$year,$wday,$yday,$isdst)=localtime(time);
my $time =  sprintf "%4d-%02d-%02d_%02d%02d",$year+1900,$mon+1,$mday,$hour,$min;
$time .= ".mpg";                      # append file extension to file name

my $nfps = 1;		#number of times each frame will exist in the mpg
my $frame = 1;  #set the initial frame to 1
$cam = "jpg";		#tag on jpg dump file to identify it as such



sub scandir {

  #
  # Scan directory for image files
  #

  $dir = $_[0];
  opendir(DIR, $dir) || die "can't opendir $dir: $!";
  @files = grep { /$cam/ && -f "$dir/$_" } readdir(DIR);
  closedir DIR;
  return @files;

}



#################### copy files for west camera #####################################################

@files = scandir ("$west_src");					# get source directory file list

@files=sort(@files);

foreach $file (@files) {


	for($i=0; $i<$nfps; $i++){				# copy the frame into tmp
		system "cp $west_src/$file $west_tmp/$frame.jpg";
		$frame++;
	}
	system "rm $west_src/$file";

}



#################### copy files for east camera #####################################################

@files = scandir ("$ne_src");                                 # get source directory file list

@files=sort(@files);
$frame = 1;
foreach $file (@files) {


        for($i=0; $i<$nfps; $i++){
 #               system "cp $ne_src/$file $ne_tmp/$frame.jpg";
                $frame++;
        }
	system "rm $ne_src/$file";


}



####################### Convert west camera to video ##################################################
@files2 = scandir ("$west_tmp");                                      # get source directory file list

@files2=sort{$a <=> $b}(@files2);			# put the list of files in numerical order
$seq = '';                            # place to hold the ordered list

    #assemble ordered list of files
foreach $file (@files2) {		

	$seq .= ' '."$west_tmp/$file";
  }

system "$convert $seq $west_vid_tmp/$time";     #convert files to mpg



####################### Convert ne camera to video ##################################################
@files2 = scandir ("$ne_tmp");                                      # get source directory file list

@files2=sort{$a <=> $b}(@files2);
$seq = '';

foreach $file (@files2) {

	$seq .= ' '."$ne_tmp/$file";
  }

#system "$convert $seq $ne_vid_tmp/$time";


####################### Clear temp files and old video files ###########################################



#system "rm  $ne_tmp/*.jpg";
system "rm  $west_tmp/*.jpg";


```

---

### Post by cmnorton on 2008-04-03
Do you have email enabled, at least locally on the box, or could you direct (>) the perl script to a log file and see what gets printed?

When you run the perl script as root, your pwd is somewhere you expect. What would happen if you replaced your perl script with a shell script that managed a few things for you, like setting you to a known default directory, or having that done in perl? 

(I happen to like the model of shell scripts running programs, but that is a preference, not a hard and fast rule.)

My guess is this is failing, because when cron runs the perl script's working directory is somewhere you do not expect.

---

### Post by vortmax on 2008-04-03
cron isn't reporting any errors.  When I redirect it to a log file, I get nothing until I put an explicit 'printf' statement in the code.  That does get printed to the log file.

I'm 99% sure it's not a PWD issue as I explicity define the path to everything in the script

okay...
so I made this shell script:

```

#!/bin/bash

export PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin'

cd /home/security

perl /home/security/convert.pl &> /home/security/error.log

```

I still get the same thing.  The perl script is running fine.  The convert function is even working...it's just producing 0 sized output file.

I also timed it.  The script takes roughly 30 seconds to complete when running from the shell

EDIT:  okay.....so I let it run while typing up that reply (didn't change anything) and suddenly it's working.  Not sure what I did but it works.  It appears that calling perl through a bash script is the way to go.  Now is there a way to simplify that down so I don't have 2 files for every script I want to cron?

---

### Post by IcemanV9 on 2008-04-03
I am sure you have tested your perl script many times. And, it worked just fine (right?). So, it's the crontab issue. You need to define the environment in the crontab. Here's the example:
```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
SHELL=/bin/bash

* * * * * cd /home/security; perl convert.pl > error.log 2>&1

```
Let me know if it works or not. And, good luck!

---

