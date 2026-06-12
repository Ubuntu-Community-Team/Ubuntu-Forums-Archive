---
title: "printer doesnt work"
date: 2016-05-20
forum: General Help
---

### Post by tyler102 on 2016-05-20
ive never been able to print with ubuntu wether it was 12.04 14.04 or now 16.04lts
what am i doing wrong?
it finds or sees the printer and seems to have the right model number and downloads the proper drivers but a print test page doesnt work nor any other attempt at printing?

---

### Post by Bucky Ball on 2016-05-20
Welcome. More info, please. 

Make and model of the machine; how you loaded the driver, if you did; anything you've tried to get it working; and how you are trying to connect with the printer. Thanks. ;)

---

### Post by tyler102 on 2016-05-20
i clicked add printer after hooking up the usb cable.
i even see a light flicker when i click a new print job, it just never prints
Brother MFC 7360N

i checked my software and cups is already installed i think as it has a remove vs install icon beside it?

---

### Post by yancek on 2016-05-20
After you attach the cables to the printer and your computer and turn the printer on then go to the Printer Configuration and select "Add Printer", what exactly happens?  There should be some kind of message indicating the reason for failure.  Posting that would help.  If you don't get any message, what exactly does happen?

---

### Post by tyler102 on 2016-05-20
after i hooked up the printer and clicked add printer it recognized the name and brand  model etc so i clciked it and it downloaded the supposed correct drivers for this model and installed them.
now when i click a document to print , it says 8th in cue to print but nothing ever happens, no clicking, or waking of the printer  and yes it is on. nothing gets printed  not even a test page

---

### Post by SuperFreak on 2016-05-20
Suggest you remove printer from Printers and then use Brother tool to install [http://support.brother.com/g/b/downloadtop.aspx?c=us_ot&lang=en&prod=mfc7360n_all]("http://support.brother.com/g/b/downloadtop.aspx?c=us_ot&lang=en&prod=mfc7360n_all")

---

### Post by tyler102 on 2016-05-20
GA-990XA-UD3:~$ unzip linux-brprinter-installer-2.0.0-1.gz
unzip:  cannot find or open linux-brprinter-installer-2.0.0-1.gz, linux-brprinter-installer-2.0.0-1.gz.zip or linux-brprinter-installer-2.0.0-1.gz.ZIP.

ok deleted my printer,  downloaded that tool but it didnt work in terminal

did i type it wrong?

tried again after opening root command sudo su but got same error

---

### Post by pqwoerituytrueiwoq on 2016-05-20
you need to cd into the current directory
i would suggest using hte gui to extract the archive and cd into hte folder the new folder and continue form there
you probally put it in your Downloads folder to cd there type [FONT=Courier New]cd Downloads[/FONT]
you  could just hit the tab key to auto complete it once you type the w

---

### Post by Bucky Ball on 2016-05-21
> **pqwoerituytrueiwoq said:**
> you need to cd into the current directory
i would suggest using hte gui to extract the archive and cd into hte folder the new folder and continue form there

Yes, CD into the directory. You don't need to do the other bit. Once you are in the correct folder the instructions you are using from the Brother website instructions will work fine ('unzip linux-brprinter-installer-2.0.0-1.gz' will do the job once you are in the correct folder). 

Just remember to read them carefully. ;)

---

### Post by tyler102 on 2016-05-21
Ok im still a newbie at linux

you guys are going to have to dumb it down a little, maybe a lot.
what is cd in directory mean?
ive opened and extracted the file in my downloads and right clicked it to open it with ktelnet services? it looked like a terminal window...?

also i opened a terminal and typed cd download but it said command not found
or am i sposed to manually open the downloaded zip file then open a terminal and type what exactly

---

### Post by SuperFreak on 2016-05-21
I think the command is ```
cd Downloads
```
In my install "Downloads" is capitalized but may not be in yours check the appropriate folder directory and see

---

### Post by tyler102 on 2016-05-22
ok got into cd Downloads
in a terminal window but still no go
heres the error

