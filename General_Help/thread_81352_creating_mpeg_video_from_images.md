---
title: "creating mpeg video from images"
date: 2005-10-24
forum: General Help
---

### Post by munkiller on 2005-10-24
Owdie all im looking at writeing a bashscript to create a video of a bunch of images that get FTP'ed to my box (from wireless camera). First step need to get mplayer encoding the images to a video. Any one done this before (if so plz share)?

found this bit of script...

mencoder *.jpg -o output.mpeg -ovc lavc -lavcopts
vcodec=mpeg1video:vhq:vbitrate=1000 

down the road want the script to do the following.
- create a video of all images in a folder.
- name the file as a combination of first and last files (ie. images have date stamps on them)
- remove all the images after the encoding. (ie. only remove the file's that have been encoded, as the FTPing of the images does not stop).
- at a later stage want to export the video file into a DB (pref mysql) so going to have to place a restriction on the file size under 16mb as max-packet on mysql 16mb.

any tips.. welcome. 

thanX

---

