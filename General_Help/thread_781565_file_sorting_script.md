---
title: "file sorting script"
date: 2008-05-04
forum: General Help
---

### Post by -random on 2008-05-04
Yo! Is someone snazzy enough to write me a bash script that can sort loads of files based on their names into corresponding folders (also created by the script)?

Here's the story: 

So, ive deleted 3.8 Gigs of pics and successfully recovered them, and renamed them to year-month-day-time.jpg

(thanks to [http://www.shawnhermans.com/how-recover-lost-files-after-you-accidentally-repa](http://www.shawnhermans.com/how-recover-lost-files-after-you-accidentally-repa))
(for some reason i can't access this site, anyway i used
-
find
/media/data/recovery/jpg/ -name "2002*.jpg" | xargs -i mv {}
/media/data/recovery/2002/
-
to move all the 2002xxxx-xxxxxx.jpg files to the folder 2002)

Now i have all the files sorted in folders by year (2001,2002,2003....)

and would like the files within the year folders to be sorted into date folders

for example all the 20060101-xxxxxx.jpg pics in a folder called 20060101 (instead of the 2006 folder it's in now).

Any help would be great!!

Thanks guys!

---

### Post by -random on 2008-05-04
Ok, so iv'e written the following script:

#!/bin/bash
echo Enter the year plz
read YEAR
echo making directories...
cd /media/sdb1/recovered/jpg/$YEAR/
mkdir 01
mkdir 02
mkdir 03
mkdir 04
mkdir 05
mkdir 06
mkdir 07
mkdir 08
mkdir 09
mkdir 10
mkdir 11
mkdir 12
echo moving files...
find /media/sdb1/recovered/jpg/$YEAR/ -name "$YEAR01*.*" | xargs -i mv {} /media/sdb1/recovered/jpg/$YEAR/01/
find /media/sdb1/recovered/jpg/$YEAR/ -name "$YEAR02*.*" | xargs -i mv {} /media/sdb1/recovered/jpg/$YEAR/02/
find /media/sdb1/recovered/jpg/$YEAR/ -name "$YEAR03*.*" | xargs -i mv {} /media/sdb1/recovered/jpg/$YEAR/03/
find /media/sdb1/recovered/jpg/$YEAR/ -name "$YEAR04*.*" | xargs -i mv {} /media/sdb1/recovered/jpg/$YEAR/04/
find /media/sdb1/recovered/jpg/$YEAR/ -name "$YEAR05*.*" | xargs -i mv {} /media/sdb1/recovered/jpg/$YEAR/05/
find /media/sdb1/recovered/jpg/$YEAR/ -name "$YEAR06*.*" | xargs -i mv {} /media/sdb1/recovered/jpg/$YEAR/06/
find /media/sdb1/recovered/jpg/$YEAR/ -name "$YEAR07*.*" | xargs -i mv {} /media/sdb1/recovered/jpg/$YEAR/07/
find /media/sdb1/recovered/jpg/$YEAR/ -name "$YEAR08*.*" | xargs -i mv {} /media/sdb1/recovered/jpg/$YEAR/08/
find /media/sdb1/recovered/jpg/$YEAR/ -name "$YEAR09*.*" | xargs -i mv {} /media/sdb1/recovered/jpg/$YEAR/09/
find /media/sdb1/recovered/jpg/$YEAR/ -name "$YEAR10*.*" | xargs -i mv {} /media/sdb1/recovered/jpg/$YEAR/10/
find /media/sdb1/recovered/jpg/$YEAR/ -name "$YEAR11*.*" | xargs -i mv {} /media/sdb1/recovered/jpg/$YEAR/11/
find /media/sdb1/recovered/jpg/$YEAR/ -name "$YEAR12*.*" | xargs -i mv {} /media/sdb1/recovered/jpg/$YEAR/12/
cd /media/sdb1/recovered/jpg/

---
but when i run it all the files in the $YEAR folder are copied to .../.../.../$YEAR/12

?

any help plz.. i'm lost newbie!

---

### Post by Monicker on 2008-05-04
Give this a whirl.  I did some testing on my machine and it seems to work.  I don't have 3.8gb of pictures though.  :)

```
#!/bin/bash

YEARS="2005 2006"
# Add or remove years as necessary.

for year in $YEARS
	do
		
		for file in `ls $year`
			do
				day=${file:0:8}
				
				if [ ! -d $year/$day ]; then
					mkdir $year/$day
				fi
				
				if [ -f $year/$file ]; then
				
					echo "mv $year/$file $year/$day/"
					# Above is for a dry run, so you can see what will happen
					# without actually moving any files
					#
					# when ready to implement uncomment the next line
				
					#mv $year/$file $year/$day/
				
				fi
			done
	done

```


I'm assuming all the file names start with an 8 digit date (20060101).  Save it as MovePictures.sh or something, then "chmod +x MovePictures.sh" to make it executable.
[I]
Hrmm. Tried to tailor it more for you with a start dir, but that bombed.  It will still work if you run it from the directory where the year directories are at.[/I]

---

### Post by -random on 2008-05-04
omw yes it's beautiful!

all the pics are in 20060102-001625.jpg format (yearMonthDate-hourMinuteSecond.jpg)

Don't quiiiiiiiite get what exactly's going on but i'll figure it out..

Thanks a lot!:):):popcorn:

---