GA-990XA-UD3:~/Downloads$ unzip linux-brprinter-installer-2.0.0-1
Archive:  linux-brprinter-installer-2.0.0-1
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of linux-brprinter-installer-2.0.0-1 or
        linux-brprinter-installer-2.0.0-1.zip, and cannot find linux-brprinter-installer-2.0.0-1.ZIP, period.
neo@neo-GA-990XA-UD3:~/Downloads$ linux-brprinter-installer-2.0.0-1.ZIP
linux-brprinter-installer-2.0.0-1.ZIP: command not found

---

### Post by SuperFreak on 2016-05-22
Did you us the  Driver Install Tool? You need to choose the deb file not the rpm file

You need to follow the instructions given at the Brother web site and alsomake sure that the prerequisite conditions are met

---

### Post by tyler102 on 2016-05-22
YES I DOWNLOADED THE DEBIAN FILE

Step1. Download the tool.(linux-brprinter-installer-*.*.*-*.gz)                                CHECK

   The tool will be downloaded into the default "Download" directory.
 (The directory location varies depending on your Linux distribution.)
 e.g. /home/(LoginName)/Download
   Step2. Open a terminal window and go to the directory you downloaded the file to in the last step.  CHECK

   Step3. Enter this command to extract the downloaded file:

   **Command: gunzip linux-brprinter-installer-*.*.*-*.gz                                                     FAIL**

   Step4. Get superuser authorization with the "**su**" command or "**sudo su**" command.                     CHECK

   Step5. Run the tool:
   **Command: bash linux-brprinter-installer-*.*.*-* Brother machine name **

   Step6. The driver installation will start. Follow the installation screen directions.
  

    When you see the message "Will you specify the DeviceURI ?",
    For USB Users: Choose N(No)



HERES TYPICALLY WHAT HAPPENS IN THE TERMINAL WINDOW

root@neo-GA-990XA-UD3:/home/neo/Downloads# linux-brprinter-installer-2.0.0-1 Brother 7360N
linux-brprinter-installer-2.0.0-1: command not found
root@neo-GA-990XA-UD3:/home/neo/Downloads# unzip linux-brprinter-installer-2.0.0-1 Brother 7360N
Archive:  linux-brprinter-installer-2.0.0-1
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of linux-brprinter-installer-2.0.0-1 or
        linux-brprinter-installer-2.0.0-1.zip, and cannot find linux-brprinter-installer-2.0.0-1.ZIP, period.
root@neo-GA-990XA-UD3:/home/neo/Downloads# 
root@neo-GA-990XA-UD3:/home/neo/Downloads# gunzip linux-brprinter-installer-2.0.0-1.gz
gzip: linux-brprinter-installer-2.0.0-1 already exists; do you wish to overwrite (y or n)? y
root@neo-GA-990XA-UD3:/home/neo/Downloads# linux-brprinter-installer-2.0.0-1.gz Brother 7360N
linux-brprinter-installer-2.0.0-1.gz: command not found
root@neo-GA-990XA-UD3:/home/neo/Downloads# 

  For Network Users: Choose Y(Yes) and DeviceURI.

   The install process may take some time. Please wait until it is complete.

---

### Post by SuperFreak on 2016-05-22
The command```
Command: gunzip linux-brprinter-installer-*.*.*-*.gz
```

Should probably be ```
gunzip linux-brprinter-installer-2.0.0-1.gz
```

Just a guess it has been awhile since I used the install tool

---

### Post by tyler102 on 2016-05-22
BEEN THERE DONE THAT

neo@neo-GA-990XA-UD3:~$ cd Downloads
neo@neo-GA-990XA-UD3:~/Downloads$ gunzip linux-brprinter-installer-2.0.0-1.gz
gzip: linux-brprinter-installer-2.0.0-1.gz: No such file or directory
neo@neo-GA-990XA-UD3:~/Downloads$

---

### Post by SuperFreak on 2016-05-22
And linux-brprinter-installer-2.0.0-1.gz is definitely in your Downloads Directory/ Just a long shot here , but for some reason my Downloads is nested in another Downloads folder like /home/david/Downloads/Downloads
If that were the case for you you would need to use the command
```
cd Downloads/Downloads
```

