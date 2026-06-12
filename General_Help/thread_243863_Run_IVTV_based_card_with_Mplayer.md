---
title: "Run IVTV based card with Mplayer"
date: 2006-08-25
forum: General Help
---

### Post by CornMaster on 2006-08-25
I'm sure there are better ways to do this then what I have done, but if you are using a IVTV based tuner (like Hauppauge TV 150/250/350/500, etc...) then you can use some of the drivers tools and mplayer to watch tv in a nice window on your desktop.  I looked around for other programs or solutions no this problem (for a few hours) but I didn't find anything so here I am.

While I was doing the tutorial to get mythtv working (the installing the drivers part) the tutorial instructed me to use mplayer to test the video.  And then continue installing mythtv from there.  Well when I realized that mythtv was overkill for watching a bit of tv while I surf the web, I decided to try and use mplayer to do what tvtime used to. (Since it doesn't work with ivtv drivers)

Below are two perl scripts I wrote that launches mplayer with audio and video and changes the channel.  They still need a lot of work, and I hope to wrap a gui around them eventually.

Pre-reqs: 
mplayer
A tv-tuner
The IVTV drivers installed

To use:
Just copy the scripts to some .pl files, and make them executable.  Make some shortcuts on the desktop and enjoy. :)

Notes:
You may need to change the device from video0 to video1 or something else depending on your setup.

```

#!/usr/bin/perl 

use strict;
use warnings;

#####
# This file starts mplayer
#
#####

&startMplayer;

# This sub starts mplayer on tuner device 0 with the audio needed
#
sub startMplayer(){
	my @args;
	@args = ("mplayer","-vo","xv","/dev/video0","-ao","alsa","/dev/video0");
	if (exec(@args) == 0){
		return " Done.\n";	
	}
	else{
		return " Error.  System @args failed: $?";
	}
}
```

Here is the perl script that uses the ivtv tools to change the channels:
```

#!/usr/bin/perl 

use strict;
use warnings;

#####
# This file contains the controller for ivtv devices
#   for mplayer
#
#####

my ($returned,$command,$currentChannel);

$currentChannel = "23";

print STDOUT "Welcome to my IVTV control program for Mplayer.\n";

$returned = &availableCommands;
print STDOUT "$returned\n";

while(1>0){
	print STDOUT "\rEnter a command: ";
	$command = <STDIN>;
	chomp($command);
	if ($command eq "+"){
		$currentChannel = $currentChannel + 1;
		&changeChannel($currentChannel);
		print STDOUT "\rCurrent Channel: $currentChannel\n";
	}
	elsif ($command eq "-"){
		$currentChannel = $currentChannel - 1;
		&changeChannel($currentChannel);
		print STDOUT "\rCurrent Channel: $currentChannel\n";			
	}
	elsif ($command eq "start"){
		&startMplayer;
	}
	elsif ($command eq "help"){
		$returned = &availableCommands;
		print STDOUT "$returned\n";
	}	
	elsif ($command eq "quit"){
		exit();
	}
	
	else{
		$currentChannel = $command;	
		&changeChannel($currentChannel);
		print STDOUT "\rCurrent Channel: $currentChannel\n";
	}
}

#
# This sub prints out the available commands
#
sub availableCommands(){
	my $return;
	$return = "Press enter to execute all commands.\n";
	$return .= "start [ENTER] = Launches Mplayer\n";
	$return .= "+ [ENTER] = One channel up\n";
	$return .= "- [ENTER] = One channel down\n";
	$return .= "help [ENTER] = Prints this list\n";
	$return .= "## [ENTER] = Go to channel\n";
	$return .= "quit [ENTER] = Quit the program\n";
	return $return;
}

sub changeChannel(){
	my ($channelnumber) = @_;
	my (@args, $toexec);
	@args = ("ivtv-tune","-c",$channelnumber,"-d","/dev/video0");
	if (system(@args) == 0){
		return "Channel Changed.\n";	
	}
	else{
		return " Error.  System @args failed: $?";
	}		
}

```

---

