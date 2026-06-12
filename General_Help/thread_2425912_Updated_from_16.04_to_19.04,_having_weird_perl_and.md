---
title: "Updated from 16.04 to 19.04, having weird perl and wine problems"
date: 2019-09-01
forum: General Help
---

### Post by ramicio on 2019-09-01
I have a perl script that encodes videos. It worked flawlessly before the upgrade. Now all of a sudden, the wine processes that it starts sometimes are not ending, despite them being done. I have to find the process and kill it manually so the perl script can continue to the next video. This is time-consuming if I am doing a lot, and they are working overnight. It adds considerable time to total encoding time. Does it have to do with forking two at once? I do this because it makes sense to lower the thread count in x265 instead of going all-out and trying to encode a single one as fast as possible. Too many threads lowers quality per bit rate.

```

use File::Find::Rule;
use File::Basename;
use Parallel::ForkManager;
use Data::Dumper::Simple;
use Getopt::Long qw(GetOptions);

GetOptions( 'log=s' => \$argument ) or die "Please provide an argument for --log (yes|no)";
die "Please provide an argument for --log (yes|no)" unless $argument;

@findlist = find( file => name => [ qw/ *.mkv / ], in => '/mnt/storage/videotemp/bluray/' );
# Makes a list of all files of the .mkv files there

foreach( @findlist ) {
    ( $file, undef, $ext ) = fileparse( $_, qr/\.[^.]*/ );
    $ext =~ s/.//;
    $array{$file}{'extension'} = $ext;
}
# Takes the list, splits the elements into a filename, path (not needed, ergo "undef"), and extension, and stores into a hash with the filename being the key.

open LIST,"<","/home/tim/movies.txt";
while( <LIST> ) {
    chomp $_;
    @line = split( /\\/, $_ );
    chomp( @line );
    if( exists $array{ @line[0] } ) {
        @crops = split( /,/, @line[1] );
        @crops[2] *= -1;
        @crops[3] *= -1;
        $array{ @line[0] }{ "crop" } = "@crops[0],@crops[1],@crops[2],@crops[3]";
        if( defined @line[2] ) {
            @resize = split( /,/, @line[2] );
            $array{ @line[0] }{ "resize" } = "@resize[0],@resize[1]";
        }
    }
}
close LIST;
# Gets crop values for movies that need cropping. Each line is a name  and then the crop value (<left,top,right,bottom>) separated by a  forward slash.
# They are stored in a hash with the filename being the key.

foreach $key ( sort { lc $a cmp lc $b || $a cmp $b } keys %array ) {
    @temp = `wine /mnt/storage/apps/avs2pipemod.exe -info "D:/videotemp/bluray/$key.avs"`;
    @frames = grep /v:frames/, @temp;
    @frames[0] =~ s/v:frames//;
    @frames[0] =~ s/^\s+|\s+$//g;
    $array{ $key }{ 'frames' } = @frames[0];
}


my $pm = new Parallel::ForkManager( 2 ); # Forks x threads.

foreach $key ( sort { lc $a cmp lc $b || $a cmp $b } keys %array ) {
    $pm->start and next;
    if( ! -e "/mnt/storage/videotemp/$key.hevc" ) {
        if( ! -e "/mnt/storage/videotemp/bluray/$key.avs" ) {
            open AVS, ">", "/mnt/storage/videotemp/bluray/$key.avs" or die( 'Could not open avisynth file!' );
            print AVS 'ffvideosource( "'.$key.'.'.$array{$key}{"extension"}.'", cachefile="'.$key.'.ffindex" )'."\n";
            if( defined $array{$key}{"crop"} ) {
                    print AVS 'crop('.$array{$key}{"crop"}.')'."\n";
            }
            if( defined $array{$key}{"resize"} ) {
                print AVS 'bilinearresize('.$array{$key}{"resize"}.')'."\n";
            }
            close AVS;
        }
        #@temp = `WINEPREFIX=~/.wine64 wine /mnt/storage/apps/avs2pipemod64.exe -info "D:/videotemp/bluray/$key.avs"`;
        #@temp = `wine /mnt/storage/apps/avs2pipemod.exe -info "D:/videotemp/bluray/$key.avs"`;
        #@frames = grep /v:frames/, @temp;
        #@frames[0] =~ s/v:frames//;
        #@frames[0] =~ s/^\s+|\s+$//g;
        $cmd = 'wine /mnt/storage/apps/avs2pipemod.exe -y4mp "D:/videotemp/bluray/'.$key.'.avs" | x265 --input - --y4m --level-idc 5.1 --profile main10 --crf 19 --frame-threads 3 --pools 12 --frames '.$array{ $key }{ 'frames' }.' --output /mnt/storage/videotemp/"'.$key.'.hevc"'.( $argument =~ 'yes' ? ' >> /mnt/storage/videotemp/"'.$key.'.log" 2>&1' : '' );
        print "\n$cmd\n\n";
        exec($cmd);
    }
    #print "\n$key\n";
    $pm->finish;
}
# This is a loop for each key in the last hash created.
# Checks to see if there is a crop value defined, and if so, makes a command string from it.
# It then builds the final command and executes it taking up a thread. When it's through, it moves to new thread until no more keys are in queue.

$pm->wait_all_children; # Waits for all threads to be completed in the previous loop and closes the entire program what that is true.

#print Dumper( %array );

```

