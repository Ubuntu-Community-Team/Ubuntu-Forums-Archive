---
title: "Extracting files from Amiga disk magazine &gt; Script needed &gt;"
date: 2023-11-20
forum: General Help
---

### Post by GeordieJedi on 2023-11-20
Hi there guys.

I was hoping that you could help me with an obscure problem that I'm trying to solve.


**Background:**
Like a lot of people my age, I grew up with, and love the Amiga range of computers.
(Linux is the closest feeling I get to using an Amiga these days).

(For those who may be unaware) BITD (before we had the internet) we used disk magazines
to store/distribute and display data and articles on floppy disks.

One of these was called Grapevine and it was one of the best diskmags ever made.

Myself and others are trying to convert these articles back into plain text / PDFs
So that they can be read much easier and without having to run an emulator.

However they were crunched down with Amiga archiving software called Powerpacker,
and then altered slightly to hide this, and obfuscate the archiving mechanism.
(So I can't just use Powerpacker on an Amiga emulator to recreate the files).


**Issue:**
I'm trying to -
2.1. Scan these files and strip out the individual articles.

2.2. Unpack /(de-crunch) some files.

I believe that once I have been able to extract the articles from the files
I will be able to put them into Powerpacker on the Amiga emulator,
unpack the files, then save each article individually.


**Troubleshooting:**
I have tried the following -

1. OCR using OCR reader = Terrible results.

2. OCR using gscan2pdf = Reasonable results. However you still need to do a lot of manual
clean up on each of the text files.

This would constitute a **massive** amount of work for the thousands of articles
that are in the complete set of Grapevine disks.

3. Looked at the files in a HEX editor

One of the guys on the EAB Amiga Forum has taken a look using a hex editor
and noticed the following details about the article files
```
$2 *bytes - Number of articles

[repeat for each article]
$2c bytes - Article title
$4 *bytes - Article offset in file
$4 *bytes - Article file size

rest.. *data files packed with powerpack with PP20 replaced with TXT!
```


He has also very kindly -

4.1. Created a Windows script/console app to do this (created using C#).
4.2. Provided the source code for this script/app (see attachment).

As a result I then tried -
5. Using the Windows console app but using -
5.1. A 32-Bit Wineprefix
5.2. A 32-bit Play on Linux install
Neither of which worked.


**Questions:**
Can you help create a bash script that would -

1.1. Scan the grapevine articles files.
1.2. Split out the articles from the file.
1.3. Change the header from TXT! back to PP (to denote that it's a powerpack file)

This should allow me to then use powerpacker to save each text file individually
so that we can obtain the separate text files, once again.

I was hoping that providing the source code would make this a whole lot easier
for the programmers amongst you.


**Useful extra details:**

GV.zip = The Windows CLI/app
Source code - For the Windows CLI/app (above)

Grapevine test file - (has the binary that contains the articles)
(Please note that this is not an actual .zip file. I had to rename it with a .zip extension
to allow me to upload it).

A MASSIVE TIA - for any help or advice.

---

### Post by MAFoElffen on 2023-11-20
I get an error with the file named "_GrapevineArticles#1*.zip"... Archive Manager says: "Error while trying to open archive..."

I was going to take a look at it but... Couldn't becasue of the above error.

---

### Post by dragonfly41 on 2023-11-21
These &#8220;obscure&#8221; challenges appeal.  I have a similar problem aiming to extract data from ancient 5inch floppy disks going back to Compaq days. And Omega Jazz drives.


However, to your challenge.
I started with the usual Google search term to kick off. I was pre-armed with the thought that these archives should be on the Wayback Machine.


&#8220;wayback machine Amiga grapevine articles&#8221;


[https://archive.org/details/grapevine-16](https://archive.org/details/grapevine-16)
Grapevine #16
by 
    [LSD]("https://archive.org/search.php?query=creator%3A%22LSD%22")
Publication date 
    [1993-07-29]("https://archive.org/search.php?query=date:1993-07-29")
Uploaded by   [denzquix]("https://archive.org/details/@denzquix")    on December 26, 2014
[https://archive.org/details/@denzquix](https://archive.org/details/@denzquix)
Grapevine was an Amiga disk magazine published by the group LSD that ran from 1991 to 1995.


Now the germ of an idea is to access such archives, through an automation process (rather more than a bash script).
When you have batch downloaded articles then begins the task of extraction of data (images and text).
I am inclined to leverage the powerful Wolfram Mathematica language. But there are other approaches.

I consulted Phind.com (an AI enabled browser) with these queries:

**query:** Today's challenge is to consider how to use Wolfram Mathematica language to extract data from url's, specifically Wayback Machine archives on Grapevine Amiga Magazine.


**question:** Could you please specify what kind of data you want to extract from the Wayback Machine?


**user:** Firstly text but also images if possilble to rebuild a modern day library. It would be helpful to index these through Zotero shared with others. Also concordance tool AntConc will be applied to the corpus.

...

And behold we have the first blueprint.

Now admittedly learning Wolfram language is quite a chunk of learning. But this mathematical engine is designed to extract data from archives. But it is not free.  You can evaluate the process.

You could use other stategies such as web url scraping the url's using Python with BeautifulSoup library.
But recruit an assistant like Phind.com (there are others) to help formulate a plan.
Wayback Machine is the entry point. Thereafter leverage AI and/or Python scripting.

I am focussing on learning Wolfram.

=========================================


To extend the experiment I downloaded the zip archive .


I found this
[https://github.com/fatpeppapig/adf-explorer](https://github.com/fatpeppapig/adf-explorer)
I use Krusader as my file manager since it has combined dual pane file explorer plus (optional) embedded command terminal.
I created a sandbox folder ~/ADF-EXPERIMENTS
I unzipped three files into sandbox.
I followed instructions .. using Krusader embedded terminal (Top bar > Tools > Show Embedded Terminal)
pip install -r requirements.txt
python main.py
This installs amitools.
I was able to explore the three archived *.adf files.

---

### Post by GeordieJedi on 2023-11-21
Hi there MAFoElffen

Thanks for taking the time to look into this issue for me

Re: Issues viewing the file - That's a bit strange.

TBF - I had to rename the file to GrapevineArticles#1.zip
In order to be allowed to actually upload the file to the forum / post.

I've included some screenshots to what it looks like on my system

If you rename the file to GrapevineArticles#1-
Then the file should show as an "unknown" format in Linux

But you should then be able to view it in either a Hex editor (screen shot 1)

Or if you pop it into an Amiga emulator, it should show as an Amiga bin file
(screen shot 2) showing how it appears my my FS-UAE Amiga emulated
A1200

---

### Post by GeordieJedi on 2023-11-21
@dragonfly41

I too like the obscure and interesting challenges

Wow ! Thank you for your detailed response.
And again, for taking the time to look into this issue for me.

It makes for interesting reading, and I'm very interested to see what results you find.

---

### Post by dragonfly41 on 2023-11-21
Must move on but hope it gives you some threads to follow. Incidentally I was Geordie born.

---

### Post by Holger_Gehrke on 2023-11-21
The program is written in C#, that means you need the .net runtime in Windows. On Linux you can use mono. By installing the package mono-mcs I got a c-sharp compiler and the mono-runtime. Then I compiled 'Program.cs' by running 'mcs Program.cs'. I ran the resulting Program.exe with the GrapevineArticles#1 file (./Program.exe GrapevineArticles#1) and got 83 files with the extension '.pp20'. The file-utility said those were PowerPacker 2.0 files. Searching for PowerPacker in apt (apt search PowerPacker) led me to a package named unar. Running unar on the first .pp20 file led to some readable ASCII text.

Holger

---

### Post by dragonfly41 on 2023-11-21
Another tool (Ubuntu) for *.adf files.

[https://amitools.readthedocs.io/en/latest/tools/xdftool.html](https://amitools.readthedocs.io/en/latest/tools/xdftool.html)

and

[https://amitools.readthedocs.io/en/latest/](https://amitools.readthedocs.io/en/latest/)

---

### Post by GeordieJedi on 2023-11-21
@Holger_Gehrke

Thanks for taking a look at this for me too.

I've followed your steps, however I'm getting a lot of resultant error messages

I have -

7.1. Downloaded and installed the whole Mono suite (including Mono mcs)

7.2. I have created a test dir that contains -

Program.zip
Program.cs
GrapevineArticles#1-

7.3. Built the Program.exe from the Program.cs using Mono mcs via the CLI

7.4. Code I ran to try and run the Program.exe from the CLI
```
./Program.exe GrapevineArticles#1-
```


However when I try to then run the Program.exe, I get the following error messages -

```

Grapevine article ripper

Extracking GrapevineArticles#1

Unhandled Exception:
System.IO.FileNotFoundException: Could not find file "/home/[my-user-name]/Documents/programming/GrapevineArticles#1-"
File name: '/home/[my-user-name]/Documents/programming/GrapevineArticles#1-'
  at System.IO.FileStream..ctor (System.String path, System.IO.FileMode mode, System.IO.FileAccess access, System.IO.FileShare share, System.Int32 bufferSize, System.Boolean anonymous, System.IO.FileOptions options) [0x001ef] in <12b418a7818c4ca0893feeaaf67f1e7f>:0 
  at System.IO.FileStream..ctor (System.String path, System.IO.FileMode mode, System.IO.FileAccess access, System.IO.FileShare share, System.Int32 bufferSize) [0x00000] in <12b418a7818c4ca0893feeaaf67f1e7f>:0 
  at (wrapper remoting-invoke-with-check) System.IO.FileStream..ctor(string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,int)
  at System.IO.File.ReadAllBytes (System.String path) [0x00000] in <12b418a7818c4ca0893feeaaf67f1e7f>:0 
  at GV.Program.Main (System.String[] args) [0x00061] in <34d8276890744542a3859d8312694d7c>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.IO.FileNotFoundException: Could not find file "/home/[my-user-name]/Documents/programming/GrapevineArticles#1-"
File name: '/home/[my-user-name]/Documents/programming/GrapevineArticles#1-'
  at System.IO.FileStream..ctor (System.String path, System.IO.FileMode mode, System.IO.FileAccess access, System.IO.FileShare share, System.Int32 bufferSize, System.Boolean anonymous, System.IO.FileOptions options) [0x001ef] in <12b418a7818c4ca0893feeaaf67f1e7f>:0 
  at System.IO.FileStream..ctor (System.String path, System.IO.FileMode mode, System.IO.FileAccess access, System.IO.FileShare share, System.Int32 bufferSize) [0x00000] in <12b418a7818c4ca0893feeaaf67f1e7f>:0 
  at (wrapper remoting-invoke-with-check) System.IO.FileStream..ctor(string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,int)
  at System.IO.File.ReadAllBytes (System.String path) [0x00000] in <12b418a7818c4ca0893feeaaf67f1e7f>:0 
  at GV.Program.Main (System.String[] args) [0x00061] in <34d8276890744542a3859d8312694d7c>:0 
[my-user-name]@falcon:~/Documents/programming$ (./Program.exe GrapevineArticles#1)
Grapevine article ripper

Extracking GrapevineArticles#1


Unhandled Exception:
System.IO.FileNotFoundException: Could not find file "/home/[my-user-name]/Documents/programming/GrapevineArticles#1"
File name: '/home/[my-user-name]/Documents/programming/GrapevineArticles#1'
  at System.IO.FileStream..ctor (System.String path, System.IO.FileMode mode, System.IO.FileAccess access, System.IO.FileShare share, System.Int32 bufferSize, System.Boolean anonymous, System.IO.FileOptions options) [0x001ef] in <12b418a7818c4ca0893feeaaf67f1e7f>:0 
  at System.IO.FileStream..ctor (System.String path, System.IO.FileMode mode, System.IO.FileAccess access, System.IO.FileShare share, System.Int32 bufferSize) [0x00000] in <12b418a7818c4ca0893feeaaf67f1e7f>:0 
  at (wrapper remoting-invoke-with-check) System.IO.FileStream..ctor(string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,int)
  at System.IO.File.ReadAllBytes (System.String path) [0x00000] in <12b418a7818c4ca0893feeaaf67f1e7f>:0 
  at GV.Program.Main (System.String[] args) [0x00061] in <34d8276890744542a3859d8312694d7c>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.IO.FileNotFoundException: Could not find file "/home/[my-user-name]/Documents/programming/GrapevineArticles#1"
File name: '/home/[my-user-name]/Documents/programming/GrapevineArticles#1'
  at System.IO.FileStream..ctor (System.String path, System.IO.FileMode mode, System.IO.FileAccess access, System.IO.FileShare share, System.Int32 bufferSize, System.Boolean anonymous, System.IO.FileOptions options) [0x001ef] in <12b418a7818c4ca0893feeaaf67f1e7f>:0 
  at System.IO.FileStream..ctor (System.String path, System.IO.FileMode mode, System.IO.FileAccess access, System.IO.FileShare share, System.Int32 bufferSize) [0x00000] in <12b418a7818c4ca0893feeaaf67f1e7f>:0 
  at (wrapper remoting-invoke-with-check) System.IO.FileStream..ctor(string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,int)
  at System.IO.File.ReadAllBytes (System.String path) [0x00000] in <12b418a7818c4ca0893feeaaf67f1e7f>:0 
  at GV.Program.Main (System.String[] args) [0x00061] in <34d8276890744542a3859d8312694d7c>:0  
```


N.B. I have edited this error message just to replace my actual name with [my-user-name]
That's the only change I have made to the error message

Questions:

1. Do you have any ideas why this is failing to provide the same extracted files that you can see ?

2. How did you run the Program.exe ?
Was it from the CLI ?
What commands did you use specifically ?

---

### Post by Holger_Gehrke on 2023-11-21
1. Yes, it's quite obvious why it doesn't work. It can't find the file GrapevineArticles#1 in the current working directory. I had the archive named as 'GrapevineArticles#1' in the same directory as the Program.exe. You either have it somewhere else or it's named something else. If it's somewhere else you can copy or move it into ~/Documents/programming or you can pass the path when calling the program (./Program.exe ~/some/other/directory/whatever_you_called_your_file)

2. I called it from the command line, exactly as I wrote: ```
./Program.exe GrapevineArticles#1
```The parenthesis you used are not a problem (commands in parenthesis are executed in a separate sub-shell), but aren't necessary. I only wrote it that way to separate the command from the text ...

While playing around with unar and the rest of the files, I found that some of the files won't unpack (specifically Amiga_Shopper_Show_pictures:_Part_1.pp20, Amiga_Shopper_Show_pictures:_Part_2.pp20, Castle_Conferance_invitation_pictures.pp20). So I looked online and found C-source for an unpacker at [http://aminet.net/package/util/arc/ppunpack10-mos](http://aminet.net/package/util/arc/ppunpack10-mos). After changing the compiler in the makefile (put 'gcc' instead of 'acc' in the line 'CC=acc') it compiled and at least produces output for these files. Still can't make heads or tails out of their contents, but at least there's content there since unar was producing empty files for these.

Holger

---

### Post by dragonfly41 on 2023-11-21
Is this helpful  ..

[https://archive.org/details/amigashopper-magazine?page=2](https://archive.org/details/amigashopper-magazine?page=2)

---

### Post by GeordieJedi on 2023-11-22
@Holger_Gehrke

Yes, I did see the error message, and you're right, the clue is in the name / error message

Howevever, I originally got the Grapevine files from PiMiga 1.5 MF edition
(IIRC comes from a TOSEC archive).

I copied the GV file over to my SSD, and it's currently copied to a few different locations, including -

A couple of different dirs on my HD
Actually on an Amiga emulated HDD within FS-UAE
A copy in my programming dir

It appears to be a hard link - see below

```
[user-name]@computer-name:~/Documents/programming$ ls -l /home/[user-name]/Documents/programming/
total 588
-rw-r--r-- 1 [user-name] 580262 Sep 13  1990 GrapevineArticles#1-
-rwxrwxr-x 1 [user-name] 4253 Nov 14 09:25 Program.cs
-rwxrwxr-x 1 [user-name] 6656 Nov 21 23:27 Program.exe
-rw-rw-r-- 1 [user-name] 1236 Nov 20 21:58 Program.zip
```

So unless Linux is doing something very strange with hard and soft links
I'm a bit confused.

I did also try renaming the file to -
GrapevineArticles#1 (no hypen at the end)

Re-ran the program, and got the same error message 


However.................

SUCCESS !!

I decided to (perma)-delete the file GrapevineArticles#1-

I got a brand new copy of the file, copied it to the programming dir,
then renamed it to "GrapevineArticles1"

Then I re-ran the Program.exe and it worked flawlessly !

I was then able to copy the 80 extracted files into a dir on my emulated Amiga.
Load Powerpacker, de-cruch the files and view them in ASCII.
After that I was able to save them out as ASCII .txt files

This has worked amazing well

Thank you to EVERYONE who has responded, with help and advice.


Thank you - You's are all Legends !

---

### Post by GeordieJedi on 2023-12-08
After posting on another forum, someone came up with a cracking little Linux program
that can unpack old archive files from a very large veriety of old computer OS's and platforms.

This is called Ancient (and in the main repositories)

So the next step in this project, is to take the 1st set of extracted files
(now in Powepacked format (.pp20) )

And run it through ancient to extract the powerpacked files to ASCII text files.

I've ran a couple of basic tests on individual files and it worked brilliantly.

Using ancient worked perfectly (even if the syntax is a bit weird).

So the next step is to knock together a basic bash script to automate this
whole process.

What I'd like to do is -

Scan a dir, (containing multiple of these separate and differently named powerpacked files).
Then either -

1. Use ancient to unpack the compressed Amiga data file (extension = .pp20)

1.1. Unpack it into the same dir, but have the output file named the same as
the original, but change the end of the output file to .txt

Or

2. Use ancient to unpack the compressed Amiga data file (extension = .pp20)

2.1. Unpack the output file into a different dir, and again change the the end of the output file
to .txt 

How would I go about doing this please ?

---

### Post by Holger_Gehrke on 2023-12-08
The normal way to run a program that only works with one file at a time with multiple files is a for-loop. This takes the form: for variable-name in list of files ; do list of commands done
The 'list of commands' is repeatedly executed. During each execution the named variable takes one of the file names from list of files as it's value. The list of files can (and should, for brevity's sake) contain wildcards.
So you need something like
```

for i in *.pp20 ; do ancient decompress "$i" "${i%%.pp20}.txt" ; done

```
In this code, "$i" is a parameter substitution which puts the value of the variable instead of the dollar-sign and the variable name and the "${i%%.pp20}.txt" is a more elaborate form of that (it replaces the variable with it's value,removes the 'pp20' at the end and replaces it with 'txt'. Sadly, ancient can't uncompress exactly the same files which were already problematic for unar (and which the "ppunpack" I found on aminet probably didn't uncompress correctly either).

Edit: To do the second variant (decompress into a different directory) you'd create the directory (in your file manager of choice or using mkdir) and put the path to the directory before the name for the unpacked file (e.g. ~/GrapevineUnpack/1/"${i%%pp20}txt").

Holger

---

### Post by GeordieJedi on 2023-12-08
@Holger_Gehrke

That bash script you just created, worked FLAWLESSLY !

You have saved me literally hundreds of hours of painstaking work !
I cannot thank you enough.

Regardless - Thank you once again for providing an excellent solution (and an outstanding explanation)
of the script and how it works.

I owe you (more than) a pint or two mate

Cheers !

---

### Post by GeordieJedi on 2023-12-11
Right - with the hard work of, and very talented people here on this forum
(Especially Holger_Gehrke)

I've been able to -

1. Extract the individual files into .pp20 (crunched) format. From each issue of
Grapevine issues 10-21

2. Convert these .pp20 files into plain ASCII text files.

3. Strip away the latent formatting codes from each text file.


So at the risk of sounding cheeky (and I'm genuinely NOT trying to be a nuisance !)

The final step is to name & number these articles according the way they were in the original
Grapevine diskmag, namely:

1).  GV-10-Article###-Name_of_article.txt
(the '###' represents the number allocated to the actual article (3 digit number).

I have a text file of this complete listing

Sample - GV issue 10:

```
005: Grapevine subscriptions 005
006: Important 006
007: Notice to Public Domain libraries 007
008: The future of Grapevine Pazza of LSD 008
009: The Grapevine Charts Torch of LSD 009
010: The Grapevine Guru Not The Momma 010
```

Is there any way to tie the names of the actual articles / text files to this list
and produce a final renamed text file ?

E.G. GV Issue #10
```
The_Grapevine_Guru.txt = (The actual name of the ASCII text file)
```

```
010: The Grapevine Guru Not The Momma 010 = (The name of the article in Grapevine)
```

2). So this would become:
```
GV-10_Article_010_The_Grapevine_Guru.txt
```

As "Not the Momma" is the author of the article


There are approximate 3,790 individual text files that need to be renamed according to
Grapevine's schema, and I can't do that manually / individually.

I've also uploaded the following files:
1. Grapevine issue 10 extracted text files
2. The text file that shows all the names of each article and it's corresponding article No 

This is so that people can see / use the ASCII text files and their named listing
to see if it's possible to create a final text file that is named correctly.


**Questions:**

Is there any way to:

1. Scan the dirs of the text files and the master list file for each issue.
2. Compare the names of the text files of the actual articles with the master list
3. Produce a final renamed text file for each article

I realise that this is not exactly easy (very bloody difficult more likely)
and may take a couple of steps / scripts to achieve (if possible at all)

Any help gratefully appreciated.

---

### Post by Holger_Gehrke on 2023-12-12
Interesting problem. Here's my attempt at a solution:
```

#!/usr/bin/env bash
# script to rename Grapevine text files according to an index of the articles
# two parameters
# - the name of the index file
# - issue number
#
# GV-ren gv_issue_10_article_list.txt 10

for i in *txt ; do
    # remove extension
    name=${i%%.txt}
    # get the article number by searching the index file for the file name and split off the number at the beginning of the line
    anr=$(grep -i "$(echo $name|tr "_" " ")" $1)
    anr=${anr%%:*}
    # if we have a number, rename the file
    if [[ -n "$anr" ]] ; then
        mv "$i" "GV-${2}_Article_${anr}_${name}.txt"
    fi
    echo
done

```
Save this in a file named GV-ren in the same directory as the text files and the index file and make it executable (chmod u+x GV-ren). Call it like this:
```

./GV-ren gv_issue_10_article_list.txt 10

```
giving the index file and the issue number as parameters. You might want to add a letter for the disk to the issue number (10a instead of 10 for the first disk, then 10b, 10c, ...) 

There's a two serious problems here:
[LIST]
[*]there's multiple articles with the same number in each index (I assume the magazine came on multiple floppies and the article numbers were unique on each disk but not for the set). This can be worked around by splitting the index files up so each file has only the names for one disk. 
[*]the file names are not exactly the same as the title in the index (e.g the filename is "About_The_Pennine_Amiga_club_user_group.txt" but the entry in the index is "About The Pennine Amiga Club Int. User Group"; the translation of '_' to space characters and the difference in capitalization is no problem, but the additional word ("Int.") is.) 
[/LIST]

Because of these - mostly because of the second - there are about 15 files it couldn't rename from the set I have from your previous post (disk 1 of Grapevine 10).
Holger

---

### Post by dragonfly41 on 2023-12-13
Exploring another scripting approach, Python can be used to split text strings, convert to JSON, and create catalogues.

On the problem of non matching strings these can be detected and presented for manual editing and cleansing in the workflow. This can be picked up by matching the text strings.

Python examples can be found in w3schools.com - Python tutorials.  Look for rsplit to break up long text strings into parts in a JSON file. The string parts can be indexed in a loop.
Multiline line blocks of text  strings should be contained between """ at start and """ at end. Spliiting at end of  each line by using "\n" as end of line separator.

Meld might be useful in command line mode.

---

### Post by GeordieJedi on 2023-12-13
Hi again Holger

1. You're absolutely right, the Grapevine diskmag usually came on 2-3 disks
for each issue. GV #10 was on x3 disks.

2. I have created article lists for each issue (from 10-21)

2.1. I have a master list that has every article and corresponding No on it
2.2. I then created sub lists, for each disk

2.3. Luckily from issue 11 onwards, the GV team decided to use some logic, and have a unique
number for each article across all disks, (so there is no repetition of articles Nos)
which has made your bash script infinitely useful.

3. I've used your (awesome) bash script, and been able to scan all of the issues (10-21).
I would say that it's close to providing 90% file renaming.
So I probably have a couple of hours of manual renaming to do now.


Holger - Sorry to sound like a stuck record. However your support has been absolutely invaluable
in helping me finish a project that started back in 2012 on another forum.

Your hard work and dedication (and technical skills are incredible).

I cannot thank you enough

Cheers pal !

---

### Post by GeordieJedi on 2023-12-13
@dragonfily41

That's really interesting - Thanks very much I'll take a look at that too

---

