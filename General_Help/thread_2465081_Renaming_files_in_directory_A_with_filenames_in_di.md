---
title: "Renaming files in directory A with filenames in directory B"
date: 2021-07-21
forum: General Help
---

### Post by dauddaud1 on 2021-07-21
I have two versions of an album in two directories. The first contains files in .mp3 format.
The second contains the same tracks in .flac format.


The mp3 files are older and I have already renamed them to fit my preferred system.


I now want to switch to using .flac files but do not want to retype (or copy one by one) the filename from one directory to the other.


For example:
daud@debian:~/Music/Blues/ElmoreJames/Disc2$ ls -lh
-rw-r--r-- 1 daud daud 6.5M Sep 14 2020 01_2_TheSunIsShining.mp3
-rw-r--r-- 1 daud daud 5.4M Sep 14 2020 02_2_ICantHoldOut.mp3
-rw-r--r-- 1 daud daud 5.8M Sep 14 2020 03_2_StormyMondayBlues.mp3
...
drwxr-xr-x 2 daud daud 4.0K Jul 21 15:29 flac


daud@debian:~/Music/Blues/ElmoreJames/Disc2/flac$ ls -lh
-rw-r--r-- 1 daud daud 12M Jul 21 14:17 01 - The Sun Is Shining.flac
-rw-r--r-- 1 daud daud 9.7M Jul 21 14:18 02 - I Can't Hold Out.flac
-rw-r--r-- 1 daud daud 11M Jul 21 14:17 03 - Stormy Monday Blues.flac
...


***The desired outcome would be:***


daud@debian:~/Music/Blues/ElmoreJames/KingOfTheSlideGuitar/Disc2/flac$ ls -lh
-rw-r--r-- 1 daud daud 12M Jul 21 14:17 01_2_TheSunIsShining.flac
-rw-r--r-- 1 daud daud 9.7M Jul 21 14:18 02_2_ICantHoldOut.flac
-rw-r--r-- 1 daud daud 11M Jul 21 14:17 03_2_StormyMondayBlues.flac


***a.*** Can anyone kindly show me how to achieve this (explicitly)?
***b.*** Can anyone point me to an elementary source where I can learn to do this and other "filename manipulation" tasks.


Thanks
D2

---

### Post by dragonfly41 on 2021-07-21
I do not batch rename files  too often but looking at repo packages through Synaptic I see a number of packages if I search "rename".
I believe that Thunar has a batch rename plugin.
And also Krusader has this feature. I use Krusader regularly for file management and you can build your own UserActions.
A useful Python script is here .. [https://pypi.org/project/pyrename/](https://pypi.org/project/pyrename/)
That can run from command line if you do not want to install GUI such as Krusader.
There must be multiple other ways.

---

### Post by dauddaud1 on 2021-07-21
> **dragonfly41 said:**
> I do not batch rename files  too often but looking at repo packages through Synaptic I see a number of packages if I search "rename".
I believe that Thunar has a batch rename plugin.
And also Krusader has this feature. I use Krusader regularly for file management and you can build your own UserActions.
A useful Python script is here .. [https://pypi.org/project/pyrename/](https://pypi.org/project/pyrename/)
That can run from command line if you do not want to install GUI such as Krusader.
There must be multiple other ways.


Thx for responding.
I have no problem with (batch) renaming files.
What I wish to do is use the filenames (but not extensions) in one directory to rename files in another directory.
Regards
D2

---

### Post by dragonfly41 on 2021-07-22
You need to parse the filename into parts and then rebuild.
Python script does the job.
Here is a starter for one.
I leave you to add code to extract multiple filenames from a folder.

```

#!/usr/env/bin python3


import datetime


def parse(file):


    list1 = file.rsplit("_") # there are multiple "_" separators in string
    print(list1) # split
    mp3_name = list1[2]
       
    list2 = mp3_name.rsplit(".")
    print(list2)
    name = list2[0] # file name
      
    today = datetime.date.today()
    print(today) # prefix today's date
 
    flac_name = (str(today) + "_" + str(name) + ".flac")
    print(flac_name)
    return


file = "Sep 14 2020 01_2_TheSunIsShining.mp3" # example file
parse(file)

```


Tutorials:

rsplit:

[https://www.w3schools.com/python/ref_string_rsplit.asp](https://www.w3schools.com/python/ref_string_rsplit.asp)


date:

[https://www.w3schools.com/python/gloss_python_date.asp](https://www.w3schools.com/python/gloss_python_date.asp)


string concatenation:

[https://www.w3schools.com/python/gloss_python_string_concatenation.asp](https://www.w3schools.com/python/gloss_python_string_concatenation.asp)

---

### Post by dauddaud1 on 2021-07-22
> **dragonfly41 said:**
> You need to parse the filename into parts and then rebuild.
Python script does the job.
Here is a starter for one.
I leave you to add code to extract multiple filenames from a folder.

```

#!/usr/env/bin python3


import datetime


def parse(file):


    list1 = file.rsplit("_") # there are multiple "_" separators in string
    print(list1) # split
    mp3_name = list1[2]
       
    list2 = mp3_name.rsplit(".")
    print(list2)
    name = list2[0] # file name
      
    today = datetime.date.today()
    print(today) # prefix today's date
 
    flac_name = (str(today) + "_" + str(name) + ".flac")
    print(flac_name)
    return


file = "Sep 14 2020 01_2_TheSunIsShining.mp3" # example file
parse(file)

```


Tutorials:

rsplit:

[https://www.w3schools.com/python/ref_string_rsplit.asp](https://www.w3schools.com/python/ref_string_rsplit.asp)


date:

[https://www.w3schools.com/python/gloss_python_date.asp](https://www.w3schools.com/python/gloss_python_date.asp)


string concatenation:

[https://www.w3schools.com/python/gloss_python_string_concatenation.asp](https://www.w3schools.com/python/gloss_python_string_concatenation.asp)


Thx [COLOR=#000000]dragonfly41!
[/COLOR]I'll take this in and adapt it as necessary - the links look to be useful aids.

In the meantime, I have discovered that what I want is possible with the aid of EasyTAG.

For others:


1.  Create a text file containing the desired filenames
    [COLOR=#2E8B57][FONT=Monaco]ls *.mp3 / *.ogg etc. > filenames.txt[/FONT][/COLOR]

2. In EasyTAG, from the menu bar, Miscellaneous > Load Filenames From a Text File...  Fiddle around, then..

3.  Save

I think in the long run, a script I can run from a terminal will be the way to go, so I'll be working on your foundations, dfly. Thx again

---