---

### Post by TheFu on 2019-09-01
As for the perl - did you install the APT versions of those perl modules or are you using cpanm?  
Did you remember to get the newest versions?  
For my perl coding, I always use perlbrew so I'm not dependent on the Canonical packages or system perl which are commonly years out of date. Perl perl-5.31.3 is the current perl5 version, for example.

If you are considering a slightly different method, I do my batch video batch work using Linux tools and using a queue manager - **TaskSpooler**. The package name is task-spooler.  

Any Windows things happen outside the batch parts.  I don't touch bluray anything, so my encoding can be handled by ffmpeg or handbrakeCLI.  My scripts deal with multiple audio tracks, both text captions and subtitles, each have separate tasks in my batch queue.

Put **tsp wine ....** into your script after you install the package. That will queue up each wine job to be run in order.  Output gets put into a file in /tmp/ for each job.  There's job control built into the command to change the order, remove tasks, view output, clean up the finished queue items.

---

### Post by ramicio on 2019-09-01
Some perl modules didn't work after updating, so I updated and installed them in cpan. I'm not interested in another method as far as video encoding is concerned, like ffmpeg or handbrake. I've been using this for years. As far as calling the tasks, possibly. But maybe not, as I have built an entire system and external "databases" for things like cropping that are all handled by my scripts. The problem I am having all of a sudden seems to be related to wine. I have no clue as to why some tasks are all of a sudden hanging and not ending until another task is over.

EDIT: I was thinking the TaskSpooler may be good, but I was also thinking if the tasks aren't ending and need to be killed manually sometimes, that it probably wouldn't solve the problem. Just thinking aloud, LOL.

---

### Post by TheFu on 2019-09-01
Could file locking be preventing the next process?

---

### Post by ramicio on 2019-09-01
I don't know? It never had this problem before the update. What sort of file lock would prevent a process from terminating? And all of a sudden? I just don't understand any of this. I'm lucky I was even able to script this stuff. I'm hardly savvy with computer software.

---

### Post by TheFu on 2019-09-03
In 3 yrs, lots of things change on actively developed software.  WINE is very active.  I'm just throwing out ideas - perhaps WINE implemented a different file locking method to be more in-line with what Windows does?