Thius is unlikely to be that case, but it does seem that the command to gunzip is not finding the .gz file

---

### Post by Bucky Ball on 2016-05-22
Looks like you have unzipped it and are repeatedly trying to unzip it. You need this:

> cd Downloads
bash linux-brprinter-installer-2.0.0-1 7360N 

That should be it. Doesn't look to me, though, as if the model number you have given is correct. Should be longer than that. For instance, mine is an HL-2270DW. I doubt they have a model that is simply '7360N'. There would be a pre-fix in front.

And no, not:
> bash linux-brprinter-installer-2.0.0-1 **Brother** 7360N

The 'Brother' is not required so leave it out. The pre-fix of the model number is, though. If this doesn't work, try a 'sudo' at the beginning of the command (although shouldn't need one).

> sudo bash linux-brprinter-installer-2.0.0-1 7360N

---

### Post by tyler102 on 2016-05-22
OK NOW WE ARE GETTING SOMEWHERE
IT SEEMS TO HAVE INSTALLED AND EVEN 
  PRINTED A TEST PAGE

YAY
THANKS SO MUCH

I THINK IT WAS BOTH THE NOT HAVING BASH UPFRONT IN COMMAND LINE AND  NOT HAVING CORRECTMODEL' MFC' IN FRONT OF THE 7360N



neo@neo-GA-990XA-UD3:~$ cd Downloads
neo@neo-GA-990XA-UD3:~/Downloads$ sudo bash linux-brprinter-installer-2.0.0-1 7360N 
[sudo] password for neo: 
Driver-packages cannot be found.
 Confirm the model name.

neo@neo-GA-990XA-UD3:~/Downloads$ sudo bash linux-brprinter-installer-2.0.0-1
Input model name ->m7360n

Driver-packages cannot be found.
 Confirm the model name.

neo@neo-GA-990XA-UD3:~/Downloads$ sudo bash linux-brprinter-installer-2.0.0-1
Input model name ->MFC-7360N

You are going to install following packages.
   mfc7360nlpr-2.1.0-1.i386.deb
   cupswrapperMFC7360N-2.0.4-2.i386.deb
   brscan4-0.4.3-3.amd64.deb
   brscan-skey-0.2.4-1.amd64.deb
OK? [y/N] ->y


=========================================
Brother License Agreement

Brother retains any and all copyrights to the Software. In no case this Agreement shall be construed to assign or otherwise transfer from Brother to User any copyrights or other intellectual property rights to whole or any part of the Software.

Brother grants User a non-exclusive license: to reproduce and/or distribute (via Internet or in any other manner) the Software. Further, Brother grants User a non-exclusive license to modify, alter, translate or otherwise prepare derivative works of the Software and to reproduce and distribute (via Internet or in any other manner) such modification, alteration, translation or other derivative works for any purpose.

The license of the Software from Brother hereunder is granted "AS IS." BROTHER HEREBY DISCLAIMS ANY WARRANTIES WITH RESPECT TO THE SOFTWARE, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO WARRANTY FOR THE QUALITY, MERCHANTABILITY, FITNESS FOR PARTICULAR PURPOSE OR NON-INFRINGEMENT.
Brother shall have no liability in contract, tort (including negligence or breach of statutory duty) or otherwise for any interruption of use, loss of data, or for any indirect, incidental, punitive or consequential loss or damage, or for any loss of profit, revenue, data, goodwill or anticipated savings that arises under, out of, or in contemplation of this Agreement or otherwise arises due to any error, inaccuracy or defect in the Software even if Brother has been advised of the possibility of such loss or damage.
Further, Brother shall have no liability to disclose and/or distribute the source cord of the Software to User under any circumstances. In no case shall the above license by Brother to modify, alter, translate or otherwise prepare derivative works of the Software be construed as Brother's implied agreement or undertakings to disclose and/or distribute the source cord of the Software.
=========================================
Do you agree? [Y/n] ->y

