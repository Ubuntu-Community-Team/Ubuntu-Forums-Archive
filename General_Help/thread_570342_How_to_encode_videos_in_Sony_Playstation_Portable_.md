---
title: "How to encode videos in Sony Playstation Portable format with subtitle?"
date: 2007-10-08
forum: General Help
---

### Post by zimmermannakos on 2007-10-08
How to encode videos in Sony Playstation Portable format with subtitle?

---

### Post by ThrobbingBrain66 on 2007-10-08
I use handbrake for encoding videos for my Ipod, and they have a preset for the PSP as well: [http://handbrake.m0k.org/trac/wiki/BuiltInPresets#psp](http://handbrake.m0k.org/trac/wiki/BuiltInPresets#psp)
Download (Linux CLI version):[http://handbrake.m0k.org/?article=download](http://handbrake.m0k.org/?article=download)

This command to use would look similar to this:

./HandBrakeCLI -i /media/cdrom0/VIDEO_TS -o ~/Movies/movie.mp4  -b 1024 -B 128 -R 48 -E faac -f mp4 -w 368 -l 208 -m -t 1 -s 1

Use the following link to read up on all the arguments and options: [http://handbrake.m0k.org/trac/wiki/CLIGuide](http://handbrake.m0k.org/trac/wiki/CLIGuide)

---

