---
title: "How to install Printer"
date: 2007-06-20
forum: General Help
---

### Post by FAS786 on 2007-06-20
I got a Lexmark Z600 Driver
Which im hopein will be compatable for my Z640 Printer
But how do i install it
i extract to a new folder
i go to Add printer
i chose the folder from the list but it says
Only file PPD will be installed

very confusing need help plz:confused:(

---

### Post by sharke on 2007-06-20
This is how i did it i forget where i found theese instructions

   1. download CJLZ600LE-CUPS-1.0-1.TAR.gz from Lexmark.com - it is the CUPS driver for RedHat 9.0
   2. Untar and unzip this file using
      $ tar -zxvf CJLZ600LE-CUPS-1.0-1.TAR.gz
   3. You will end up with a file called
      z600cups-1.0-1.gz.sh
   4. Extract the .rpm part of this file using
      sh z600cups-1.0-1.gz.sh -target temp_lex this will create a sub-directory called "temp_lex" under the current directory, and put a whole lot of files in it. Ignore any errors you might get - if the two .rpm files are in temp_lex you are fine.
   5. In the newly created directory temp_lex you will find, amongst others, the files:
      z600cups-1.0-1.i386.rpm, and
      z600llpddk-2.0-1.i386.rpm
   6. To install to a debian system (or Ubuntu or Knoppix) you need to convert these two files to the .deb equivalent. The program to use is called "alien" and you run it as follows:
      $ alien z600cups-1.0-1.i386.rpm
      $ alien z600llpddk-2.0-1.i386.rpm
   7. You will now find the dpkg packages:
      z600cups-1.0-1.i386.deb
      z600llpddk-2.0-1.i386.deb
   8. Now install the driver with:
      dpkg -i z600cups-1.0-1.i386.deb
      dpkg -i z600llpddk-2.0-1.i386.deb
   9. Now use CUPS or the Printer configuration tool in Ubuntu to add the printer
Regards
Sharke

---

### Post by samuraiCat on 2007-06-21
> **sharke said:**
> This is how i did it i forget where i found theese instructions

   1. download CJLZ600LE-CUPS-1.0-1.TAR.gz from Lexmark.com - it is the CUPS driver for RedHat 9.0
   2. Untar and unzip this file using
      $ tar -zxvf CJLZ600LE-CUPS-1.0-1.TAR.gz
   3. You will end up with a file called
      z600cups-1.0-1.gz.sh
   4. Extract the .rpm part of this file using
      sh z600cups-1.0-1.gz.sh -target temp_lex this will create a sub-directory called "temp_lex" under the current directory, and put a whole lot of files in it. Ignore any errors you might get - if the two .rpm files are in temp_lex you are fine.
   5. In the newly created directory temp_lex you will find, amongst others, the files:
      z600cups-1.0-1.i386.rpm, and
      z600llpddk-2.0-1.i386.rpm
   6. To install to a debian system (or Ubuntu or Knoppix) you need to convert these two files to the .deb equivalent. The program to use is called "alien" and you run it as follows:
      $ alien z600cups-1.0-1.i386.rpm
      $ alien z600llpddk-2.0-1.i386.rpm
   7. You will now find the dpkg packages:
      z600cups-1.0-1.i386.deb
      z600llpddk-2.0-1.i386.deb
   8. Now install the driver with:
      dpkg -i z600cups-1.0-1.i386.deb
      dpkg -i z600llpddk-2.0-1.i386.deb
   9. Now use CUPS or the Printer configuration tool in Ubuntu to add the printer
Regards
Sharke

Wow! Would that work with a Lexmark Z517? Thanks!

---

### Post by sharke on 2007-06-22
download z700 driver [http://users.cybercity.dk/~dko12479/](http://users.cybercity.dk/~dko12479/)
and follow instructions here  [http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark](http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark)
Regards
Sharke

---

### Post by samuraiCat on 2007-06-22
> **FAS786 said:**
> I got a Lexmark Z600 Driver
Which im hopein will be compatable for my Z640 Printer
But how do i install it
i extract to a new folder
i go to Add printer
i chose the folder from the list but it says
Only file PPD will be installed

very confusing need help plz:confused:(


I have a Lexmark Z517, which was deemed a paperweight. I had tried all the instructions posted here, and nothing had worked.

Then I found this page: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters)

I followed it to the letter, and despite the fact that my printer is neither a multifunction printer nor listed as being supported in the instructions, it worked like a charm.

So, sudo newbie-gotopage read fixproblem

---