When people say "suddenly", it usually means that nothing had changed in months, NOTHING, then something stopped working in the expected way.  Upgrading from a stable LTS release to a non-stable, non-LTS release that is 3 years newer isn't exactly an unchanged system. Heck, you aren't even running the same version of perl. ;(

Forget your script.  If you run it manually, does it get stuck?
Is there no native Linux program that can replace avs2pipemod?

---

### Post by ramicio on 2019-09-03
"Forget your script.  If you run it manually, does it get stuck?: "

I  haven't tried it yet. It is completely random and only does it when  running more than one instance of wine. I will try with taskspooler  later.

"Is there no native Linux program that can replace avs2pipemod?"

No there is not.

---

### Post by ramicio on 2019-09-03
task-spooler doesn't work at all. The piping from avs2pipemod to x265 isn't working, whatsoever.

---

### Post by TheFu on 2019-09-03
Read something about using the same WINEPREFIX concurrently being an issue in WINE.
[https://stackoverflow.com/questions/26486114/how-to-run-multiple-wine-instances-in-parallel](https://stackoverflow.com/questions/26486114/how-to-run-multiple-wine-instances-in-parallel)
[https://forum.winehq.org/viewtopic.php?t=26006&p=103672](https://forum.winehq.org/viewtopic.php?t=26006&p=103672)

---

### Post by ramicio on 2019-09-04
That seems pretty outrageous that I would need to have a whole other wine folder just because it can't run two instances. Weird that it worked flawlessly for years, but as it gets newer, a major bug like this exists. I'm not really understanding what that "slot" directory would be in that stackoverflow example.

---

### Post by ramicio on 2019-09-04
Okay I copied my wine folder and gave it a different name. I won't be able to test it until later tomorrow, as I am encoding now, but only two videos. Tomorrow will be a run of many shorter ones. Thank you so far.

---

### Post by ramicio on 2019-09-05
This isn't going to work. I have no idea how to tell wine which prefix to use correctly. If I have one video that takes like 6 hours to encode, but have a bunch that take maybe an hour to encode, these slots will intersect. As an example, slot 1 takes 6 hours to encode, slot 2 and every other video takes an hour to encode. When the first slot 2 video is done, it becomes slot 1, then the next is slot 2, then the next is slot 1, and so on. I have no idea how to do this. Does forkmanager have some sort of slot variable?

```

$slot = 1;

my $pm = new Parallel::ForkManager( 2 );

foreach $key ( sort { lc $a cmp lc $b || $a cmp $b } keys %array ) {
    if( $slot == 2 ){ $slot = 1; } elsif( $slot == 1 ){ $slot = 2; }
    $pm->start and next;
    if( ! -e "/mnt/storage/videotemp/$key.hevc" ) {
        $cmd = 'WINEPREFIX=~/.wine64_'.$slot.' wine /mnt/storage/apps/avs2pipemod64.exe -y4mp "D:/videotemp/bluray/'.$key.'.avs" | x265 --input - --y4m --level-idc 5.1 --profile main10 --crf 19 --frame-threads 3 --pools 12 --frames '.$array{ $key }{ 'frames' }.' --output /mnt/storage/videotemp/"'.$key.'.hevc"'.( $argument =~ 'yes' ? ' >> /mnt/storage/videotemp/"'.$key.'.log" 2>&1' : '' );
        print "\n$cmd\n\n";
        exec($cmd);
    }
    $pm->finish;
}

$pm->wait_all_children; # Waits for all threads to be completed in the previous loop and closes the entire program what that is true.

```

---

### Post by ramicio on 2019-09-05
I am at my wit's end here and I please need help. I have been at this for hours and I cannot get a system to select the correct slot. Shorter jobs keep the slot number the same, and come time when the long job is over, the variable has been changed by the short jobs. I have tried this stupid "my" thing I keep seeing everywhere to try to keep that $slotnow variable exclusive to that one piece of loop, and I don't fully understand what it even does. Can anyone please help?

```

use Parallel::ForkManager;

@data = ( 10,4,20,2,15,6 );

%slot = ( '1' => 'unoccupied', '2' => 'unoccupied' );

my $pm = new Parallel::ForkManager( 2 );
foreach my $n (@data) {
    if ( $slot{ '1' } eq 'unoccupied' ) { $slotnow = '1'; $slot{ '1' } = 'occupied'; } elsif ( $slot{ '2' } eq 'unoccupied' ) { $slotnow = '2'; $slot{ '2' } = 'occupied'; }
    $pm->start and next;
    my $slotnoww = $slotnow;
    $slotnow = undef;
    print $slotnoww." sleep($n)\n";
    exec( "sleep $n" );
    $slot{ $slotnoww } = 'unoccupied';
    $pm->finish;
}
$pm->wait_all_children;

```

---

