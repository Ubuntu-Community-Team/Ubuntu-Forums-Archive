---
title: "Please recommend an easy to install laser printer"
date: 2016-02-16
forum: General Help
---

### Post by Tom_Carr on 2016-02-16
I bought a brother HLL2320D laser printer.  I pluged it in with the usb cable.  I went to printing/add printer.  It searched for drivers and could not find one.  I recommended that I use the generic text only driver, which I did.  It tried to print a test page and could not.  I don't remember the error message it gave.  Now when I try to print, nothing happens.

I have had printers in the past that I just plugged in and they worked perfectly.  I can take this one back to Staples and get a refund.  Can you recommend a good laser print that you know has available drivers for ubuntu?  

I am running ubuntu 12.04.  Could that be the problem?

---

### Post by newbie-user on 2016-02-16
Get the driver from the Brother website: [http://support.brother.com/g/b/downloadtop.aspx?c=us&lang=en&prod=hll2320d_us_as]("http://support.brother.com/g/b/downloadtop.aspx?c=us&lang=en&prod=hll2320d_us_as"). They provide a .deb file to install.

I have a strong preference for HP printers. They have good linux drivers. That said, I used to have a Brother printer, and that worked well in linux as well.

---

### Post by Tom_Carr on 2016-02-16
I see where I can download a driver for the printer I have, but I would rather get a printer that does it all automatically for me.
I am embarrassed to say that after all the time I have been using ubuntu I don't know how to install a driver.

---

### Post by pqwoerituytrueiwoq on 2016-02-16
if the deb provided by brother actually works, double click the file and it will let you install it from the software center
if you want a printer that works out of the box for the most part HP printers do that, sometimes you can find a printer that is too new to have the driver preloaded, if that happens upgrade the OS or get the driver here:
[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

---

### Post by kurt18947 on 2016-02-16
Brother supplies an installer script that works pretty well. It can be downloaded here:

[http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hll2320d_us_as&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hll2320d_us_as&os=128&dlid=dlf006893_000&flang=4&type3=625)

It does have to run from a terminal though. Brother's linux install directions are rather behind the times IMO. Even if I don't use their tool, i just download the .deb files and install them, LPR first then CUPS. All the pre required procedures mentioned here:

[http://support.brother.com/g/s/id/linux/en/before.html?c=us_ot&lang=en&redirect=on#004](http://support.brother.com/g/s/id/linux/en/before.html?c=us_ot&lang=en&redirect=on#004)

seem unnecessary with newer Ubuntu releases.  If you're just annoyed with Brother, i bought a Samsung Multi-function laser and was able to install it without downloading anything, just using the included printer installer.

---

### Post by newbie-user on 2016-02-17
> **Tom_Carr said:**
> I see where I can download a driver for the printer I have, but I would rather get a printer that does it all automatically for me.
I am embarrassed to say that after all the time I have been using ubuntu I don't know how to install a driver.

It's okay. I'm not a fan of installing drivers either. That's why I prefer HP printers, as their drivers are fairly up-to-date. However, you are using 12.04, so you probably will be missing drivers for newer printers. Upgrading your OS may help with the driver issue, but it's sometimes good to get drivers from the manufacturer.

---

### Post by Tom_Carr on 2016-02-17
> [COLOR=#000000] However, you are using 12.04, so you probably will be missing drivers for newer printers. 

[/COLOR]

When I tried to install the printer, it said it was  searching for drivers.  I thought that meant it was going online to look for a driver and that the version of the OS did not matter.  Maybe I don't understand exactly what is going on.

I think I am going to return the Brother printer and get an HP, since several people have suggested that.
If the old operating system is a problem I could go ahead and install the newest ubuntu.  Also I have a box running Mint 17 that I could use to test.

Now I am just playing with it to see if I can get the brother to work, even though I know I will probably return it and get an HP.

I went to the download driver page and it listed 5 different downloads. 

[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2320d_us_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2320d_us_as&os=128)

I had no idea which to use, so I just picked one of  the newest ones  

CUPSwrapper printer driver (deb package)	04/02/2015

I downloaded it and clicked on it and the software center came up and let me install it (I learned something new!)

There is a page that lists intall instructions from the terminal.  
[http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=hll2320d_us_as&os=128&dlid=dlf101909_000&flang=4&type3=561](http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=hll2320d_us_as&os=128&dlid=dlf101909_000&flang=4&type3=561)
Am I correct in assuming that is all done by the software center?

I then opened "printers", deleted the old install of the the brother printer, then added it again.  This time everything went smoothly, but the printer still doesn't print.  It just hangs on "Sending data to printer"

At [http://localhost:631/printers](http://localhost:631/printers)   it says:  Idle - "Sending data to printer."

---

### Post by 1clue on 2016-02-17
Just as a point of information, I have a Canon color all-in-one laser (MF8050Cn) networked in my house.  It has been a massive pain in the rear to get working on absolutely every computer I've hooked up to it.  Oddly enough, my wife's Windows 10 laptop (windows 8/8.1 before) was the worst of all.  Quite often my Ubuntu box has been the only thing that could print to it.  Also, at the moment anyway, Ubuntu is pretty easy to set up now that they have drivers in the repository for it.

I strongly recommend a networked laser printer which has well-maintained Linux drivers as of the time you buy the printer.  HP has had good Linux support for years, but if you have a Mac they can be problematic.  I might give them a try next time, it's been quite awhile since I had an HP printer.

You might also be interested in printing from mobile devices.  My printer does not support this.

---

### Post by kurt18947 on 2016-02-17
> **Tom_Carr said:**
> Now I am just playing with it to see if I can get the brother to work, even though I know I will probably return it and get an HP.

I went to the download driver page and it listed 5 different downloads. 

[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2320d_us_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2320d_us_as&os=128)

I had no idea which to use, so I just picked one of  the newest ones  

CUPSwrapper printer driver (deb package)    04/02/2015

I downloaded it and clicked on it and the software center came up and let me install it (I learned something new!)

There is a page that lists intall instructions from the terminal.  
[http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=hll2320d_us_as&os=128&dlid=dlf101909_000&flang=4&type3=561](http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=hll2320d_us_as&os=128&dlid=dlf101909_000&flang=4&type3=561)
Am I correct in assuming that is all done by the software center?

I then opened "printers", deleted the old install of the the brother printer, then added it again.  This time everything went smoothly, but the printer still doesn't print.  It just hangs on "Sending data to printer"

At [http://localhost:631/printers](http://localhost:631/printers)   it says:  Idle - "Sending data to printer."

I don't recall details re installing Brother printers on 12.04. You may need some of the pre-install steps I mentioned earlier.  If it were me, I'duninstall Brother's .deb file - there should be an uninstaller in the same folder as the .deb files then download and run the installer. The installer should download and install any additional packages required in addition to the Brother .deb files. You will need to do this from an account with SUDO privileges which is typically the first account after installing. If you're able to download the script open a terminal, navigate to the folder where the downloaded script is e.g. Downloads then type  

```
sudo bash linux-brprinter-installer-2.0.0-1
```

and press enter. You'll be prompted for the machine's model - HL-L2320D. Type that and press 'enter'. It should then offer to download the required drivers and any additional required packages. You'll need to type 'y' to accept the license(s). It will download and install the required stuff. There is an earlier version of the printer installer which is linux-brprinter-installer-1.x.x.x. It works as well.

I've had pretty good luck with the installer script configuring connections. How are you connecting? USB? Network? I also install the package "system-config-printer" from the repositories. It is included by default in Xubuntu & Lubuntu among others. The printer app included with Ubuntu & Ubuntu-gnome is not nearly as informative. You run "system-config-printer" by pressing alt+f2 then entering the name in the box.

It may suit you better to return the Brother and purchase another printer, nothing wrong with that.

---

### Post by newbie-user on 2016-02-17
> **Tom_Carr said:**
> 
I had no idea which to use, so I just picked one of the newest ones  

CUPSwrapper printer driver (deb package)	04/02/2015


For Brother printers, you need both the CUPS and LPR drivers. With all operating systems in general, you'll generally have to go find the driver for newer printers.

---

### Post by dennis54 on 2016-02-17
I'm unable to get my Epsom stylus TX200 printer to work on ASUS laptop using Ubuntu. It recognises it, but won't print or show ink levels. Any advice would be most welcome. I am running version 15.10 and it wouldn't work on the 15.04 version either. HELP!!!!!!!!!!!!!!

---

### Post by Bucky Ball on 2016-02-17
Don't test on Linux Mint if you are after help in this forum section. Mint is not officially supported here, only in the specific area 'Mint'. They have a very active forum which would be a better place to post for support in Mint.

Download the Brother Installer Tool [from here]("http://support.brother.com/g/b/downloadhowto.aspx?c=us_ot&lang=en&prod=hll2320d_us_as&os=128&dlid=dlf006893_000&flang=4&type3=625") and simply follow the instructions. Pretty straight forward. Or you simply download [the two .deb files underneath it here]("http://support.brother.com/g/b/downloadlist.aspx?c=us_ot&lang=en&prod=hll2320d_us_as&os=128"), CUPS Wrapper and Generic LPR (the .deb files), double click them, to install with Software Centre. Easy.

Once you've installed the drivers either way, simply 'Printers> Add Printer'. When you get to the driver section, choose 'Brother' and scroll down the list. Your driver will be there, choose it, proceed, print a test page. Done. Brother make great printers (possibly why you bought it) so taking it back is kinda severe and a shame. They are also, along with HP, one of the printer manufacturers that plays real nice with Linux (no offense intended, but their drivers are just about the easiest to install). 

12.04 LTS is still fully supported and would have nothing to do with this.

---

### Post by kurt18947 on 2016-02-18
> **newbie-user said:**
> For Brother printers, you need both the CUPS and LPR drivers. With all operating systems in general, you'll generally have to go find the driver for newer printers.

And order matters. LPR first then CUPS I believe.

---

### Post by Tom_Carr on 2016-02-19
> [COLOR=#000000]Download the Brother Installer Tool [/COLOR][from here]("http://support.brother.com/g/b/downloadhowto.aspx?c=us_ot&lang=en&prod=hll2320d_us_as&os=128&dlid=dlf006893_000&flang=4&type3=625")[COLOR=#000000] and simply follow the instructions. [/COLOR]

I got to step 5. 

[COLOR=#000000][FONT=sans-serif]Step5. Run the tool:[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif][B]Command: bash linux-brprinter-installer-*.*.*-* Brother machine name

[/B][/FONT][/COLOR]What should I put in for the Brother machine name? It is a model HL-L2320D, but I don't know if I should enter it exactly that way, in upper or lower case, or what.

---

### Post by Bucky Ball on 2016-02-19
The version number of the installer you downloaded is all that is required. If you cd to the folder you've downloaded to, for instance, if in 'Downloads' then:

```
cd ~/Downloads
```

Then

```
dir
```

You should see the brother installer there with the version number on the end. Just copy that, or copy the name of the file and plop it where it says 'linux-brprinter-installer ...... etc.'

Hit enter. :)

You should be doing all instruction when in the folder you have downloaded to (probably Downloads so 'cd ~/Downloads'). The installer will take care of the rest (e.g. the right driver for your printer).

---

### Post by Tom_Carr on 2016-02-19
Bucky, thanks for all your help, but I am really confused.  I did what you said here:

> [COLOR=#000000][COLOR=#000000]*Download the Brother Installer Tool *[/COLOR][/COLOR][from here]("http://support.brother.com/g/b/downloadhowto.aspx?c=us_ot&lang=en&prod=hll2320d_us_as&os=128&dlid=dlf006893_000&flang=4&type3=625")[COLOR=#000000][COLOR=#000000]* and simply follow the instructions.*[/COLOR][/COLOR]

Then I did  what you said in the last post, and this is what I got in the terminal:  

```
tom@tom-OptiPlex-755:~$ cd Downloads
tom@tom-OptiPlex-755:~/Downloads$ gunzip linux-brprinter-installer-*.*.*-*.gz
tom@tom-OptiPlex-755:~/Downloads$ sudo su
[sudo] password for tom:           [COLOR=#ff0000]---- Up to here I was following the directions from the link you gave me[/COLOR]
root@tom-OptiPlex-755:/home/tom/Downloads# dir     [COLOR=#ff0000]--- Then I did the dir you said to do in the last post         [/COLOR]
022012changeformdowngrade.pdf     [COLOR=#ff0000]--- From here on is the result of the dir command[/COLOR]
1\ -\ 3\ -\ Karatsuba\ Multiplication\ (13\ min).srt
1\ -\ 3\ -\ Karatsuba\ Multiplication\ (13\ min).txt
1\ -\ 7\ -\ Merge\ Sort-\ Analysis\ (9\ min).txt
1-s2.0-S1053811912004703-main.pdf
20071220.pdf
2008-Nissan-350Z.pdf
2009\ Honda\ Odyssey\ White.jpg
20101002-Leigh_Brasington-GAIA-the_four_noble_truths_and_the_eight_fold_path.mp3
2012_6_21_immunizationFormandInformation.pdf
2012-map.pdf
201308_frp.pdf
2014\ -\ Carr\ -\ Pool\ Renovation\ Proposal.docx
2015\ Ally\ Bank\ Form\ 1099-INT.pdf
2016\ Americold_Newsletter\ FINAL.pdf
2\ -\ 1\ -\ 1.1.\ Scientific\ World\ View\ (00-08-02).srt
433741Last\ Will\ and\ Testament.pdf
6\ -\ 5\ -\ Office\ Hours\ for\ Lecture\ Six\ (34-28).mp4
6\ -\ 6\ -\ Office\ Hours\ for\ Week\ Seven\ (42-49).mp4
6\ -\ 7\ -\ Office\ Hours\ for\ Week\ Eight.mp4
6\ -\ 8\ -\ Office\ Hours\ for\ Weeks\ Nine\ and\ Ten.mp4
707192-une-charlie-png.png
Advancement-Intern-Spring-2016.docx
AL\ 3021\ Fall\ 2013\ session\ 1\ (1).pdf
AL\ 3021\ Fall\ 2013\ session\ 1\ (2).pdf
AL\ 3021\ Fall\ 2013\ session\ 1\ (3).pdf
AL\ 3021\ Fall\ 2013\ session\ 1\ (4).pdf
AL\ 3021\ Fall\ 2013\ session\ 1\ (5).pdf
AL\ 3021\ Fall\ 2013\ session\ 1\ (6).pdf
AL\ 3021\ Fall\ 2013\ session\ 1\ (7).pdf
AL\ 3021\ Fall\ 2013\ session\ 1\ (9).pdf
AL\ 3021\ Fall\ 2013\ session\ 1.pdf
AL\ 3021\ Fall\ 2013\ session\ 2\ (1).pdf
AL\ 3021\ Fall\ 2013\ session\ 2.pdf
AL\ 3021\ Fall\ 2013\ session\ 3\ (1).pdf
AL\ 3021\ Fall\ 2013\ session\ 4\ (1).pdf
AL\ 3021\ Fall\ 2013\ session\ 4\ (2).pdf
AL\ 3021\ Fall\ 2013\ session\ 4\ (3).pdf
AL\ 3021\ Fall\ 2013\ session\ 4\ (4).pdf
AL\ 3021\ Fall\ 2013\ session\ 4.pdf
AL\ 3021\ Fall\ 2013\ session\ 5\ (1).pdf
AL\ 3021\ Fall\ 2013\ session\ 5.pdf
AL\ 3021\ Fall\ 2013\ session\ 6\ (1).pdf
AL\ 3021\ Fall\ 2013\ session\ 6.pdf
AL\ 3021\ Fall\ 2013\ session\ 7.pdf
AL\ 3021\ Fall\ 2013\ syllabus.pdf
AL\ 8970\ Fall\ 2013\ session\ 9\ (1).pdf
ALAMEDA\ MORTGAGE\ AGREEMENT\ (1).doc
ALAMEDA\ MORTGAGE\ AGREEMENT\ (2).doc
ALAMEDA\ MORTGAGE\ AGREEMENT.doc
algo-merge3_typed.pdf
All\ InclusiveFee-Schedule.pdf
Assignment_Alameda_Louisiana.pdf
attachment
attachment\ (1)
attachment\ (2)
Attachments_2014114.zip
BBQ\ Flyer\ 2013.pdf
Bogleheads_&#8226;_View_topic_-_Defined_Maturity_ET\ Fs_vs._Traditional_Bond_Funds.pdf
bookmarks-2011-11-27\ 2.json
bookmarks\ Chrome\ _11_27_11.html
bookmarks\ firefox\ 11\ 27\ 2011.html
brgenml1cupswrapper-3.1.0-1.i386.deb
brgenml1lpr-3.1.0-1.i386.deb
BuddhistRomanticism151209.epub
Carr\ 2.22\ new\ listing\ aggrmt.pdf
Commitment\ Letter\ 1\ (1).pdf
Commitment\ Letter\ 1.pdf
complete-abandon-investigated\ (1).pdf
complete-abandon-investigated.pdf
Computer\ Literacy.pdf
confirmation\ (1).pdf
confirmation\ (2).pdf
confirmation\ (3).pdf
confirmation\ (4).pdf
confirmation\ (5).pdf
confirmation\ letter.pdf
confirmation.pdf
Constructive-Living.pdf
contract\ Afra\ Construction.pdf
Corrective\ Warranty\ Deed\ -\ Clay\ County\ (00091703).DOC
correspondence-1.pdf
correspondence-2.pdf
Co-Trustees\ Affidavit\ -\ Dorothea\ Carr\ Trust\ (00091704)\ (1).DOC
Co-Trustees\ Affidavit\ -\ Dorothea\ Carr\ Trust\ (00091704)\ (2).DOC
Co-Trustees\ Affidavit\ -\ Dorothea\ Carr\ Trust\ (00091704)\ (3).DOC
Co-Trustees\ Affidavit\ -\ Dorothea\ Carr\ Trust\ (00091704).DOC
Co-Trustees\ Affidavit\ -\ Thomas\ Carr\ Trust\ (00089918)\ (1).DOC
Co-Trustees\ Affidavit\ -\ Thomas\ Carr\ Trust\ (00089918).DOC
David\ Francis\ meta-analysis.pdf
desktop4shared-1.3_1-all.deb
document\ (1).pdf
document.pdf
durant\ family\ tree.zip
DURANT.zip
ecsBillDisplay\ (1).pdf
ecsBillDisplay\ (2).pdf
english-to-chin-hakha-dictionary-03.05.2013\ (1).pdf
english-to-chin-hakha-dictionary-03.05.2013.pdf
esl\ test.html
ET_Guide_2014_Lo-Res.pdf
Fall2013ContEdSchedule\ (1).pdf
Fall_2013_Printable_Semester_Calendar.pdf
Fall\ schedule_English\ 1.pdf
Fate0494.doc
FFSR\ roster\ -\ map15.pdf
Fido\ wire\ request\ (1).pdf
Fido\ wire\ request.pdf
flyer\ 2013.doc
Form1095a.pdf
Foy-Driscoll\ Petition\ for\ Certiorari\ to\ Supreme\ Court\ Draft\ 3.wpd
GEISLMS_20160129.pdf
Getting\ Started\ with\ GAMBAS.odt
gmail\ contacts.vcf
google-chrome-stable_current_i386.deb
health-plan-information-download.ods
health-plan-information-download.xlsx
History_for_Account_X73887907\ (1).csv
History_for_Account_X73887907\ (2).csv
History_for_Account_X73887907.csv
hll2320dcupswrapper-3.2.0-1.i386.deb
Homework\ assignment\ 1\ AL\ 3021\ Fall\ 2013\ (1).docx
Homework\ assignment\ 1\ AL\ 3021\ Fall\ 2013\ ANSWER\ KEY.docx
Homework\ assignment\ 1\ AL\ 3021\ Fall\ 2013.docx
Homework\ assignment\ 2\ AL\ 3021\ Fall\ 2013\ ANSWER\ KEY.docx
Homework\ assignment\ 3\ AL\ 3021\ Fall\ 2013\ ANSWER\ KEY.docx
Homework\ assignment\ 3\ AL\ 3021\ Fall\ 2013.docx
HowToMeditateForPDF.pdf
image1.jpeg
IMG_1038.jpeg
IMG_3161.jpeg
Information_Complexity\ ebook_Mitchel.pdf
jdk1.7.0_75
jdk-7u75-linux-i586.tar.gz
kubuntu-14.04.1-desktop-amd64.iso
lake01.jpg
Last\ Will\ and\ Testament\ and\ Testament\ of\ Tom.docx
Last-Will-and-Testament.docx
Learning-Resources-2.ppsx
linux-brprinter-installer-2.0.0-1
linux-brprinter-installer-2.0\ (1).0-1
linux-brprinter-installer-2.0\ (2).0-1
linuxmint-13-cinnamon-dvd-32bit.iso
linuxmint-17-cinnamon-32bit-v2.iso
linuxmint-17-cinnamon-64bit-v2.iso
MarketplaceApp_Checklist_Generic.pdf
me-with-elephant02.bmp
me-with-elephant.bmp
mtn01.jpg
MVP\ Mentor-Mentee\ Agreement\ FY\ 2015.docx
NEW_VOLUNTEER_APPLICATION.doc
Ni\ Cung\ (1).pdf
NM-Release_Thomas\ (1).doc
NM-Release_Thomas.doc
Note\ and\ Mtg\ -\ ROCKY.pdf
OshoShambhala\ (1).docx
OshoShambhala.docx
Payment\ Signature\ Doc.pdf
PDFRequestRouter\ (1).pdf
PDFRequestRouter\ (2).pdf
PDFRequestRouter\ (3).pdf
PDFRequestRouter\ (4).pdf
PDFRequestRouter.pdf
pesticide_list_final_59620.pdf
Pre-qualification\ Worksheet\ (1).pdf
Pre-qualification\ Worksheet.pdf
Prime01.html
processing-2.2.1-linux64.tgz
Psorisis_IMG_0895.JPG
pw_e206472.pdf
pycharm-community-4.0.6.tar.gz
refreshing\ word\ classes\ (1).pdf
refreshing\ word\ classes.pdf
Release\ of\ \ Mortgage\ Alameda\ (1).pdf
Release\ of\ \ Mortgage\ Alameda.pdf
Release\ ROCKY\ (1).pdf
Release\ ROCKY.pdf
Rockwell_Sevano_Note.doc
Rockwell_Sevano_REM\ (1).doc
Rockwell_Sevano_REM.doc
SafetyNet2013\ (1).pdf
SafetyNet2013.pdf
sca_disc.pdf
Scan0348.pdf
Scanned\ from\ a\ Xerox\ multifunction\ device\ (22)\ (1).pdf
Scanned\ from\ a\ Xerox\ multifunction\ device\ (22).pdf
Scanned\ Signed\ contract\ Alameda\ deal.pdf
Security\ Escrow\ direct\ deposit\ form.pdf
Self_Directed_IRA_Fee_Schedule\ 2015.pdf
Sexual-Harassment-and-Title-IX-Fall-13-Newsletter.pdf
SR\ Comps\ -\ seller\ report.xlsx
statement\ (1).pdf
Statement_201501.pdf
statement\ (2).pdf
statement\ (3).pdf
statement\ (4).pdf
statement\ (5).pdf
statement\ (6).pdf
Statement_Apr\ 2014\ (1).pdf
Statement_Apr\ 2014\ (2).pdf
Statement_Apr\ 2014.pdf
Statement_Dec\ 2013.pdf
Statement_Dec\ 2014.pdf
Statement_Dec\ 2015.pdf
Statement_Feb\ 2014\ (1).pdf
Statement_Feb\ 2014.pdf
Statement_Jan\ 2014.pdf
Statement_Jul\ 2015.pdf
Statement_Jun\ 2013.pdf
Statement_Jun\ 2014.pdf
Statement_Mar\ 2014\ (1).pdf
Statement_Mar\ 2014\ (2).pdf
Statement_Mar\ 2014.pdf
Statement_May\ 2013.pdf
Statement_May\ 2014.pdf
Statement_Nov\ 2013.pdf
Statement_Oct\ 2013.pdf
statement.pdf
StatementPdf\ (1).pdf
StatementPdf.pdf
Statement_Sep\ 2013.pdf
state-of-states.ppt
Steve.jpg
swim\ skills.pdf
Thang\ Peng\ documents-1.jpg
the-four-agreements\ (1).pdf
the-four-agreements.pdf
The\ Shelter\ Six\ -\ 9-3-13\ (1).pdf
The\ Shelter\ Six\ -\ 9-3-13.pdf
To\ Do\ November\ 11,\ 2014.pdf
To\ Do\ November\ 11,\ 2014.wpd
Tom\ 1.jpg
Tree\ Planting\ Instructions.docx
TRIC_interview_uncut.doc
TSC\ AND\ RRC\ 2013-14\ BUSINESS\ AND\ TAX\ NOTES.doc
ubuntu-12.04-desktop-i386.iso
Unconfirmed\ 302442.crdownload
Unnamed\ page.html
Vedanta\ for\ Agnostics.pdf
VENOMOUSSNAKESOFGEORGIA.pdf
voice-message.wav
Warranty\ Deed\ -\ Clay\ County\ (00091584).DOC
wbfex.pdf
WhenIsItAppropriatetoReferanELL.ppt
Wire\ -\ complete\ Scanned\ Document.pdf
Wire\ Inst-Domestic\ Incoming.pdf
wire\ instructions\ (1).pdf
wire\ instructions\ (2).pdf
wire\ instructions.pdf
Wright-Chapter13.pdf
xenial-desktop-i386.iso
yahoo_ab.csv
zmtf.pdf
root@tom-OptiPlex-755:/home/tom/Downloads# ^C
root@tom-OptiPlex-755:/home/tom/Downloads#
```

---

### Post by Bucky Ball on 2016-02-20
I have no idea what command you've given there but it is definitely not right from your output. Would be better to include the exact terminal output and provide exactly what you type in rather than describe what you did. Use separate [code] boxes if you need to.

Please start using code tags for your terminal output. Neater, cleaner, keeps formatting and saves space. ;)

See link in my signature for how. I've added to your last post.

---

### Post by leunam12 on 2016-02-20
Ok, this is what you have to do:

Extract the file that you downloaded:
```
gunzip linux-brprinter-installer-2.0.0-1.gz
```
Make executable
```
chmod +x linux-brprinter-installer-2.0.0-1
```
Execute
```
sudo ./linux-brprinter-installer-2.0.0-1
```
Enter your password
Enter model name: 
```
HL-L2320D
```

---

### Post by kurt18947 on 2016-02-20
> **Bucky Ball said:**
> **I have no idea what command you've given there but it is definitely not right from your output.** 
snip


A HUGE +1 to that. I could post the latest Brother Installer script here in gz form if that would help. It's 2525 lines and starts like this:[INDENT]
```
#! /bin/bash
#
# Copyright(c) 2011-2013 Brother Industries, Ltd.  
#    All Rights Reserved.
#
#Brother retains any and all copyrights to the Software. 
#In no case this Agreement shall be construed to assign 
#or otherwise transfer from Brother to User any copyrights 
#or other intellectual property rights to whole or any part 
#of the Software.
#
#Brother grants User a non-exclusive license: to reproduce 
#and/or distribute (via Internet or in any other manner) the 
#Software. Further, Brother grants User a non-exclusive 
#license to modify, alter, translate or otherwise prepare 
#derivative works of the Software and to reproduce and 
#distribute (via Internet or in any other manner) such 
#modification, alteration, translation or other derivative 
#works for any purpose.
```


[/INDENT]

---

### Post by Tom_Carr on 2016-02-20
I followed the directions that leunam12 posted and now it works fine.

Thank you all.  Thank you, thank you, thank you, thank you !!!!!!

I think the problem was that when people know how to do things, they assume the people they are talking to know almost as much.  

For example, when the instructions said enter -  gunzip linux-brprinter-installer-*.*.*-*.gz
I thought it meant literally to enter that string, including the *.*.*  I did not know that the *.*.* meant to put in the numbers 2.0.0.1

I knew that years ago but I have forgotten it.

I am 66 years old and I have some memory loss.  This stuff can be very frustrating for me because when I was younger I worked for years as a programmer and I could pound out code super fast and felt proud of my abilities.  Now I forget things and have to keep asking questions and looking stuff up over and over.  

I really appreciate the patience that all of you showed in coming back to this thread again and again to help.

---

### Post by Bucky Ball on 2016-02-20
That's what we do. :D

Glad it's working and just post a new thread for any other issues. Mark this one as solved (first link in my signature for how). 

Good luck.

---

