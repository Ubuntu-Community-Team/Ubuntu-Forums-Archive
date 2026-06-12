---
title: "Help finding pictures that do NOT have EXIF Tags"
date: 2014-12-02
forum: General Help
---

### Post by hundred1906 on 2014-12-02
From a set of 20K+ images I want to find a copy out all those that do not have any tags set. Does anyone have a method I could use?

The reason for doing this is that the set includes many duplicates, which I can easily find using dupeGuru, but I only want to delete those that do not have tags set. Otherwise I will have to spend lots of time re-entering tags.
If I move everything that does not have a tag into a distinct directory I can quickly use dupeGuru to identify the specific files I can afford to lose.

---

### Post by nerdtron on 2014-12-02
Give details like sample file names and the exif tags file names and what you want to do with them. Maybe move them to a folder just to separate and sort or later on to delete.

---

### Post by Vaphell on 2014-12-02
OP, install *exiftool*, use it in terminal on few files and tell what's the difference in outputs between the haves and the have-nots. What's the tag(s) name differenciating between them, we'll figure something out once it is known.

---

### Post by papibe on 2014-12-02
Hi hundred1906.

I think you would need some scripting.

There are several command line tools to extract exif data. For instance:
[LIST]
[*]identify from the package imagemagick ([example]("http://www.imagemagick.org/script/identify.php")), and
[*]exiftool from the package libimage-exiftool-perl ([example]("http://hacktux.com/read/remove/exif")).
[/LIST]
Hope it helps. Let us know if you need more suggestions, or help with the script.
Regards.

---

### Post by hundred1906 on 2014-12-03
In hindsight I can see that the formulation of my question lacked some precision. The tags I am interested in show up in the Keywords field when I look at the properties of the image, via Nautilus. These keywords were placed there using f-spot. 
I assumed they were positioned within the EXIF structure but looking using exif I cannot see them, or they are within what is reported as a "Unsupported UNICODE string".

I'll first spend a while looking via imagemagic and exiftool as you suggest. Then maybe come back for some scripting help.

---

### Post by Vaphell on 2014-12-03
maybe try *exiv2* then, googling for 'f-spot exiftool' yielded this

[http://www.bluecedar.org.uk/?p=120](http://www.bluecedar.org.uk/?p=120)

---

### Post by hundred1906 on 2014-12-07
The bluecedar reference provided by Vaphell was most helpful and I have adapted the script there to give me a new prototype script that searches all my pictures to list all those with a zero length EXIF Subject field, which is where f-spot places keywords. This script works ok as far as it goes.

When I get this finished I will post the final script.

```
#!bin/bash
#
#
find /media/sf_pictures -type f -iname '*.jpg' |while read fname
do
 ssubject=$(exiftool -Subject "${fname}" | sed 's/^.*: //')
 if [[ -z "${ssubject}" ]] ;  then

   echo "$fname"
   echo "$fname" >>  /media/sf_temp_working/empties.txt
 fi
done
```

---

### Post by hundred1906 on 2015-01-08
The final script I used is below.

```
#!bin/bash
#
#
find <your file input location> -type f -iname '*.jpg' |while read fname
do
 ssubject=$(exiftool -Subject "${fname}" | sed 's/^.*: //')
 if [[ -z "${ssubject}" ]] ;  then

   echo "$fname"
   echo "$fname" >>  <your text output place>
  cp  -i --preserve=all --parents "$fname" <your output location>
#  rm  "$fname"
 fi
done
```

If you want to do something similar you need to be aware that this is my first script and it does not include any error checking or fail-safes. Back-up before doing anything significant with your picture files.

The 'find' statement goes to every file in your input location and tests to see if of type .jpg (case insensitive). The full name of the file drops into 'fname'.
Assuming it is a .jpg the exiftool utility is used to extract the 'subject' field into 'ssubject' which is then tested to see if it is blank (the -z operator), meaning that f-spot has not inserted any tag fields.
In which case the script echo's the name both onto the terminal and into a pre-created text output file for reference. next it copies the file and its directory structure onto your predefined output location.

Finally (assuming you remove the leading # comment field) it deletes (rm) the original. The effect being that any .jpg that do not contain tags in the exif subject field are moved to the output location.

Create your version of this script. Save it as a text file and run it from the terminal using "bash textfile". Try it first on a test directory! Note that it also picks up and moves lots of hidden .thumbnails.

In my case I used the original directory and the output directory as inputs into DupeGuru to identify picture files that were likely to be duplicates of each other. By knowing where the duplicates were located I could then ensure I only deleted the duplicates that did not have tags. I only need to do this once so I am not an expert and there are probably much better ways of achieving the same ends - only I did not find them.

After going through this whole process I switched from f-spot to digiKam - but that is another post!

---

