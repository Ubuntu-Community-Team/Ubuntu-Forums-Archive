---
title: "question about using jpegtran for lossless compression of jpegs"
date: 2006-10-09
forum: General Help
---

### Post by ewaguespack on 2006-10-09
I have been using a freeware windows application that strips all non
image info from a jpeg, here are the details:

[http://davidcrowell.com/jStrip/Default.aspx](http://davidcrowell.com/jStrip/Default.aspx)
Features

jStrip removes the following from JPEG files:

   * Comments (optionally)
   * EXIF Data (optionally)
   * JFIF Header (optionally)
   * Photoshop Image Resource Block (optionally)
   * ICC color profile
   * Adobe APP14 tag (optionally)
   * XMP data (optionally)
   * Extra bytes at end of file
   * Extra bytes or header at beginning of file
   * Extra bytes between JPEG blocks
   * Application-specific APPx blocks
   * Photoshop thumbnails
   * Any other unknown blocks in the JPEG files

jStrip also has the following features:

   * Option to retain original time-stamp of modified files
   * Ability to process a single file, or batch processing, including
recursing a folder tree
   * Option to attempt to clear read-only bit
   * Includes a full help file
   * Allows browsing and processing of UNC paths
   * A command line version for batch processing
   * Can change case of filenames, and change %20 and underscores to
spaces in filenames

in attempting to come up with a solution that does all of the above in
linux, I have played around with a couple of perl solutions, jhead,
exiftool, and jpegtran.

the best thing I have come up with so far is the following:
#jpegtran -optimize -outfile $image $image

or recursively:
# find -type f -name "*.jpg" -exec jpegtran -optimize -copy none
-outfile {} {} \;

other options I played with were the following:
# exiftool -all= $image
# jhead -purejpg $image

so, anyway to finally get to my point, the jpegtran (Linux) solution
does everything that jstrip (windows) does, (and more: optimize,
progressive) except remove the jfif header

so the question is, how do I remove the jfif header in a scripted,
recursive fashion in Linux.

If I am successful at finding a solution with this, it will finally
allow me to move completely to Linux.

finally, if you know where a forum / mailing list is that would be more appropriate, please let me know.

Thank you in advanced.

---