wget -T 10 -nd --no-cache [http://www.brother.com/pub/bsc/linux/packages/mfc7360nlpr-2.1.0-1.i386.deb](http://www.brother.com/pub/bsc/linux/packages/mfc7360nlpr-2.1.0-1.i386.deb)
--2016-05-22 10:31:28--  [http://www.brother.com/pub/bsc/linux/packages/mfc7360nlpr-2.1.0-1.i386.deb](http://www.brother.com/pub/bsc/linux/packages/mfc7360nlpr-2.1.0-1.i386.deb)
Resolving [www.brother.com](www.brother.com) ([www.brother.com](www.brother.com))... 142.165.4.51, 142.165.4.41
Connecting to [www.brother.com](www.brother.com) ([www.brother.com)|142.165.4.51|:80](www.brother.com)|142.165.4.51|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 35820 (35K) [text/plain]
Saving to: ‘mfc7360nlpr-2.1.0-1.i386.deb’

mfc7360nlpr-2.1.0-1 100%[===================>]  34.98K  --.-KB/s    in 0.03s   

2016-05-22 10:31:29 (1.09 MB/s) - ‘mfc7360nlpr-2.1.0-1.i386.deb’ saved [35820/35820]


=========================================
GPL License Agreement

This Software may be used in accordance with GNU General Public License (GPL). Please read carefully the following GPL and click on "I Accept" button. If you cannot agree with the following terms, please click "I don't Accept" button. In case of your non-acceptance, you can not use this Software.
Note:
Please click on "I Accept" while holding down "Shift" or right click on "I Accept" and select "Save Target As,,," from the menu.

GNU GENERAL PUBLIC LICENSE
Version 2, June 1991

Copyright (C) 1989, 1991 Free Software Foundation, Inc.51 Franklin St, Fifth Floor, Boston, MA 02110-1301 USA
Everyone is permitted to copy and distribute verbatim copies of this license document, but changing it is not allowed.

Preamble

The licenses for most software are designed to take away your freedom to share and change it. By contrast, the GNU General Public License is intended to guarantee your freedom to share and change free software--to make sure the software is free for all its users. This General Public License applies to most of the Free Software Foundation's software and to any other program whose authors commit to using it. (Some other Free Software Foundation software is covered by
the GNU Library General Public License instead.) You can apply it to your programs, too.

When we speak of free software, we are referring to freedom, not price. Our General Public Licenses are designed to make sure that you have the freedom to distribute copies of free software (and charge for this service if you wish), that you receive source code or can get it if you want it, that you can change the software or use pieces of it in new free programs; and that you know you can do these things.

To protect your rights, we need to make restrictions that forbid anyone to deny you these rights or to ask you to surrender the rights. These restrictions translate to certain responsibilities for you if you distribute copies of the software, or if you modify it.

For example, if you distribute copies of such a program, whether gratis or for a fee, you must give the recipients all the rights that you have. You must make sure that they, too, receive or can get the
source code. And you must show them these terms so they know their rights.

We protect your rights with two steps: (1) copyright the software, and (2) offer you this license which gives you legal permission to copy, distribute and/or modify the software.

Also, for each author's protection and ours, we want to make certain that everyone understands that there is no warranty for this free software. If the software is modified by someone else and passed on, we want its recipients to know that what they have is not the original, so that any problems introduced by others will not reflect on the original authors' reputations.

Finally, any free program is threatened constantly by software patents. We wish to avoid the danger that redistributors of a free program will individually obtain patent licenses, in effect making the program proprietary. To prevent this, we have made it clear that any patent must be licensed for everyone's free use or not licensed at all.

The precise terms and conditions for copying, distribution and modification follow.

GNU GENERAL PUBLIC LICENSE
TERMS AND CONDITIONS FOR COPYING, DISTRIBUTION AND MODIFICATION

0. This License applies to any program or other work which contains a notice placed by the copyright holder saying it may be distributed under the terms of this General Public License. The "Program", below, refers to any such program or work, and a "work based on the Program" means either the Program or any derivative work under copyright law: that is to say, a work containing the Program or a portion of it, either verbatim or with modifications and/or translated into another language. (Hereinafter, translation is included without limitation in the term "modification".) Each licensee is addressed as "you".

Activities other than copying, distribution and modification are not covered by this License; they are outside its scope. The act of running the Program is not restricted, and the output from the Program
is covered only if its contents constitute a work based on the Program (independent of having been made by running the Program). Whether that is true depends on what the Program does.

   1. You may copy and distribute verbatim copies of the Program's source code as you receive it, in any medium, provided that you conspicuously and appropriately publish on each copy an appropriate copyright notice and disclaimer of warranty; keep intact all the notices that refer to this License and to the absence of any warranty; and give any other recipients of the Program a copy of this License along with the Program.

      You may charge a fee for the physical act of transferring a copy, and you may at your option offer warranty protection in exchange for a fee.
   2. You may modify your copy or copies of the Program or any portion of it, thus forming a work based on the Program, and copy and distribute such modifications or work under the terms of Section 1 above, provided that you also meet all of these conditions:

      a) You must cause the modified files to carry prominent notices stating that you changed the files and the date of any change.

      b) You must cause any work that you distribute or publish, that in whole or in part contains or is derived from the Program or any part thereof, to be licensed as a whole at no charge to all third parties under the terms of this License.

      c) If the modified program normally reads commands interactively when run, you must cause it, when started running for such interactive use in the most ordinary way, to print or display an
      announcement including an appropriate copyright notice and a notice that there is no warranty (or else, saying that you provide a warranty) and that users may redistribute the program under these conditions, and telling the user how to view a copy of this License. (Exception: if the Program itself is interactive but does not normally print such an announcement, your work based on the Program is not required to print an announcement.)
      
      These requirements apply to the modified work as a whole. If identifiable sections of that work are not derived from the Program, and can be reasonably considered independent and separate works in themselves, then this License, and its terms, do not apply to those sections when you distribute them as separate works. But when you distribute the same sections as part of a whole which is a work based on the Program, the distribution of the whole must be on the terms of this License, whose permissions for other licensees extend to the entire whole, and thus to each and every part regardless of who wrote it.

      Thus, it is not the intent of this section to claim rights or contest your rights to work written entirely by you; rather, the intent is to exercise the right to control the distribution of derivative or collective works based on the Program.

      In addition, mere aggregation of another work not based on the Program with the Program (or with a work based on the Program) on a volume of a storage or distribution medium does not bring the other work under the scope of this License.
   3. You may copy and distribute the Program (or a work based on it, under Section 2) in object code or executable form under the terms of Sections 1 and 2 above provided that you also do one of the following:

      a) Accompany it with the complete corresponding machine-readable source code, which must be distributed under the terms of Sections 1 and 2 above on a medium customarily used for software interchange; or,

      b) Accompany it with a written offer, valid for at least three years, to give any third party, for a charge no more than your cost of physically performing source distribution, a complete machine-readable copy of the corresponding source code, to be distributed under the terms of Sections 1 and 2 above on a medium customarily used for software interchange; or,

      c) Accompany it with the information you received as to the offer to distribute corresponding source code. (This alternative is allowed only for noncommercial distribution and only if you
      received the program in object code or executable form with such an offer, in accord with Subsection b above.)

      The source code for a work means the preferred form of the work for making modifications to it. For an executable work, complete source code means all the source code for all modules it contains, plus any associated interface definition files, plus the scripts used to control compilation and installation of the executable. However, as a special exception, the source code distributed need not include anything that is normally distributed (in either source or binary form) with the major components (compiler, kernel, and so on) of the operating system on which the executable runs, unless that component itself accompanies the executable.

      If distribution of executable or object code is made by offering access to copy from a designated place, then offering equivalent access to copy the source code from the same place counts as distribution of the source code, even though third parties are not compelled to copy the source along with the object code.
   4. You may not copy, modify, sublicense, or distribute the Program except as expressly provided under this License. Any attempt otherwise to copy, modify, sublicense or distribute the Program is void, and will automatically terminate your rights under this License. However, parties who have received copies, or rights, from you under this License will not have their licenses terminated so long as such parties remain in full compliance.
   5. You are not required to accept this License, since you have not signed it. However, nothing else grants you permission to modify or distribute the Program or its derivative works. These actions are prohibited by law if you do not accept this License. Therefore, by modifying or distributing the Program (or any work based on the Program), you indicate your acceptance of this License to do so, and all its terms and conditions for copying, distributing or modifying
      the Program or works based on it.
   6. Each time you redistribute the Program (or any work based on the Program), the recipient automatically receives a license from the original licensor to copy, distribute or modify the Program subject to these terms and conditions. You may not impose any further restrictions on the recipients' exercise of the rights granted herein. You are not responsible for enforcing compliance by third parties to this License.
   7. If, as a consequence of a court judgment or allegation of patent infringement or for any other reason (not limited to patent issues), conditions are imposed on you (whether by court order, agreement or otherwise) that contradict the conditions of this License, they do not excuse you from the conditions of this License. If you cannot distribute so as to satisfy simultaneously your obligations under this License and any other pertinent obligations, then as a consequence you may not distribute the Program at all. For example, if a patent license would not permit royalty-free redistribution of the Program by all those who receive copies directly or indirectly through you, then the only way you could satisfy both it and this License would be to refrain entirely from distribution of the Program.

      If any portion of this section is held invalid or unenforceable under any particular circumstance, the balance of the section is intended to apply and the section as a whole is intended to apply in other circumstances.

      It is not the purpose of this section to induce you to infringe any patents or other property right claims or to contest validity of any such claims; this section has the sole purpose of protecting the integrity of the free software distribution system, which is implemented by public license practices. Many people have made generous contributions to the wide range of software distributed through that system in reliance on consistent application of that system; it is up to the author/donor to decide if he or she is willing to distribute software through any other system and a licensee cannot impose that choice.

      This section is intended to make thoroughly clear what is believed to be a consequence of the rest of this License.
   8. If the distribution and/or use of the Program is restricted in certain countries either by patents or by copyrighted interfaces, the original copyright holder who places the Program under this License may add an explicit geographical distribution limitation excluding those countries, so that distribution is permitted only in or among countries not thus excluded. In such case, this License incorporates the limitation as if written in the body of this License.
   9. The Free Software Foundation may publish revised and/or new versions of the General Public License from time to time. Such new versions will be similar in spirit to the present version, but may differ in detail to address new problems or concerns.

      Each version is given a distinguishing version number. If the Program specifies a version number of this License which applies to it and "any later version", you have the option of following the terms and conditions either of that version or of any later version published by the Free Software Foundation. If the Program does not specify a version number of this License, you may choose any version ever published by the Free Software Foundation.
  10. If you wish to incorporate parts of the Program into other free programs whose distribution conditions are different, write to the author to ask for permission. For software which is copyrighted by the Free Software Foundation, write to the Free Software Foundation; we sometimes make exceptions for this. Our decision will be guided by the two goals of preserving the free status of all derivatives of our free software and of promoting the sharing and reuse of software generally.

