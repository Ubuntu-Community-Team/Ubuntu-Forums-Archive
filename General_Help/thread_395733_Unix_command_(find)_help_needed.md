---
title: "Unix command (find) help needed"
date: 2007-03-28
forum: General Help
---

### Post by btrotter on 2007-03-28
Can someone please help me figure out what the command syntax I need to use is?

Here is what I am wanting to do.

I have hundreds of thousands of files I need to look for a specific search string in.
These files are spread across multiple subdirectories from one main directory.
I would like to find a way to search through all these files, and everytime it sees a file with this specific search string in it, make a note of it in a log file.

So, for instance, I have the directory /files/accounting/ 
Under /files/accounting, I have LOTS of Microsoft Excel files that I want to search for the specific string "\\cttrut04\dept\" and then everytime it finds a file by that name, dump it to a log file.

I thought about something like:

find /files/accounting/ -name "*xls" | more | grep -i "\\clttrut04\dept" > \log\filelog.txt

This doesnt work. I am not sure how to do a find and then feed each file name it finds to more to search it and then grep it for the search string.

Can anyone help with this?

Thank you,
Brian

---

### Post by hde on 2007-03-28
If you only searches in the file names for the string "\\cttrut04\dept\" then you can search it directly in find with something like this:

find /path/to/your/files -name "*\\cttrut04\dept\*"  > foundfiles.txt

---

### Post by btrotter on 2007-03-28
> **hde said:**
> If you only searches in the file names for the string "\\cttrut04\dept\" then you can search it directly in find with something like this:

find /path/to/your/files -name "*\\cttrut04\dept\*"  > foundfiles.txt


It is not the file name I am looking for, it is the contents of each file I need to search.
So for instance, I am going to have lots of files like file1.xls, file2.xls, file3.xls, etc.

I need to look at the contents of those files looking for a particular text sting of "\\cttrut04\dept\",  and then report which file (file1.xls, file2.xls, etc) contained that string.

---

### Post by miguelbmartinez on 2007-03-28
try 
find /path/to/your/files -depth | grep '.xls' > foundfiles.txt

should produce something similar to the following;
./docs/projects/S1/Prod/rgnprwb1_060809_0000.nmon.xls
./docs/projects/S1/Prod/rgnprwb2_060809_0000.nmon.xls
./docs/projects/S1/Prod/rgnprwb3_060809_0000.nmon.xls
./docs/projects/S1/Prod/rgnprws1_060809_0000.nmon.xls
./docs/projects/S1/Prod/rgnprws2_060809_0000.nmon.xls
./docs/projects/S1/Prod/rgnprws3_060809_0000.nmon.xls
./docs/projects/S1/Prod/rgnprws4_060809_0000.nmon.xls
./docs/projects/S1/Prod/rgnprws5_060809_0000.nmon.xls
./docs/projects/S1/Prod/rgnprha1_060809_0000.nmon.xls

Where the initial . = /path/to/your/files

---

### Post by miguelbmartinez on 2007-03-28
OK, you want to search internally...
try this
find . -depth -exec grep checkwinsize {} + 

but make sure you have access to all directories, etc. since if you don't you will have to parse the txt file that you end up creating to get rid of entries similar to the following;

find: ./.gnome/accels: Permission denied
./.bashrc:shopt -s checkwinsize
grep: ./.Xauthority: Permission denied
grep: ./.gnome2/totem-addons/README: No such file or directory
grep: ./.gnome/accels: Permission denied
grep: ./.mozilla/firefox/gxug9hsr.default/lock: No such file or directory
grep: ./.viminfo: Permission denied
grep: ./.bash_history: Permission denied
grep: ./cxoffice/bin/notes: No such file or directory
grep: ./cxoffice/bin/nminder: No such file or directory
grep: ./cxoffice/bin/desktopmgr: No such file or directory

---

### Post by hde on 2007-03-28
> **btrotter said:**
> It is not the file name I am looking for, it is the contents of each file I need to search.
So for instance, I am going to have lots of files like file1.xls, file2.xls, file3.xls, etc.

I need to look at the contents of those files looking for a particular text sting of "\\cttrut04\dept\",  and then report which file (file1.xls, file2.xls, etc) contained that string.

okay, then you can use grep alone, something like this

grep -r \\cttrut04\dept\ *xls > interestingfiles.log

it will grep recursively from the directory you are in.

---

### Post by hde on 2007-03-28
> **hde said:**
> okay, then you can use grep alone, something like this

grep -r \\cttrut04\dept\ *xls > interestingfiles.log

it will grep recursively from the directory you are in.

ah, that won't work I think (the *xls bit), better like this:

find . -name "*xls" | xargs grep \\cttrut04\dept\ > file.log

---

### Post by btrotter on 2007-03-29
That looks like it is working, thank you!

---

