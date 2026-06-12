---
title: "Launch a Program from ZIP format"
date: 2007-09-09
forum: General Help
---

### Post by Rosemere on 2007-09-09
I would appreciate if someone could give me the steps so I can use the following program.

First I went to Synaptic and installed 7zip. I have checked and it says it is installed. when I Click on applications I do not find it listed anywhere.

I downloaded the follwoing to Home folder but don't seem to find any directions on a Step by Step basis as to how Launch and use. Can anyone guide me?
Here is the program I downloaded.
    pdfsam-0.7sr1-out-scr.zip

---

### Post by prodigal on 2007-09-09
use apt-get to install ark or unzip. That should do the trick. Don't know much about 7zip

---

### Post by cjazz on 2007-09-09
Have you tried double-clicking or right-clicking on the file in Nautilus? That should allow you to open it with Archive Manager, which allows you to extract?

Alternatively, you can open a terminal and enter "unzip (filename)."

I don't know what the file is or where you got it, so I can help with further installation.

---

### Post by Rosemere on 2007-09-09
here is what I did, I am sure you are laughing re my level is so beginer. I just read a few Ubuntu Help pages and I still don't have it. I will show you what I put in Terminal and the answer;pete@pete-desktop:~$  # apt-get install pdfsam
pete@pete-desktop:~$ 
pete@pete-desktop:~$ sudo apt-get install pdfsam
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pdfsam
pete@pete-desktop:~$

---

### Post by prodigal on 2007-09-09
Are you running a desktop and want to be able to view pdf files? If so just go into the synaptic package manager and look in the sections related to graphics and utilities you'll find a pdf program in there that you can click and download without the command line involvement.

---

### Post by Rosemere on 2007-09-09
I have a PDF file that I want to be able to Open and delete some pages to make the file smaller as a lot of the pages are unnessary. 

This is why I was trying to install this application. I also know I have seen other zip type apps so I figured I would learn on this one. 

Yes I do has a Desktop.

---

### Post by mali2297 on 2007-09-09
Hello again.

Although I could walk you through how to setup pdfsam (I think), what about taking a look on the other program I suggested?

You can find [Pdftk]("http://www.accesspdf.com/pdftk/") in Synaptic (if you have enabled the universe repository). Although it is a command line tool, it has a good manual which you can view by typing *man pdftk*. Among other things it gives you an example of how to "delete" pages from a pdf document:

> 
       Remove &#8217;page 13&#8217; from in1.pdf to create out1.pdf
         pdftk in.pdf cat 1-12 14-end output out1.pdf
         or:
         pdftk A=in1.pdf cat A1-12 A14-end output out1.pdf


I hope this helps.

EDIT: Also, have a look at the [simple examples]("http://www.accesspdf.com/article.php/20041129175231241") given on the web site.

---

### Post by Rosemere on 2007-09-09
OK I give up but only partially. I checked and I have pdftk in synaptic and it says it is installed. Now how I run the application. sorry I am so new to this.

---

### Post by mali2297 on 2007-09-09
Assume that you have the file Example1.pdf in a folder Documents. You want to delete page number 2 and save the remaining pages in a new file Example2.pdf. Then open a terminal and type:
```

cd Documents
pdftk Example1.pdf cat 1 3-end output Example2.pdf verbose

```
and you are done.

If you would want to remove both page 2 and page 6, then type:
```

pdftk Example1.pdf cat  1 3-5 7-end output Example2.pdf verbose

```
Do you see the pattern? You tell the program which pages should be saved.

The last word *verbose* is optional, I added it so that the program will give you some feedback of what it has done.

---

### Post by Rosemere on 2007-09-10
No it hasn't worked yet.

I have the pdf file on my Desktop and I renamed it Example 1. Here is the response from Terminal.
pete@pete-desktop:~$ cd Desktop

pete@pete-desktop:~/Desktop$ pdftk Example1.pdf cat  1 3-5 7-end output Example2.pdf verbose

Error: Failed to open PDF file: 

   Example1.pdf

   OWNER PASSWORD REQUIRED, but not given (or incorrect)

Errors encountered.  No output created.

Done.  Input errors, so no output created.

pete@pete-desktop:~/Desktop$ 

Any idea what I should do?

---

### Post by mali2297 on 2007-09-10
Check that the file name is *Example1.pdf* exactly without spaces (you could have kept the original name and instead changed the command). 

Also, check that you have permission to both read and write the file. You can do that by right-clicking on the icon in the filebrowser and go to *Properties* (or something like that).  Alternatively, run
```
 chmod +rw Example1.pdf 
``` in the terminal.

The error *OWNER PASSWORD REQUIRED* seems a bit worrying. Apparently, PDFs may be encrypted so that a password is needed to view or edit the contents. If the file you are trying to edit is encrypted, you will probably have to use some other method for deleting pages. Are you allowed to print the document? In that case it should be possible to work it out. Of course, I assume that you don't have a suitable password to unlock the document.

First, see if the suggestions above solve the problem.

---

### Post by mali2297 on 2007-09-10
I just noticed that you had tried at least two different PDFs. Just to be sure, check a third PDF that you're certain isn't protected by encryption or anything like that. 

Also, check that the document has at least 8 pages so that the range *1 3-5 7-end* makes sense.

---

### Post by mali2297 on 2007-09-10
I doubt that your PDFs really are password-protected, but if they are you could try the following commands in the terminal:
```

pdftops Example1.pdf Example2.ps
pstopdf Example2.ps

```
and you will hopefully get a file Example2.pdf that you will be able to edit.

EDIT: Change pdftops and pstopdf to *pdf2ps* and *ps2pdf* respectively.

