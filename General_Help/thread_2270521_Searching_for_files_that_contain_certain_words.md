---
title: "Searching for files that contain certain words"
date: 2015-03-23
forum: General Help
---

### Post by ross4 on 2015-03-23
I am running Xubuntu 14.04 with catfish installed.
A while back (>two years ago) I had to recover data from a disk full of XP files. The recovered files all have recovery names that tell me little or nothing about the actual contents, though they do tell me if they are .doc, docx .xls .xlsx etc. files. I now need to search for some old project files but when I try using the search function in Thunar, it does not find any words that I know exist within some of the files. 

To elaborate: In Thunar, I highlight a folder. Then I right-click and click on "Find in this folder". This brings up the Catfish window. I type in "racor" (because I know that word is within several files in the highlighted folder). The result is a list of several files with "racor" in the title. If I select the option of fulltext search then NO files are found at all. 

So it seems that catfish does not search within files. If this is NOT correct, what am I doing wrong? If this is correct, then could someone suggest an approach that will work.
Ross

---

### Post by dragonfly41 on 2015-03-23
I find that **searchmonkey** (see Ubuntu Software Centre for installation) is useful for searching text patterns in filesystem.

---

### Post by ajgreeny on 2015-03-23
I use Xubuntu 14.04 and have often used **recoll** to do exactly what you want, and so far it has always worked faultlessly.

---

### Post by oldos2er on 2015-03-23
> **ross4 said:**
> So it seems that catfish does not search within files. 

That is correct. Catfish is a GUI front-end for the CLI tools *locate* and *find*, neither of which search inside files. 

I second the recommendation for recoll, it is an excellent tool.

---

### Post by kjohri on 2015-03-23
Suppose you wish to find recursively all files in "my-directory" which end in .c and contain the string "fopen". You can run the following command from the shell,

cd my-directory
find . -name '*.c' | xargs grep "fopen"

---

### Post by CantankRus on 2015-03-23
I like **ack-grep** for searching for strings in files from a certain directory.
```
ack-grep <string> <directory>
```

eg search for  the string "xdpyinfo" in my scripts folder....
```
ack-grep xdpyinfo ~/scripts
```
shows the file name, highlights the searched string and shows the line number of the grepped string.
Searches recursively into subdirectories by default.
You will need to install **ack-grep**.

---

### Post by ross4 on 2015-03-24
Thank you all for responding. I decided to start out by trying recoll so installed it through the Ubuntu Software Centre. After figuring out how, generally, to use it, I discovered that it does not search Microsoft Excel worksheets of the .xls type. I am sure of this because I opened "myfile.xls" with Open Office libre and saved it as "myfile.xlsx". A search for the word "Ross" in the files in  the folder containing "myfile.xls" and the new file "myfile.xlsx" found "Ross" in the latter but nothing in the former. Is there an easy way to remedy this? A lot of my recovered files are .xls files.

---

### Post by oldos2er on 2015-03-24
For Excel files you will need to install xls2csv which is part of the package *catdoc*. Having never used xls2csv with recoll though I can't advise you further.

---

### Post by ross4 on 2015-03-25
Ann, Thank you for the information and thank you also for the link to the command line pdf. 
For others that have contributed suggestions, do any of you know for sure whether your suggested search procedures work on an excel .xls file? As I said, recoll works on .xlsx files but not on .xls files. I find, as a newbie to linux (only about a year now), when something doesn't work, I can't be sure if it just doesn't work (e.g. recoll, as initially installed, with .xls files) or it is not working because I have screwed up or misunderstood the procedure. So, it would be helpful to know ahead of time that one, or all, of the above suggested approaches does actually work with .xls files. If no one knows, I guess I'll try everything anyways but that is goind to take some time.
Thanks for everyone's help so far.

---

### Post by dragonfly41 on 2015-03-25
I did try recoll again yesterday (I remember trying it some time ago) but I decided to uninstall when the index files grew to be far too large - into GB's - filling up my disk.  There might be an option to limit index db size but I have not used recoll further.

I did try searchmonkey with some *.xls documents and it does not find text patterns in Excel cells.

Since I'm currently playing around developing a python tool requiring parsing *.xls files I have tried the code found in threads below to batch convert *.xls to *.csv  (note: where there are multiple worksheets multiple *.csv files are created).

[http://stackoverflow.com/questions/19833658/trying-to-convert-xls-to-csv-in-python](http://stackoverflow.com/questions/19833658/trying-to-convert-xls-to-csv-in-python)

[http://stackoverflow.com/questions/9884353/xls-to-csv-convertor](http://stackoverflow.com/questions/9884353/xls-to-csv-convertor)

The python code in above threads works nicely and could be refined  to scan in batch mode through each *.xls file, search the created *.csv files, and purge the *.csv files - that is if you don't want to fill up your disk with *.csv files.

You can then apply your searchmonkey search to the *.csv files for each *.xls file.

However a python programming approach rather than using an existing tool may not be what you want if you are new to Linux.

---

### Post by Holger_Gehrke on 2015-03-25
> **ross4 said:**
> For others that have contributed suggestions, do any of you know for sure whether your suggested search procedures work on an excel .xls file? As I said, recoll works on .xlsx files but not on .xls files. 

xlsx is xml in a zip-container, similar to open document files. xls is anything from the early nineties on, with several internal format changes. So a tool might read one xls-file but not another ...

---

### Post by ross4 on 2015-03-25
I re-installed recoll to include catdoc which also has xls2csv. This definitely allowed the reading of the .xls files that I recovered. After playing around with various setting, I also found that I could easily limit the indexing to the files on a thumb drive and, once a search was done, I could limit the files searched to the .xls files. Careful selection of the search words (included and excluded will help a great deal in sorting through the recovered files. The program outputs a list of the files in which the search words are found OR a table of these files. If I could figure out how to output this table to a text file I would be very happy. I'll work on this and if I find a way of doing it, I'll add it to the thread. I think, though, that I can mark the thread as solved.
Thanks again to all who helped.
Ross

---

