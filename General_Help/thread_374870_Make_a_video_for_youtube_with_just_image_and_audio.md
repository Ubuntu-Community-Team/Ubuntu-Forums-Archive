---
title: "Make a video for youtube with just image and audio"
date: 2007-03-03
forum: General Help
---

### Post by peabody on 2007-03-03
I've been googling for 2+ hours and can't find anything that would provide an answer to what I think should be fairly trivial.  I don't have a cam that works, but I have a mic and I wanted to put something on youtube.  I frequently see video responses on youtube that consist of only a still image with an audio track.  I figured it should be easy to create something like this with Linux vid tools, but as previously stated, I'm fairly exhausted from searching and am now in need of advice.  Any help greatly appreciated.

I have seen several examples of either mencoder or ffmpeg being used to convert a folder of jpegs into a video, but not on how to stretch a single image out for a whole video.

I'm running dapper.

---

### Post by DagMan on 2007-03-03
This is going to be a bit of a naive post because I don't know what format youtube needs.  I also don't know which program provides the following, it isn't in the repos but if you follow a how to on installing tovid, which also is not in the repos but can be found in the tutorials section assuming it's been updated, then there is a tool called makemenu which makes a menu with an image and background music.  It will spit out an mpg file and audio I think in ac3 but you could convert it to whatever you needed from there.

These are the dependancies for tovid:
build-essential mplayer mencoder mjpegtools ffmpeg python python-dev python-wxgtk2.6 python-imaging imagemagick dvdauthor dvd+rw-tools vcdimager transcode sox normalize-audio txt2tags lsdvd python-cairo zenity automake1.9 subversion

You can see that some things there are for building tovid itself but I left them there in case you need to.  Something of one or more of the other packages provides what you need though and as for the makemenu program, it may just be a script that's part of the tovid package.  May as well just install tovid if you decide to go this way I think.

---

### Post by peabody on 2007-03-03
I have finally rolled my own solution.

it consists of the following python script used with mencoder:

```

#!/usr/bin/env python

"""
multiply.py by Sam Peterson <peabodyenator@gmail.com>

You will need an mp3 called 'audio.mp3' in the folder this script is
run from.  The path to the jpg file is a required argument to this
script.

The script will prompt you for how long the video should be.

You need mencoder.

Once done, the video is output to output.avi in the working folder.

this creates a ton of symlinks to a single jpg file, then uses
mencoder to encode video.  It then removes the symlinks.

WARNING, this will delete any files whose name is a number in the
working folder."""

import os, sys

if not os.path.exists('audio.mp3'):
    raise ValueError, "Missing audio.mp3 in folder."

filetype = os.path.splitext(sys.argv[1])[1]
secs = int(raw_input("Please enter a time in seconds: "))

for i in xrange(secs):
    os.symlink(sys.argv[1], "%08d%s" % (i, filetype))

# mencoder command to create a video
os.system('mencoder "mf://*.jpg" -mf fps=1 -o output.avi'
          ' -ovc lavc -lavcopts vcodec=msmpeg4v2:vbitrate=800'
          ' -audiofile audio.mp3 -oac copy')

# clean up
for each_file in os.listdir('.'):
    if os.path.splitext(each_file)[0].isdigit():
        os.unlink(each_file)

```

View the result here:
[http://www.youtube.com/watch?v=ZaIpOQypZng](http://www.youtube.com/watch?v=ZaIpOQypZng)

---

### Post by DagMan on 2007-03-03
That is a much simpler solution than mine.

---

### Post by peabody on 2007-03-05
I have found an even better way to do it, plus this new method creates files that don't seem to have the seeking problems my first video did.

The new script is available here:
[http://peabody.weeman.org/makevid.py](http://peabody.weeman.org/makevid.py)

I'm thinking of starting another thread on the Multimedia board to make some publicity for this and perhaps gain some suggestions.

---

### Post by jeroach on 2008-05-07
This is not a "solution".  Ubuntu is definitely not consumer ready if this is consider reasonable.  If anyone comes across a usable program that will do this, please let me know.

---

