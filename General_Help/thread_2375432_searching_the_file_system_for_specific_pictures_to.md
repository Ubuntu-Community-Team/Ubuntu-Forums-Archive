---
title: "searching the file system for specific pictures to reupload to an image server"
date: 2017-10-24
forum: General Help
---

### Post by oddballmotorsports on 2017-10-24
OK,  so after photobucket, I have several forum posts which I want to make have pictures again.  I have since switched to imgur.  the problem is,  on long threads with multiple pictures I can't for the life of me remember which picture was which. I have all my photos on an external drive  so looking for a simple way to do this.  here's the idea I had.  take a specific forum post, take the info from the inspect which has the img src codes with the names of the files uploaded to photobucket.  for example

<img src="http://i1253.photobucket.com/albums/hh583/forwhalein/P1010020_zpseps3pa4d.jpg" border="0" alt>

isolate the "P1010020" and then search my external hard drive and all its subdirectories for that and say anything close within a few character's and output what it finds to a text file.  I would then have a road map to which pictures to upload to imgur.

is there a way to make a script or command that would read the entire source code and output automatically?  and if there is,  is it something simple(ish) a newb could do?  with the amount of ad's photobucket has now, it makes just browsing for 1 picture an hour ordeal.

---

### Post by SeijiSensei on 2017-10-24
I think the harder problem will be isolating your posts into one or more separate files, but I've never tried to download all my forum traffic.  I'm not even sure it's possible with vBulletin.

I can tell you how to extract the <img> URLs and get the strings you want.  Suppose all your posts are in a directory called "myposts", and each is saved as one or more HTML documents.  You could use something like this:

```

cd /path/to/myposts
grep 'img src' *.html | awk -F '/P' '{print $2}' | awk -F'_' '{print "P" $1}' >> list_of_images

```

When I apply that command to the URL you posted I get "P1010020".  When run with ">> list_of_images" appended it will write those numbers to a file named "list_of_images".

The command uses "grep" to find all lines containing "img src" in all .html files in the myposts directory.  It then sends ("pipes") those lines to the command "awk" which can parse strings using arbitrary boundaries.  The first awk returns all the text to the right of "/P" (represented by $2), and the second awk returns all the text to the left of the underscore ($1) with the "P" returned to its rightful place at the beginning of the string.

---

### Post by SeijiSensei on 2017-10-28
Did you see this at the bottom of my post?

If you ask for help, do not abandon your request. Please have the courtesy to check for responses and thank the people who helped you.

You're not going to get much help if you ask people for scripting assistance and never reply when you get it.

---

### Post by oddballmotorsports on 2017-11-02
sorry..  I've been wrapped up in other things,  I've got like 10 projects running right now in various venues.  this confuses me a bit to be honest,  I'm a novice at best..  I don't need the image names listed,  I can gather that from just looking at the source file.  but that does solve one half of the problem,  with that output file, with all the image names how i can read it and have a file that lists all the files specific paths,  and say the 2 closeset named files?  like say theres a p030441 in two different folders,  and a p0304411 because it had a same file name and had to be changed?  that's what I need..  but I would like to automate it...  as just the one post of mine has about 100 pictures..  and I realize that I have my pictures horribly organized on my external drive...

---

### Post by oddballmotorsports on 2017-12-19
update.  I have given away the only laptop I had with ubuntu to  a friend who needed something for writing college papers, in favor of a chromebook.  have since abandoned this quest (for now)..  honestly I think my skills limit my abilities, and need to learn the basics better before I can attempt this reload..    sorry for the slow response but I am spread very thin, and getting thicker.

---