NO WARRANTY

  11. BECAUSE THE PROGRAM IS LICENSED FREE OF CHARGE, THERE IS NO WARRANTY FOR THE PROGRAM, TO THE EXTENT PERMITTED BY APPLICABLE LAW. EXCEPT WHEN OTHERWISE STATED IN WRITING THE COPYRIGHT HOLDERS AND/OR OTHER PARTIES PROVIDE THE PROGRAM "AS IS" WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. THE ENTIRE RISK AS TO THE QUALITY AND PERFORMANCE OF THE PROGRAM IS WITH YOU. SHOULD THE PROGRAM PROVE DEFECTIVE, YOU ASSUME THE COST OF ALL NECESSARY SERVICING, REPAIR OR CORRECTION.
  12. IN NO EVENT UNLESS REQUIRED BY APPLICABLE LAW OR AGREED TO IN WRITING WILL ANY COPYRIGHT HOLDER, OR ANY OTHER PARTY WHO MAY MODIFY AND/OR REDISTRIBUTE THE PROGRAM AS PERMITTED ABOVE, BE LIABLE TO YOU FOR DAMAGES, INCLUDING ANY GENERAL, SPECIAL, INCIDENTAL OR CONSEQUENTIAL DAMAGES ARISING OUT OF THE USE OR INABILITY TO USE THE PROGRAM (INCLUDING BUT NOT LIMITED TO LOSS OF DATA OR DATA BEING RENDERED INACCURATE OR LOSSES SUSTAINED BY YOU OR THIRD PARTIES OR A FAILURE OF THE PROGRAM TO OPERATE WITH ANY OTHER PROGRAMS), EVEN IF SUCH HOLDER OR OTHER PARTY HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES.

