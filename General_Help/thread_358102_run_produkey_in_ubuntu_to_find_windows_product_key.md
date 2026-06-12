---
title: "run produkey in ubuntu to find windows product key...? readme included"
date: 2007-02-10
forum: General Help
---

### Post by Fittersman on 2007-02-10
i was reading the readme for produkey and it has something in there that you can run it on a different operating system to find the product key of windows xp.... has anyone ever done this before? here is the readme, cuz i dont understand how to do it.

Basically why i want to do this on ubuntu instead of just doing it on windows is that my windows is so bogged down it takes about ten minutes to log in, another ten to open a .exe file, and i dont know how long this is going to take to come up with the product key, so i figure it would be alot easier to just do it on ubuntu if i can. 

manufacturers need to tell you the product key when they preinstall windows if you ask me...

```






ProduKey v1.06

Copyright (c) 2005 - 2006 Nir Sofer

Web Site: http://www.nirsoft.net







Description

===========



ProduKey is a small utility that displays the ProductID and the CD-Key of

MS-Office, Windows, Exchange Server, and SQL Server installed on your

computer. You can view this information for your current running

operating system, or for another operating system/computer - by using

command-line options. This utility can be useful if you lost the product

key of your Windows/Office, and you want to reinstall it on your computer.







Versions History

================





* Version 1.06 - Added support for SQL Server 2005.

* Version 1.05

  o Display information in the status bar while scanning computers

    with /remoteall and /remotefile options

  o New option /remotealldomain - scan all computers in the specified

    domain.

  o Changes in the way that /remoteall scan all computers.



* Version 1.04 - Added product key of Exchange Server.

* Version 1.03 - new command-line option: /remoteall

* Version 1.02 - On newer versions of Office (XP/2003) - display the

  real product name, if it's written in the Registry.

* Version 1.01 - Added support for XP visual style.

* Version 1.00 - First release.







Known Problems

==============





* If you bought your computer with installed operating system, you may

  find the product key appeared in ProduKey utility is different from the

  product key on your Windows CD. This problem is mostly reported with

  Dell computers.

* From unknown reason, the product key of Visual Stuido .NET is written

  in the Registry as Office XP product...

* In old versions of Office (Office 2000 and below), the 'Product Key'

  value is not available.







Using ProduKey

==============



ProduKey doesn't requite any installation process or additional DLLs. In

order to start using it, just run the executable file - produkey.exe

The main window of ProduKey displays the list of Windows, Office, and SQL

Server products installed on your system. For each product, the "Product

ID" and "Product Key" are displayed. If you want the view the product key

information in another computer, or in another operating system within

the same computer, use the command-line options below.







Command-Line Options

====================







/remoteall

Enumerate all computers on your local network, and load the product key

information from them. Be aware that this option is quite slow, and you

may need to wait a few minutes until the product key information is

displayed. In order to use this option, you must have Administrator

privileges in all computers on your local network.



/remotealldomain [Domain Name]

Enumerate all computers in the specified domain, and load the product key

information from them.



/remote [Computer Name]

Load product key information from the specified computer name. In order

to use this option, you must log in to the remote computer with

Administrator privileges.



/remotefile [Computer Names Filename]

Load product key information from all computer names specified in the

file. The file can be tab-delimited, comma-delimited, or CRLF-delimited.

In order to use this option, you must have Administrator privileges in

all computers specified in the computer names file.



/windir [Windows Directory]

Load product key information from another operating system on the same

computer. The [Windows Directory] specifies the base folder of Windows

installation, for example: c:\windows, c:\winnt



This feature is only supported on Windows 2000/XP.



/regfile [Software Registry File]

Load product key information from another operating system on the same

computer. The [Software Registry File] specifies the software registry

file usually located under c:\windows\system32\config



This feature is only supported on Windows 2000/XP.



/nosavereg

Load ProduKey without saving your last settings (window location, columns

size, and so on) to the Registry.



You can also combine the above command-line options with the following

save options in order to save product key information to file:



/stext <Filename>

Save the list of product keys into a regular text file.



/stab <Filename>

Save the list of product keys into a tab-delimited text file.



/stabular <Filename>

Save the list of product keys into a tabular text file.



/shtml <Filename>

Save the list of product keys into HTML file.



/sverhtml <Filename>

Save the list of product keys into vertical HTML file.



/sxml <Filename>

Save the list of product keys into XML file.



Examples:

produkey.exe /remote \\Server01

produkey.exe /remotefile "c:\temp\computers.txt"

produkey.exe /regfile "F:\WINNT\system32\config\software"

produkey.exe /windir "c:\winnt" /shtml "c:\temp\pk.html"

produkey.exe /remoteall

produkey.exe /remotealldomain MyDomain







System Requirements

===================



ProduKey works on all 32-bit versions of Windows. However, some features,

like viewing the product keys of another operating system instance, are

only supported on Windows 2000/XP



License

=======



This utility is released as freeware. You are allowed to freely

distribute this utility via floppy disk, CD-ROM, Internet, or in any

other way, as long as you don't charge anything for this. If you

distribute this utility, you must include all files in the distribution

package, without any modification !







Disclaimer

==========



The software is provided "AS IS" without any warranty, either expressed

or implied, including, but not limited to, the implied warranties of

merchantability and fitness for a particular purpose. The author will not

be liable for any special, incidental, consequential or indirect damages

due to loss of data or any other reason.







Translating ProduKey to the languages

=====================================



In order to translate ProduKey to other language, follow the instructions

below:

1. Run ProduKey with /savelangfile parameter:

   ProduKey.exe /savelangfile

   A file named ProduKey_lng.ini will be created in the folder of

   ProduKey utility.

2. Open the created language file in Notepad or in any other text

   editor.

3. Translate all string entries to the desired language. Optionally,

   you can also add your name and/or a link to your Web site.

   (TranslatorName and TranslatorURL values) If you add this information,

   it'll be used in the 'About' window.

4. After you finish the translation, Run ProduKey, and all translated

   strings will be loaded from the language file.

   If you want to run ProduKey without the translation, simply rename the

   language file, or move it to another folder.







Feedback

========



If you have any problem, suggestion, comment, or you found a bug in my

utility, you can send a message to nirsofer@yahoo.com


```

