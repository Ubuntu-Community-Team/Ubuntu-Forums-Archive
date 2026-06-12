---
title: "TESSERACT 1.03: INSTALLATION, USE, AND BATCH PROCESSING on 6.10, Edgy Eft"
date: 2007-04-08
forum: General Help
---

### Post by secular on 2007-04-08
I've put together this how-to for myself. Since it looks fairly complete&#8212;and is all in one place&#8212;I'm posting it here benefit others new to Tesseract.

I borrowed/stole all of this mainly from two sources:
[http://ubuntuforums.org/showthread.php?t=361851&highlight=tesseract]("http://ubuntuforums.org/showthread.php?t=361851&highlight=tesseract")
and
[http://www.pclinuxos.com/forum/index.php?topic=19663.0]("http://www.pclinuxos.com/forum/index.php?topic=19663.0")

INTRODUCTION:
Tesseract is now an open source program with a history you can look up elsewhere. In my opinion it's the best open source ocr (optical character recognition) program. It reads text pretty well, but so far doesn't detect layout and formatting. I don't mind this, as I almost always just want plain text that that I can format my own way.  

It works only with TIFs, but there are instructions on the Web that show how to read PDF's. I haven't tried that because I use Abiword for grabbing text from PDF's.



[CENTER]**PART 1: BASIC SETUP AND INSTALLATION**[/CENTER]

**Step 1-Download Tesseract**

Download this program from: [http://sourceforge.net/project/downloading.php?groupname=tesseract-ocr&filename=tesseract-1.03.tar.gz&use_mirror=umn]("http://sourceforge.net/project/downloading.php?groupname=tesseract-ocr&filename=tesseract-1.03.tar.gz&use_mirror=umn")


**Step 2-Un-tar Tesseract**

Un-tar it so you have a folder named tesseract-1.03 . (I un-tarred it by right-clicking it and selecting &#8220;Extract Here.&#8221;)


**Step 3-Check Requirements**

Open Synaptic (or check with apt-get) to make you have the following files installed:
```
gs-common
```
```
libtiff4-dev
```


**Step 4-Basic Installation**

1. Open Terminal (Applications, Accessories, Terminal) and &#8220;cd&#8221; to the directory containing the un-tarred Tesseract folder. 
```
cd  /home/username/tesseract-1.03
```
(and press "Enter")

2. Once you've cd'd to the Tesseract folder, type the following command and press Enter:

```
./configure --with-libtiff=no
```

This may take a few minutes, and Terminal will show some messages.

3. In Terminal, type
```
make
``` 
(and press "Enter")

Wait a bit more for this to finish.

4. In Terminal, type 
```
sudo make install
``` 
(and press "Enter")

Wait a bit for this to finish.

5. In Terminal, copy some files:
```
sudo cp -R tessdata /usr/local/bin/
```
(and press "Enter")

6. In Terminal, change permissions on the directory you just copied:
```
sudo chmod 777 /usr/local/bin/tessdata
```
(and press "Enter")

**Step 5-Test the Basic Installation**
Still in Terminal, type:
```
tesseract phototest.tif out
```
(and press "Enter")

(This assumes that you are still in the following folder: /home/username/tesseract-1.03 )

You should see a file named out.txt in the folder names /home/username/tesseract-1.03 .





**[CENTER]PART 2: SETTING UP A SCRIPT FOR BATCH PROCESSING[/CENTER]**

Without a special script, Tesseract scans only one file at a time. I found at great script called ocube at [http://www.geocities.com/thierryguy/ ]("http://www.geocities.com/thierryguy/")that allows a person to scan all TIF files in a directory.

**Step 1-Get the Files**
You can get the files you need from [http://www.geocities.com/thierryguy/]("http://www.geocities.com/thierryguy/") . Look for the ocube section and download ocube.tar.gz. 


**Step 2-Un-tar the Files**
Once you've downloaded ocube.tar.gz, un-tar it. I did this by right-clicking it and selecting "Extract Here."


**Step 3-Modify (if you prefer)**
I modified one of the files in that download to suit myself. I changed the ocube file because the script transforms your files to 150 dpi, and I much prefer 300 dpi for scanning with Tesseract. If you'd like to do the same, open the ocube file  and find "-density 150x150". Just change the to "-density 300x300" and save the file.

**Step 4-Copy the Files to Other Locations**

1. Open Terminal and navigate to /home/username/ocube.tar.gz_FILES, typing:
```
cd /home/username/ocube.tar.gz_FILES
```
(and press "Enter")

2. In Terminal, copy the files to different locations, typing:
```
sudo cp ocube /usr/local/bin
```
(and press "Enter")

and typing:
```
sudo cp ocube.conf  /etc
```
(and press "Enter")

**Step 5-Change Permissions on the two files**
1. In Terminal, type:
```
sudo chmod 755 /usr/local/bin/ocube
```
(and press "Enter")

and type:
```
sudo chmod 755 /etc/ocube.conf
```
(and press "Enter")

**Step 6-Logout and then log back in **
I tried the tip below from ihavenoname, and logging out an then back in gets ocube to work.



**[CENTER]Part 3-Using Tesseract/ocube[/CENTER]**

***To use Tesseract on a single file***, just open Terminal and type:
```
tesseract path-to-file/filename.tif
```
(and press "Enter")
(I often cheat by opening the folder, selecting Go, Location, and copying the path to that folder. I then click cntrl-shift-insert to insert the path into Terminal.)

***To use ocube so Tesseract can perform ocr on a batch of files in a directory***, open Terminal and type:
```
ocube -f filename.txt path-to-file *.tif
```
(and press "Enter")

(Open ocube.txt in the folder ocube.tar.gz_FILES for complete instructions on commands and options.)


**[CENTER]Part 4: A Couple of Tips[/CENTER]**

Tip1: Tesseract only scans TIF files (not TIFF). There's a way to scan PDF's, and the instructions are here: [http://www.groklaw.net/article.php?story=20061210115516438]("http://www.groklaw.net/article.php?story=20061210115516438") . I tried this but didn't have the know-how to get it to work. I found that I can grab images from a PDF using Gimp and that I can grab text from a PDF using Abiword, so I don't think I would use this anyway.

Tip 2: My own scanning leads me to think that 300 dpi is best. I use XSane to scan, so set it to scan and save with the TIF extension. Also, in XSane, click on Preferences, Setup, and Filetype. There, change "TIFF Lineart Image Compression" to "none," as Tesseract will scan only uncompressed TIF's.


This completes the instructions. If anyone finds a mistake, let me know. I'll makes corrections in this post.

---

### Post by ihavenoname on 2007-04-08
rather than compliling this yourself you could try the debian package found here. [http://packages.debian.org/cgi-bin/search_packages.pl?keywords=tesseract&searchon=names&subword=1&version=all&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=tesseract&searchon=names&subword=1&version=all&release=all)

download tesseract-ocr and tesseract-ocr-data and install them both at the same time using dpkg -i tesseract-ocr*.deb (in the folder where you downloaded them.

(Feisty should have this in its repos too.)

---

### Post by secular on 2007-04-08
> **ihavenoname said:**
> rather than compliling this yourself you could try the debian package found here. [http://packages.debian.org/cgi-bin/search_packages.pl?keywords=tesseract&searchon=names&subword=1&version=all&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=tesseract&searchon=names&subword=1&version=all&release=all)

download tesseract-ocr and tesseract-ocr-data and install them both at the same time using dpkg -i tesseract-ocr*.deb (in the folder where you downloaded them.

(Feisty should have this in its repos too.)

That sounds great. Maybe the rest of my how-to will help others.

---

### Post by ihavenoname on 2007-04-08
> **secular said:**
> That sounds great. Maybe the rest of my how-to will help others.
It's helped me. I don't think those debs include the extra scripts you mentioned.  Also I think we can make a deb of ocube. Manually copying  files into your filesystem can get confusing when you  are trying to reinstall etc. 

You could probably get it to work by simply logging out and logging back in.

---

### Post by Jose Catre-Vandis on 2007-05-12
This is fantastic, a great addition to the office requirements at home and work!

A few notes:

If you use the debs to install (I did):

tessdata can be found here:
```
/usr/share/tesseract-ocr/tessdata
```
for when you copy to usr/local/bin

To run the test, you will need to find any tif file on your system, not that it will give any output if it is just a picture, but it will work.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The command to run tesseract requires an output file, so should read:
```
tesseract /path-to-file/filename.tif outputfile
```

and for ocube:
```
ocube -f outputfile.txt /path-to-file/*.tif
```

Oh, and I forgot to logout and in again, but ocube worked OK anyway, probably safer to do so though....

If I get time, I will write a little nautilus script so that you can right click on a tif file and set the thing running :-)

---

### Post by Jose Catre-Vandis on 2007-05-13
Simple nautilus script for single pages:
```
#!/bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI

  for arg

  do
	zenity  --info --title "OCR"   --text  "You are about to OCR  $arg
Please Wait For The Completion Dialog"

	tesseract "$arg" ${arg%.tif}out 
	rm -f *.map
	rm -f *.raw    
zenity  --info --title "OCR"   --text  "You Are Finished"
  done
```

Simply copy the text in the code box to a text file, save it as ocr-it or something you like. Copy the file to your nautilus scripts folder. Change permissions so that it is executable.

ocr-it will now show up in your scripts list on right click. The script gives your output file the same name as input but adds an "out" to the end, and you will note I have added extra bits to the script to delete the .map and .raw files also created. (This will remove all .map and .raw files in the working directory. Delete these lines if you do not need them. Ensure your files have the .tif extension. I have added a couple of zenity dialogs for info. You will need zenity installed for this to work

ocube:
```
#!/bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI



  for arg
  do
	zenity  --info --title "OCR"   --text  "You are about to batch OCR $arg
Please Wait For The Completion Dialog"
	ocube -f "$arg"/"$arg"out.txt "$arg"/*.tif  

zenity  --info --title "OCR"   --text  "You Are Finished"  
  done
```
Have fun :-)

---

### Post by t2000kw on 2007-06-06
If you add the multiverse and universe repositories (you'll need to decide if that's something you want to do), TESSERACT will show up in Synaptics for an easy installation. Haven't tried it yet, but it was an easy install, no compiling whatsoever.

---

### Post by ricardisimo on 2008-05-08
Here's a concrete example someone might be able to walk me through: The Pentagon got caught breaking the law (hard to believe, I know) and were required by the Freedom of Information Act to release [some pertinent documents]("http://www.dod.mil/pubs/foi/milanalysts/"). They promptly printed out all of them, then ran them through the Ditto Master from my 3rd Grade home room, stepped on them all for a few days, then scanned them and pasted them into 500-page PDFs, probably all askew at 17° angles. They are in bad shape, to say the least, and most certainly by design.

However, I have been able to "burst" each mega-PDF into one-page PDFs via pdftk (in the repositories), and then mogrify each of these into either a .pgm image (when I was trying ocrad) or now into .tiff files. All has been fairly sweat-free so far, but I will need help with the ocube part, so as to avoid scanning each of 10,000 pages by hand.

The other alternative is if some fine, dedicated anarchist out there would like to scan the above pages for me, and email me the results in plain text format... nah, I didn't think that would go over well.

I think the only part I'm missing is where I would find the Nautilus shell scripts folder that is mentioned above. Thanks in advance.

---

### Post by ricardisimo on 2008-05-09
I found the folder (it's in .gnome2) and I saved the script. Works like a charm! Thank yous to both secular and Jose Catre-Vandis.

The results are pretty good considering the poor quality of the originals. Has anyone tried the 2.03 version of tesseract from Google-Code? Is it worth trying to compile and install? I'm currently using the deb version (1.03) from synaptic. If someone can assure me that the results are dramatically better in one or the other I'll gladly select that version. I would need a bit of help on the make-install part of this. Thanks again.

---

### Post by travisn000 on 2008-05-16
> 
Step 1-Download Tesseract

Download this program from: [http://sourceforge.net/project/downl...use_mirror=umn](http://sourceforge.net/project/downl...use_mirror=umn)


The latest version (currently v2.03) is maintained by google; it can be found here:
[http://code.google.com/p/tesseract-ocr/]("http://code.google.com/p/tesseract-ocr/")

If you use v2.0+ you also have to download at least one language pack and put it in your tesseract-2.0+ directory.  The support of more languages seems to be the biggest change from previous releases..  

From release notes:
> 
Note that tesseract-2.00.tar.gz unpacks to the tesseract-2.00 directory. tesseract-2.00.<lang>.tar.gz unpacks to the tessdata directory which belongs inside your tesseract-2.00 directory. It is therefore best to download them into your tesseract-2.00 directory, so you can use unpack here or equivalent. You can unpack as many of the language packs as you care to, as they all contain different files.




> 
Step 3-Modify (if you prefer)
I modified one of the files in that download to suit myself. I changed the ocube file because the script transforms your files to 150 dpi, and I much prefer 300 dpi for scanning with Tesseract. If you'd like to do the same, open the ocube file and find "-density 150x150". Just change the to "-density 300x300" and save the file.


ALSO: [this little "study"]("http://groundstate.ca/ocr") found that 400 and 600 dpi greyscale gives the best OCR performance with Tesseract.  You may want to try these in place of those in step 3 above.

---

