---
title: "NewB 2 stupid Cant convert Z600 DRIVER plz help"
date: 2007-06-21
forum: General Help
---

### Post by FAS786 on 2007-06-21
Hiya
I got a Z600 Driver but its made for ReHat9.0 
Im using ubuntu and i have to convert the rpm files to dubs but i cant 

i just dont get it
Does any one have or give me or tell me 
where i can get a ready made driver from 
Thank You

I been trying for a week i just dont get the instruction that follow

   1. download CJLZ600LE-CUPS-1.0-1.TAR.gz from Lexmark.com - it is the CUPS driver for RedHat 9.0 DONE
   2. Untar and unzip this file using
      $ tar -zxvf CJLZ600LE-CUPS-1.0-1.TAR.gz DONE
   3. You will end up with a file called
      z600cups-1.0-1.gz.sh DONE
   4. Extract the .rpm part of this file using
      sh z600cups-1.0-1.gz.sh -target temp_lex
      this will create a sub-directory called "temp_lex" under the current directory, and put a whole lot of files in it. Ignore any errors you might get - if the two .rpm files are in temp_lex you are fine. 
??????? I GET ERRORS SAY THE THING DONT EXIST AND THE REST IS HISTORY :(

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

---

### Post by Happy_Man on 2007-06-21
What things don't exist? Can you post those errors here?

---

