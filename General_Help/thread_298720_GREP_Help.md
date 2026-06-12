---
title: "GREP Help"
date: 2006-11-13
forum: General Help
---

### Post by mattmole on 2006-11-13
Hi,

I have data from my weather station and I am trying to seperate the data into different days.

I have written a shell script to traverse through the file for every day and every month. I then write a directory structure with a file for each day of the year. These files are seperated into directories for each month.

Dir Structure

2006
---01
------0101.txt
------0201.txt
------etc
---02
------0102.txt
------0202.txt
------etc
---etc

The date column of the data file looks like this:
1112006
10112006
11112006

My problem occurs when using grep to search for each day. If I have data from the 1st of the month and the 11th as my script traverses through the data file it creates the file for the 1st and then when it searches for the 11th it overwrites the original data from the 1st.

How do I tell grep to search for the exact thing? Or do I need to use awk/sed and seperate the first two characters representing the day and just grep on those?

Thanks, Matt

---

### Post by Tomosaur on 2006-11-13
The data file should really follow a consistent format for the date. If a particular month/day is below 10, the date should still be shown in a 2/2/4 format, such as this:

11012006
or
01112006

this would mean each date code is unique, and would make sorting it much easier. At the moment, it would be possible for this to occur:

1112006 = 1st of November 2006
1112006 = 11th of January 2006

In a worst case scenario, your script may interpret the above as 11th of December 006, which is clearly no good, whereas the earlier examples mean this situation could never occur.

But yes, you will probably need to use awk/sed since the data is badly formatted.

---

### Post by mattmole on 2006-11-13
Yes, I agree with you that the format should be consistent. Unfortunately it isnt! Stupid thing!

Thanks!

Matt

---

