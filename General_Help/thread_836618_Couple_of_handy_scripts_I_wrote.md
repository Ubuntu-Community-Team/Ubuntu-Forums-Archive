---
title: "Couple of handy scripts I wrote"
date: 2008-06-21
forum: General Help
---

### Post by sonicb00m on 2008-06-21
I wrote a couple of scripts I needed to write to handle a few daily tasks. They are knocked up in perl and might help someone.

Both scripts are pretty basic and could be improved upon, but truth be known Perl isn't my favourite language and I find it quite cumbersome to write.

The first script is for those who have friends or remote computers with a dynamic IP and wish to use their firewall to deny access by ip. You will need a dynamic IP host provided by places like no-ip.info. You will need to make sure that this is updated when your IP changes (either in your router or IP updater program for the service).

In this example, the dynamic host address is checked and compared with the previous record and then shorewall is restarted. All your friends with dynamic hosts will still be able to access your services without a manual restart.

```

#!/usr/bin/perl -w
use Socket;

my $file = "currentip";
my $log = "ipchecks-log";
my $restart = "N";

use POSIX qw/strftime/;
my $stamp = strftime("%Y-%m-%d %H:%M", localtime);

open (F, $file) || die ("Input file does not exist $file!");
open(L,">>".$log);

while ($line = <F>)
{
	($host,$currentip) = split ':', $line;
	
	$host =~ s/\n// if defined $host;
	$currentip =~ s/\n// if defined $currentip ;
	
	if($currentip ne ""){
		if (inet_aton($host)) {
			$ip = inet_ntoa(inet_aton($host));
			$ip =~ s/\n//;
		} else {
			$ip = $host." is non-existant domain, no IP address";
	 
		}
		
		$line  =~ s/\n//;
		print L $stamp." Checking : ".$line."\n";
		print L $stamp." Old  IP : ".$currentip."\n";
		print L $stamp." Host IP : ".$ip."\n";
		
		if($currentip ne $ip){
			 
			 print L $stamp." Restart - ".$host.":".$currentip." to ".$ip."\n";
			 $restart ="Y";
	 
		}else{
			print L $stamp." Nothing to do.\n";
		}
		 
		print L "==========\n\n";

		push(@write,$host.":".$ip);
	}
}
close (F);

if($restart eq "Y"){
	system("/etc/init.d/shorewall restart");
	print L $stamp." Restarting shorewall.\n";
	
	#Write new ip address to file
	open(F,">".$file);

	foreach (@write){
		print F $_."\n"; 
	}

	close (F);
}

$status = system("shorewall status");

print $status;

close (L);


```

You will need to place a file called currentip in the working directory and here you can list all the computers with dynamic ips in this format

```

www.host1.com:212.01.22.211
www.host2.com:78.101.88.01
etc etc

```

=======================================0

The second script converts either a directory of mp4 files or an input file to xvid. 

```

#!/usr/bin/perl -w

# Convert an mp4 to xvid
# Take a single input file or a directory of mp4s

use lib 'classes';
my $in = $ARGV[0];
my $out= $ARGV[1];
my $bitrate = $ARGV[2];

if($bitrate <= 0){
	$bitrate = 2000;	
}

if($out eq ""){
	
	@files = <$in/*.mp4>;
	foreach (@files) {
		print "\n\n====================\n\n";
		$in = $_;
		print "Being encoding file $in\n";
		print "Writing xvid converstion to $in.avi at $bitrate\n";
		print "\n\n====================\n\n";

		system("mencoder $in -ovc xvid -oac mp3lame -xvidencopts bitrate=$bitrate -o $in.avi");
	}
	
}else{
			
	print "\n\n====================\n\n";
	print "Being encoding file $in\n";
	print "Writing xvid converstion to $out at $bitrate\n";
	print "\n\n====================\n\n";

	system("mencoder $in -ovc xvid -oac mp3lame -xvidencopts bitrate=$bitrate -o $out");
	
}


```

name the script whatever you want and set it to be executable. 

you can do this

script.pl /media/video 

and all the videos with extension .mp4 will be converted

or you can do 

script.pl /media/video/1.mp4 /home/xxx/

the 3rd parameter is bitrate and is set to 2000 by default.


script.pl /media/video  "" 1000
script.pl /media/video/1.mp4 /home/xxx/ 1000

I know they are a bit cowboyish but what the hell, I program for a living and can't be bothered doing a great job on my days off :lolflag:

---

### Post by K.Mandla on 2008-06-22
Moved to General Help.

---