---

### Post by Rosemere on 2007-09-10
I decided to chenge my approach. I opened a File in Openoffice that was created by me on this computer and then I saved as a PDF. I have checked properties and no problem with access by me. 
I will show you what are my results from Terminal. These files are stored on the Desktop. 

One question when I click on Applications I checked there is no Access PDF but s ***there is  PDFedit.*** This program won't do what I want. Should I delete this program. 
I have also checked the Synaptic and PDF abd repositories are installed.
I hate to give up when I know something should work.  I don't believe spaces are a problem as I copied your line and just changed the file name. I have also looked at the web site and don't see any commands I wish to use. One last Question how should I start/load this program if I can't find an Icon or name anywhere?

Yes I can print and I will but I figured there was an answer and I appreciate all your time.

pete@pete-desktop:~$ cd Desktop

pete@pete-desktop:~/Desktop$ pdftk Setuptheatre1.pdf cat 1 3-end output Setupthetre2.pdf verbose

Error: Failed to open PDF file: 

   Setuptheatre1.pdf

Errors encountered.  No output created.

Done.  Input errors, so no output created.

pete@pete-desktop:~/Desktop$ chmod +rw Setuptheatre.pdf

pete@pete-desktop:~/Desktop$ pdftops Setuptheatre1.pdf Setuptheatre2.ps

Error: Couldn't open file 'Setuptheatre1.pdf'

pete@pete-desktop:~/Desktop$ pstopdf Setuptheatre2.ps

bash: pstopdf: command not found

pete@pete-desktop:~/Desktop$

---

### Post by mali2297 on 2007-09-10
> 
One question when I click on Applications I checked there is no Access PDF but s there is PDFedit. This program won't do what I want. Should I delete this program.
I have also checked the Synaptic and PDF abd repositories are installed.
I hate to give up when I know something should work. I don't believe spaces are a problem as I copied your line and just changed the file name. I have also looked at the web site and don't see any commands I wish to use. One last Question how should I start/load this program if I can't find an Icon or name anywhere?


The name of the program is pdftk. You have it installed otherwise you would have got an error like *command not found* in the terminal. It's a command line program only, which means that you run it in the terminal by typing *pdftk* followed by the actions you want it to make. There is no icon for it.


To simplify troubleshooting, let us work with the same PDF. Download this one:
[www.thejemreport.com/TLLG.pdf](www.thejemreport.com/TLLG.pdf)
and save it to the desktop.

Open a terminal and type
```

cd Desktop
ls

```
then you should see *TLLG.pdf* in the output. If that is alright, copy and paste the following:
```

pdftk TLLG.pdf cat 3-4 output Newfile.pdf verbose

```
Tell me the output of this.

EDIT:
For me, the output is
> Command Line Data is valid.

Input PDF Filenames & Passwords in Order
( <filename>[, <password>] ) 
   TLLG.pdf

The operation to be performed: 
   cat - Catenate given page ranges into a new PDF.

The output file will be named:
   Newfile.pdf

Output PDF encryption settings:
   Output PDF will not be encrypted.

No compression or uncompression being performed on output.

Creating Output ...
   Adding page 3 X0X  from TLLG.pdf
   Adding page 4 X0X  from TLLG.pdf

and I've now got a PDF named Newfile.pdf consisting of pages 3 and 4 from TLLG.pdf.

---

### Post by Rosemere on 2007-09-10
I guess there is something wrong with me as to entering data.  I followed your directions and I have the Newfile on the Desktop so here is my entry from Terminal:

pete@pete-desktop:~$ cd Desktop
pete@pete-desktop:~/Desktop$ ls
delete directions.rtf     Manuals           Shandong.pdf
 Documents                Newfile.pdf       TLLG.pdf
Example1.pdf              opera.desktop     Working Folder 
Explore-Top-100-2006.pdf  Setuptheatre.pdf
pete@pete-desktop:~/Desktop$ pdftk TLLG.pdf cat 3-4 output Newfile.pdf verbose
Command Line Data is valid.

Input PDF Filenames & Passwords in Order
( <filename>[, <password>] ) 
   TLLG.pdf

The operation to be performed: 
   cat - Catenate given page ranges into a new PDF.

The output file will be named:
   Newfile.pdf

Output PDF encryption settings:
   Output PDF will not be encrypted.

No compression or uncompression being performed on output.

As you will note the file I am trying to edit is Example 1. If I could delete the first "4" pages it would be great or split to 4 and 4. 


Just had an idea the pdf file I am playing with is in the Toronto Star Part 2 August 18th.  Maybe if you want to see try downloading directly to you computer. Must leave for and hour or two.


[www.thestar.com/fractionalproperties](www.thestar.com/fractionalproperties)

---

### Post by mali2297 on 2007-09-10
Alright, that file IS password-protected. Fortunately there is a workaround. 8)

Save the file 070818_fractional_properties.pdf on Desktop. Open a terminal and copy/paste each of the lines below in turn. Be patient, some commands may take a while.
```

cd Desktop
pdf2ps 070818_fractional_properties.pdf temp.ps
ps2pdf temp.ps
pdftk temp.pdf cat 5-end output Article070818.pdf verbose
rm temp.ps temp.pdf

```
The last command is just a cleanup.  Now you should have the file Article070818.pdf with the pages you have chosen.


Although there is a graphical user interface to almost everything in Linux, it is not a bad idea  to become familiar with the command line. A good start:
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Also, play with pdftk so that you learn how to use it!

---

### Post by Rosemere on 2007-09-10
Thank you, it worked and I was also able to create a file of pages 1-4. Now I will start and read some more of the web page you included.:)

---