END OF TERMS AND CONDITIONS

How to Apply These Terms to Your New Programs

If you develop a new program, and you want it to be of the greatest possible use to the public, the best way to achieve this is to make it free software which everyone can redistribute and change under these terms.

To do so, attach the following notices to the program. It is safest to attach them to the start of each source file to most effectively convey the exclusion of warranty; and each file should have at least the "copyright" line and a pointer to where the full notice is found.

<one line to give the program's name and a brief idea of what it does.>
Copyright (C) <year> <name of author>

This program is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 2 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program; if not, write to the Free Software Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA 02110-1301 USA


Also add information on how to contact you by electronic and paper mail.

If the program is interactive, make it output a short notice like this when it starts in an interactive mode:

Gnomovision version 69, Copyright (C) year name of author Gnomovision
comes with ABSOLUTELY NO WARRANTY; for details type `show w'.
This is free software, and you are welcome to redistribute it
under certain conditions; type `show c' for details.

The hypothetical commands `show w' and `show c' should show the appropriate parts of the General Public License. Of course, the commands you use may be called something other than `show w' and `show c'; they could even be mouse-clicks or menu items--whatever suits your program.

You should also get your employer (if you work as a programmer) or your school, if any, to sign a "copyright disclaimer" for the program, if necessary. Here is a sample; alter the names:

Yoyodyne, Inc., hereby disclaims all copyright interest in the program
`Gnomovision' (which makes passes at compilers) written by James Hacker.