---

### Post by dagnabit dang doohickey on 2007-02-10
Assuming you're looking for the product key of a pre-installed version of Windows, there should be a sticker somewhere on your case that has that number on it.

As far as that produkey goes, it's windows software. A popular app for finding the key is [MagicalJellyBean's Keyfinder]("http://www.magicaljellybean.com/"), but this is also Windows software. The good news: there is a boot cd that you can use that has Keyfinder already on it.
[http://www.ubcd4win.com]("http://www.ubcd4win.com/")

---

### Post by Fittersman on 2007-02-10
so that boot cd just boots up before an OS does and tells you the info you need and gives a diagnosis of windows?

---

### Post by dagnabit dang doohickey on 2007-02-10
It boots, and is used, like a LiveCD. I've never used this CD (I've used the Linux version - Ultimate Boot CD), but if you take a look at the screenshots, it seems a Windows user should feel right at home.

Edit: Describing Ultimate Boot CD as "Linux version" is incorrect. It's not OS based.

---

### Post by Fittersman on 2007-02-10
you dont need to run this from windows do you? something just feels wrong when im doing this on ubuntu...

first i downloaded a .exe file, i used it and it told me i couldnt use it where it was located... where do i need to put it? it is currently in Z:\home\cleippi\Boot CD (cleippi is my account and Boot CD is a folder i made to put it in), it isnt in My Documents or on my Desktop, and if i put it in C:\UBCD4Win (as recommended in the warning below) i cant access it without using windows, when do i start putting it on the CD?

here is the warning message it gave:




WARNING!!!

UBCD4Win can not be run from Z:\home\cleippi\Boot CD
(or any other folder with spaces in the path)

This includes My Documents and your Desktop


Moving this directory to a path without spaces will NOT work, you have to
extract again to a place like C:\UBCD4Win

---

### Post by dagnabit dang doohickey on 2007-02-10
My bad, I had no idea that this boot CD requires some serious hoop jumping to create. Creating it seems to require a healthy Windows system, which for someone who needs a boot CD, seems to be a lot to ask for.
There is another boot CD out there that I've refrained from naming, but this blog will fill you in: [http://maxt.dk]("http://maxt.dk/archives/2006/08/01/hirens-bootcd-83/")
This CD also contains a key finder. It's called WinKeyFinder. I have never used it, so I can't say much about it. BTW, I downloaded the zip to make sure it contains a burnable iso, and it does.

---

### Post by Fittersman on 2007-02-11
alright, ill give that one a shot.

---

### Post by Fittersman on 2007-02-12
i cant find that program in there, is that what its real name is? i dont think its listed in the readme either... (i have v8.3)

---

