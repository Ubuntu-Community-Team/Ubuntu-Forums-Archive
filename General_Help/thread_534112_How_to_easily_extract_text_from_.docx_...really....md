---
title: "How to easily extract text from .docx ...really..."
date: 2007-08-24
forum: General Help
---

### Post by woodsmoke on 2007-08-24
HI

I am in a rather irksome situation, I teach at a junior college, in that many of the PHDs are just to "busy" to take the time to send out their "missives" to all and sundry on the intra/internet by using the Gordian Knot of Microsloth Office 2007's function of "save as" to .doc or .rtf and instead just default to .docx...

I, know, it just such a BURDEN on them... so much to do...so little time in which to take naps.. :(

Anyway.... this was somewhat irksome when there were just a few Profs/admins with Vista machines, but since the j/c has gone full bore MSO07, we now get them daily..and it is just a PROBLEM...

Fortunately the STUDENTS know what is going on and actually send me their submissions in .doc or .rtf.... kids know "where it's at!" :)

But, I really did need access to these things there is a Debian packaged "reader" that I never could get to work in "another distro"... and now have it properly working...

But...still I couldn't "interact" with the information....like firing comments back at some fuzzy head that thinks he knows better than the rest of humankind, especially anyone that doesn't think like he thinks one ought to think... :)

The READER...only lets one do that...READ the text, you can't copy, paste, highlight nothing...

I've striven with this for months and happened on how to do it yesterday...

I've searched the forii but havn't found a similar item...if anyone knows of a previous such post I will be glad to edit this and provide a link.

The method is this:

A) double click the .docx file with Nautilus, or whatever file manager you use..,   which will perceive it to be an ARK/ZIP/TAR file, (it may appear as some other file type with another file system for another distro).
B) you will see quite a few folders with many of them "subheaded", that is because the .docx basically is...a Zip file of many things.  
C) Look about half way down through the files and find one named "document.xml" copy or drag the "document.xml"place to an appropriate place, (other than the ARK/ZIP/TAR) .. I dragged it to the desktop.
D) rename it with an appropriate name if you are going to do several, because they all have the same name.
E) double click it to open it in the file manager, and you will see the text.
F) highlight the text and copy and paste to a word processor.

If you have(had) paid any attention to Microsith's bullying and buying of multiple congress people in the U.S. to bribe them into using this instead of XML or ODF,..... AND had noticed the discussions in various forii a year or so back, now you know why the FOSS and Open Source people were so umbraged by what Microsith was doing....they took XML(extensible markup language) and coopted it with a patent that has been..UPHELD. in a U.S. court.... sheesh...](*,)

anyway...

Now that you know the "full way"... and know a little of the "why"...Microsith has just wrapped a perfectly good way of presenting information XML in an unreadable package... 

Here is a quicker way to extract the text.

First, place the .docx file...IN A FOLDER... then... within the folder, double click it.

The file manager then OPENS THE FOLDER... the reason being that the file managers in Linux are capable of opening XML files.

Inside you then just see three folders and a document... at least in THIS instance....

Two of the folders are the "stuff" that encapsulates the word doc and there is a folder called "word".

Click the file named "word" and you see  two folders and five documents.. one of them is labeled "document".xml.  One of them is labeled "web" which indicates the "roots" of the thing...XML... extensible markup language...

Click the document labeled "document.xml" and you can see the text which you can then copy and paste it into a word processor.

NOW HERE IS A CHALLENGE.....

Now that YOU have seen the above, let's discuss the .docx version of Microsith's Excel spreadsheet....

Inside it are three "sheets"....

I have no clue how to get "at" that information....

Maybe YOU.... or somebody you know, .... could now figure out how to get at that information for the benefit of those Linux folks, who, like myself, have to deal with this drek on a daily basis.

any comments APPREICATED...good,bad or indifferent...

and like I said, if this has been posted elsewhere tell me and I'll delete it..

woodsmoke

---

### Post by forestpixie on 2007-08-25
Did you see [this]("http://ubuntuforums.org/showthread.php?t=533564") thread - haven't had to go anywhere near these file types yet - maybe it'll work with xls as well? Really is just a guess ;)

---

### Post by Golyadkin on 2007-08-25
I simply open all .docx files with OpenOffice.Org, and they are editable and everything. Just "click" and done! 
This will help you set it up: [http://ubuntuforums.org/showpost.php?p=2352335&postcount=3](http://ubuntuforums.org/showpost.php?p=2352335&postcount=3)

---