<signature of Ty Coon>, 1 April 1989
Ty Coon, President of Vice

This General Public License does not permit incorporating your program into proprietary programs. If your program is a subroutine library, you may consider it more useful to permit linking proprietary applications with the library. If this is what you want to do, use the GNU Library General Public License instead of this License.
=========================================

Do you agree? [Y/n] ->y

wget -T 10 -nd --no-cache [http://www.brother.com/pub/bsc/linux/packages/cupswrapperMFC7360N-2.0.4-2.i386.deb](http://www.brother.com/pub/bsc/linux/packages/cupswrapperMFC7360N-2.0.4-2.i386.deb)
--2016-05-22 10:31:34--  [http://www.brother.com/pub/bsc/linux/packages/cupswrapperMFC7360N-2.0.4-2.i386.deb](http://www.brother.com/pub/bsc/linux/packages/cupswrapperMFC7360N-2.0.4-2.i386.deb)
Resolving [www.brother.com](www.brother.com) ([www.brother.com](www.brother.com))... 142.165.4.41, 142.165.4.51
Connecting to [www.brother.com](www.brother.com) ([www.brother.com)|142.165.4.41|:80](www.brother.com)|142.165.4.41|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13248 (13K) [text/plain]
Saving to: ‘cupswrapperMFC7360N-2.0.4-2.i386.deb’

cupswrapperMFC7360N 100%[===================>]  12.94K  --.-KB/s    in 0.006s  

2016-05-22 10:31:34 (1.96 MB/s) - ‘cupswrapperMFC7360N-2.0.4-2.i386.deb’ saved [13248/13248]

Hit:1 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease       
Get:3 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates InRelease [94.5 kB]
Hit:4 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-backports InRelease
Get:5 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [89.5 kB]
Get:6 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [87.4 kB]
Get:7 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [30.1 kB]
Get:8 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [29.4 kB]
Fetched 331 kB in 1s (199 kB/s)                            
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  lib32ncurses5 lib32z1

E: Package 'ia32-libs' has no installation candidate
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  lib32gcc1 libc6-i386
The following NEW packages will be installed:
  lib32gcc1 lib32stdc++6 libc6-i386
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,785 kB of archives.
After this operation, 12.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial/main amd64 libc6-i386 amd64 2.23-0ubuntu3 [2,335 kB]
Get:2 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial/main amd64 lib32gcc1 amd64 1:6.0.1-0ubuntu1 [46.6 kB]
Get:3 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) xenial/main amd64 lib32stdc++6 amd64 5.3.1-14ubuntu2 [404 kB]
Fetched 2,785 kB in 5s (525 kB/s)     
Selecting previously unselected package libc6-i386.
(Reading database ... 235718 files and directories currently installed.)
Preparing to unpack .../libc6-i386_2.23-0ubuntu3_amd64.deb ...
Unpacking libc6-i386 (2.23-0ubuntu3) ...
Selecting previously unselected package lib32gcc1.
Preparing to unpack .../lib32gcc1_1%3a6.0.1-0ubuntu1_amd64.deb ...
Unpacking lib32gcc1 (1:6.0.1-0ubuntu1) ...
Selecting previously unselected package lib32stdc++6.
Preparing to unpack .../lib32stdc++6_5.3.1-14ubuntu2_amd64.deb ...
Unpacking lib32stdc++6 (5.3.1-14ubuntu2) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Setting up libc6-i386 (2.23-0ubuntu3) ...
Setting up lib32gcc1 (1:6.0.1-0ubuntu1) ...
Setting up lib32stdc++6 (5.3.1-14ubuntu2) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
dpkg -x mfc7360nlpr-2.1.0-1.i386.deb /
dpkg -x cupswrapperMFC7360N-2.0.4-2.i386.deb /
dpkg-deb: building package 'mfc7360nlpr' in 'mfc7360nlpr-2.1.0-1a.i386.deb'.
dpkg -b ./brother_driver_packdir mfc7360nlpr-2.1.0-1a.i386.deb
dpkg-deb: building package 'cupswrappermfc7360n' in 'cupswrapperMFC7360N-2.0.4-2a.i386.deb'.
dpkg -b ./brother_driver_packdir cupswrapperMFC7360N-2.0.4-2a.i386.deb
dpkg -i --force-all mfc7360nlpr-2.1.0-1a.i386.deb
Selecting previously unselected package mfc7360nlpr:i386.
(Reading database ... 236031 files and directories currently installed.)
Preparing to unpack mfc7360nlpr-2.1.0-1a.i386.deb ...
Unpacking mfc7360nlpr:i386 (2.1.0-1) ...
Setting up mfc7360nlpr:i386 (2.1.0-1) ...
dpkg -i --force-all cupswrapperMFC7360N-2.0.4-2a.i386.deb
Selecting previously unselected package cupswrappermfc7360n:i386.
(Reading database ... 236048 files and directories currently installed.)
Preparing to unpack cupswrapperMFC7360N-2.0.4-2a.i386.deb ...
Unpacking cupswrappermfc7360n:i386 (2.0.4-2) ...
Setting up cupswrappermfc7360n:i386 (2.0.4-2) ...
Restarting cups (via systemctl): cups.service.
#
Will you specify the Device URI? [Y/n] ->


> **Bucky Ball said:**
> Looks like you have unzipped it and are repeatedly trying to unzip it. You need this:

 

That should be it. Doesn't look to me, though, as if the model number you have given is correct. Should be longer than that. For instance, mine is an HL-2270DW. I doubt they have a model that is simply '7360N'. There would be a pre-fix in front.

And no, not:


The 'Brother' is not required so leave it out. The pre-fix of the model number is, though. If this doesn't work, try a 'sudo' at the beginning of the command (although shouldn't need one).

---

