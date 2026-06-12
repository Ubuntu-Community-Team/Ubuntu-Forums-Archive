---
title: "transcode: AVI-&gt;DVD-MPG2 with ease"
date: 2005-04-03
forum: General Help
---

### Post by farnsworth on 2005-04-03
Hey guys,
I found this script a while ago, and I thought it would be useful for some of you.  It's a great script; a magical black box which transforms your avi/xvid/divx files into dvd-ready mp2s.  I've modified it slightly for use with ubuntu: transcode simply WILL NOT play nice with mplayer or ffmpeg on my system, and I've heard alot of people were having the same problems I had.

 ```

 #!/bin/sh

 # 01/2005 modified for ubuntu's lack of a working ffmpeg codec

 # ***************************************************************
 # This is a batch processing script for normalizing and converting
 # a mixed collection of .avi files into .mpg files that can be fed
 # to dvdauthor to create dvd's that will play perfectly on nearly
 # all NTSC dvd players and analog/digital televisions.
 #
 # A special feature of this script is the overscan compensation
 # based on laborious trial and error. Because I went to this
 # trouble your subtitles and/or supertitles will be visible
 # on even the most badly overcompensated television screen, but
 # you will not see deformed edges on a television that has 'normal'
 # overscan.
 #
 # The list of input files should be edited below, replacing 
 # file_01.avi, file_02 etc. with your batch of filenames.
 # No other editing is required.
 #
 # NOTE: This script takes it's input filenames from the
 #       command line if provided, otherwise it will use
 #       the list declared below on the 'files=' line.
 #
 # This script requires transcode, mplayer, sox, and toolame.
 #
 # Performance on my 2.8 GHz system is 30-40 fps conversion.
 #
 # copyright 2004 Phil Ehrens <phil@slug.org>
 # Valuable contributions by Adam Di Carlo <adam@onshored.com>
 # ***************************************************************
 # declare the list of root filenames to operate on. this is
 # the only line of this file that is edited for use. list the
 # names of all the files you want to process.
 # The source files will NOT be deleted.
 #
 # YOU MAY EDIT THE FOLLOWING LINE TO BE THE LIST OF INPUT
 # FILES IF YOU DO NOT WISH TO PROVIDE THEM ON THE COMMAND
 # LINE.
 #
 # For example:
 #
 #   files="file_01.avi file_02.avi file_03.avi file_04.avi"
 #
 
 files=""
 
 #
 # YOU DO NOT NEED TO EDIT ANYTHING BELOW HERE!!
 #

 # this block writes out the ffmpeg.cfg file with some
 # possibly useful values. Note that the lines in this
 # block must begin in text column zero or the script
 # will exit at this point!

 
cat > ffmpeg.cfg <<_EOF


[mpeg2video]
vhq = 1
vqcomp = 0.7
vqblur = 0.3
_EOF

 # Script will take input file(s) on the command line, or, if
 # no arguments are passed, will use the 'files' list declared
 # above. 

 [ ! -z "$1" ] && files="$@";

 for arg in $files ;

 do

 # strip the .avi, .mkv, .mov, or .ogm file extension

 file=`echo $arg | sed -e 's/\.[amo][vkgo][ivm]$//'`
 ext=`echo $arg | sed -e 's/^.*\.//'`

 # test for file existence

 if [ ! -f "$file.$ext" ];

 then

 echo "file '$file.$ext' doesn't exist" >&2
 exit 1

 fi

 # use mencoder to force frame rate to 29.970 all the way through.
 # this is because an avi may be a concatenated series of subfiles
 # each with a different frame rate, or even a single avi file
 # may have a varying frame rate in the worst case.
 #
 # the expectation that this will work with all sorts of non
 # avi input containers is naive at best. offering support
 # for container formats that support essentially arbitrary
 # stream content type is probably a mistake!

 mencoder -oac copy \
          -ovc copy \
          -ofps 29.970 \
          -o output.avi \
          "$file.$ext" > /dev/null 2>&1

 # input files of type .ogm and .mkv can have multiple audio tracks
 # and multiple (soft) subtitle tracks. to produce an output .avi
 # with a hard subtitle, it is at least necessary to re-encode while
 # specifying a subtitle track with the -sid option, i.e.:
 #
 # mencoder -oac copy \
 #          -ovc lavc \
 #          -lavcopts vcodec=mpeg4:vhq:v4mv:trell:vbitrate=3000 \
 #          -aid 0 \
 #          -sid 0 \
 #          -o $file.avi "$file.$ext" >& /dev/null
 #
 # note that, for didactic purposes, I have included the -aid option
 # which is used for the audio stream selection.
 # using this code will require changing the -i option of the
 # transcode invocation below from output.avi to $file.avi

 # At this point you can extract and make use of an ac3 audio
 # track by doing this and skipping all the other audio processing
 # steps:
 #        tcextract -i $file.avi -x ac3 > $file.ac3
 #
 # Remember to mplex the ac3 file!

 # dump the audio to a .wav file using mplayer

 mplayer -ao pcm \
         -vo null \
         -vc dummy \
         output.avi > /dev/null 2>&1

 # if the sound turns out to be 8 bit, then sox needs
 # extra options to handle it correctly.
 # thanks to Kenneth Stailey for this patch!

 file audiodump.wav | grep -qs 'PCM, 8 bit'
 if [ $? = 0 ]; then
    B=-b
    W=-w
 else
    B=
    W=
 fi

 # if the incoming sound is at 44100
 # upsample the sound to 48000.
 # here we rely on the fact that sox will abort if the input
 # frequency is 48000.
 # there will be a stub 44 byte long output.wav if sox aborts.

 if sox $B audiodump.wav -r 48000 $W output.wav resample ; then
    WAVFILE=output.wav 
 else

 # otherwise sound was already 48000

    WAVFILE=audiodump.wav
 fi

  # and make it into toolame mp2 format, nice!

  nice -n 20 toolame -p 2 -b 384 $WAVFILE output.mp2 > /dev/null 2>&1
  rm -f output.wav audiodump.wav

 # note the use of '-x mplayer,null' to remove export problems
 # imposed by bugs in ffmpeg that sometimes cause segfaults.
 #
 # the -j option here is intended to account for a phenomenon
 # of the NTSC standard and analog TV sets called 'overscan'.
 # the black borders created by this option will NOT be visible
 # on your TV screen unless the source .avi has already got
 # overscan compensation, which is HIGHLY unlikely.
 #
 # There is an additional interesting side effect of -j that can
 # be exploited. Using values that are no mod(8) seems to improve
 # the output quality quite a bit. Try using -j -18,-34,-22,-34.
 # Using non mod(8) values will slow down transcoding by about
 # 20%.
 #
 # note also that we add -e 48000,16,2 in the transcode invocation
 # forcing the sync adjustment to -1600@1000
 #
 # When encoding animated material, adding the option
 # -J hqdn3d will produce significant improvements in image
 # quality and an impressive decrease in file size!
 #
 # If your source has a 'washed out' appearance, you can
 # brighten it up with a gamma adjustment using the -G
 # option. A value of 0.9 or 0.8 will make quite a large
 # difference (in this case, 0.8 is a stronger correction
 # than 0.9).
 #
 # To create a 2-pass invocation (for significant quality
 # improvement with live-action material) simply make two
 # identical calls to transcode, but with the options
 # '-R 1,2pass.log' and '-R 2,2pass.log' in the respective
 # invocations.

 transcode --nice 20 \
           --print_status 500 \
           -e 48000,16,2 \
           --export_asr 2 \
           --export_fps 29.970 \
           --export_prof dvd-ntsc \
           -Z 720x480,fast \
           -j -16,-32,-16,-32 \
           -o output \
           -i output.avi \
	   -R 1,2pass.log

transcode --nice 20 \
           --print_status 500 \
           -e 48000,16,2 \
           --export_asr 2 \
           --export_fps 29.970 \
           --export_prof dvd-ntsc \
           -Z 720x480,fast \
           -j -16,-32,-16,-32 \
           -o output \
           -i output.avi \
	   -R 2,2pass.log

 rm -f output.avi

 # mplex supports constant sync offset correction.
 # '-O -300ms' would, for example, start audio 300 ms
 # earlier than otherwise.

 mplex -f 8 -o "$file.mpg" output.m2v output.mp2

 rm -f output.m2v output.mp2 ;

 # now you have .mpg files, all ready for dvdauthor.
 # like so:
 #          dvdauthor -t -o mydvd -c 0,11:30 file_01.mpg -c 0,11:30 file_02.mpg -c 0,11:30 file_03.mpg
 #          (and possibly -v ntsc+4:3+720xfull if you get errors
 #          and want to be certain that nothing funny happens.)
 #          dvdauthor -T -o mydvd
 #          mkisofs -dvd-video -o mydvd.dvd.iso mydvd
 #          dvdrecord -v -sao dev=0,0,0 driveropts=burnfree mydvd.dvd.iso

 done

 # end of script

```

---

