---
title: "Simple Scan &quot;unable to connect to scanner&quot;"
date: 2019-06-12
forum: General Help
---

### Post by sks24 on 2019-06-12
Printer: MFC9130CW
The computer is running 18.04.2 LTS.

Print via wifi works. But I can't initiate a scan using Simple Scan: "Failed to scan" "Unable to connect to scanner"

On my laptop running 16.04 I ran the same software from Brother in a terminal and it works fine via a USB connection. But this particular computer is two rooms away and it's not practical to run a physical connection. I tried [this]("https://ubuntuforums.org/showthread.php?p=13077954#post13077954") using "sudo apt-get libsane-extras" ; "invalid operation"  (Super-rusty here; I mostly use Chrome OS now.)

Before it installed the scanner it asked me for the IP address. See:

```
scott@scott-p7-1234:~$ cd Downloads
scott@scott-p7-1234:~/Downloads$ gunzip linux-brprinter-installer-2.2.1-1.gz
scott@scott-p7-1234:~/Downloads$ sudo bash linux-brprinter-installer-2.2.1-1 MFC9130CW
[sudo] password for scott: 
You are going to install following packages.
   mfc9130cwlpr-1.1.2-1.i386.deb
   mfc9130cwcupswrapper-1.1.4-0.i386.deb
   brscan4-0.4.8-1.amd64.deb
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

wget -T 10 -nd --no-cache http://www.brother.com/pub/bsc/linux/packages/mfc9130cwlpr-1.1.2-1.i386.deb
--2019-06-12 12:29:20--  http://www.brother.com/pub/bsc/linux/packages/mfc9130cwlpr-1.1.2-1.i386.deb
Resolving www.brother.com (www.brother.com)... 104.119.2.48
Connecting to www.brother.com (www.brother.com)|104.119.2.48|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 694532 (678K) [application/x-troff-man]
Saving to: ‘mfc9130cwlpr-1.1.2-1.i386.deb’

mfc9130cwlpr-1.1.2- 100%[===================>] 678.25K   510KB/s    in 1.3s    

2019-06-12 12:29:22 (510 KB/s) - ‘mfc9130cwlpr-1.1.2-1.i386.deb’ saved [694532/694532]


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

wget -T 10 -nd --no-cache http://www.brother.com/pub/bsc/linux/packages/mfc9130cwcupswrapper-1.1.4-0.i386.deb
--2019-06-12 12:29:23--  http://www.brother.com/pub/bsc/linux/packages/mfc9130cwcupswrapper-1.1.4-0.i386.deb
Resolving www.brother.com (www.brother.com)... 104.119.2.48
Connecting to www.brother.com (www.brother.com)|104.119.2.48|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13450 (13K) [application/x-troff-man]
Saving to: ‘mfc9130cwcupswrapper-1.1.4-0.i386.deb’

mfc9130cwcupswrappe 100%[===================>]  13.13K  --.-KB/s    in 0.002s  

2019-06-12 12:29:24 (8.51 MB/s) - ‘mfc9130cwcupswrapper-1.1.4-0.i386.deb’ saved [13450/13450]

Get:1 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
Hit:2 http://us.archive.ubuntu.com/ubuntu bionic InRelease                     
Get:3 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Ign:4 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:5 http://archive.canonical.com/ubuntu bionic InRelease                     
Hit:6 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:7 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease           
Get:9 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [643 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [536 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu bionic-updates/main Translation-en [239 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [934 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [947 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe Translation-en [280 kB]
Fetched 3,756 kB in 3s (1,439 kB/s)                            
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32ncurses5 lib32z1

E: Package 'ia32-libs' has no installation candidate
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  lib32gcc1 libc6-i386
The following NEW packages will be installed:
  lib32gcc1 lib32stdc++6 libc6-i386
0 upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
Need to get 3,114 kB of archives.
After this operation, 14.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libc6-i386 amd64 2.27-3ubuntu1 [2,651 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 lib32gcc1 amd64 1:8.3.0-6ubuntu1~18.04 [47.9 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 lib32stdc++6 amd64 8.3.0-6ubuntu1~18.04 [415 kB]
Fetched 3,114 kB in 1s (3,095 kB/s)   
Selecting previously unselected package libc6-i386.
(Reading database ... 156002 files and directories currently installed.)
Preparing to unpack .../libc6-i386_2.27-3ubuntu1_amd64.deb ...
Unpacking libc6-i386 (2.27-3ubuntu1) ...
Selecting previously unselected package lib32gcc1.
Preparing to unpack .../lib32gcc1_1%3a8.3.0-6ubuntu1~18.04_amd64.deb ...
Unpacking lib32gcc1 (1:8.3.0-6ubuntu1~18.04) ...
Selecting previously unselected package lib32stdc++6.
Preparing to unpack .../lib32stdc++6_8.3.0-6ubuntu1~18.04_amd64.deb ...
Unpacking lib32stdc++6 (8.3.0-6ubuntu1~18.04) ...
Setting up libc6-i386 (2.27-3ubuntu1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Setting up lib32gcc1 (1:8.3.0-6ubuntu1~18.04) ...
Setting up lib32stdc++6 (8.3.0-6ubuntu1~18.04) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
dpkg -x mfc9130cwlpr-1.1.2-1.i386.deb /
dpkg -x mfc9130cwcupswrapper-1.1.4-0.i386.deb /
dpkg-deb: building package 'mfc9130cwlpr' in 'mfc9130cwlpr-1.1.2-1a.i386.deb'.
dpkg -b ./brother_driver_packdir mfc9130cwlpr-1.1.2-1a.i386.deb
dpkg-deb: building package 'mfc9130cwcupswrapper' in 'mfc9130cwcupswrapper-1.1.4-0a.i386.deb'.
dpkg -b ./brother_driver_packdir mfc9130cwcupswrapper-1.1.4-0a.i386.deb
dpkg -i --force-all mfc9130cwlpr-1.1.2-1a.i386.deb
Selecting previously unselected package mfc9130cwlpr:i386.
(Reading database ... 156316 files and directories currently installed.)
Preparing to unpack mfc9130cwlpr-1.1.2-1a.i386.deb ...
Unpacking mfc9130cwlpr:i386 (1.1.2-1) ...
Setting up mfc9130cwlpr:i386 (1.1.2-1) ...
mkdir: cannot create directory ‘/var/spool/lpd/mfc9130cw’: No such file or directory
chown: cannot access '/var/spool/lpd/mfc9130cw': No such file or directory
chgrp: cannot access '/var/spool/lpd/mfc9130cw': No such file or directory
chmod: cannot access '/var/spool/lpd/mfc9130cw': No such file or directory
dpkg -i --force-all mfc9130cwcupswrapper-1.1.4-0a.i386.deb
Selecting previously unselected package mfc9130cwcupswrapper:i386.
(Reading database ... 156347 files and directories currently installed.)
Preparing to unpack mfc9130cwcupswrapper-1.1.4-0a.i386.deb ...
Unpacking mfc9130cwcupswrapper:i386 (1.1.4-0) ...
Setting up mfc9130cwcupswrapper:i386 (1.1.4-0) ...
Restarting cups (via systemctl): cups.service.
lpadmin -p MFC9130CW -E -v dnssd://Brother%20MFC-9130CW._ipp._tcp.local/?uuid=e3248000-80ce-11db-8000-c038961e1c7a -P /usr/share/cups/model/Brother/brother_mfc9130cw_printer_en.ppd
#
Will you specify the Device URI? [Y/n] ->y


0: cups-brf:/
1: socket
2: ipps
3: https
4: hp
5: lpd
6: ipp
7: beh
8: http
9: hpfax
10: dnssd://Brother%20HL-3140CW%20series._ipp._tcp.local/?uuid=e3248000-80ce-11db-8000-f8da0c7b0e2c
11: dnssd://Brother%20MFC-9130CW._ipp._tcp.local/?uuid=e3248000-80ce-11db-8000-c038961e1c7a
12: lpd://BRWF8DA0C7B0E2C/BINARY_P1
13: lpd://BRWC038961E1C7A/BINARY_P1
14: ipp://BRWF8DA0C7B0E2C.local:631/ipp/print
15: ipp://BRWC038961E1C7A.local:631/ipp/print
16 (I): Specify IP address.
17 (A): Auto. (dnssd://Brother%20MFC-9130CW._ipp._tcp.local/?uuid=e3248000-80ce-11db-8000-c038961e1c7a)

select the number of destination Device URI. ->17

lpadmin -p MFC9130CW -v dnssd://Brother%20MFC-9130CW._ipp._tcp.local/?uuid=e3248000-80ce-11db-8000-c038961e1c7a -E
Test Print? [y/N] ->y

wait 5s.
lpr -P MFC9130CW /usr/share/cups/data/testprint
You are going to install following packages.
   brscan4-0.4.8-1.amd64.deb

=========================================
Brother License Agreement

Brother retains any and all copyrights to the Software. In no case this Agreement shall be construed to assign or otherwise transfer from Brother to User any copyrights or other intellectual property rights to whole or any part of the Software.

Brother grants User a non-exclusive license: to reproduce and/or distribute (via Internet or in any other manner) the Software. Further, Brother grants User a non-exclusive license to modify, alter, translate or otherwise prepare derivative works of the Software and to reproduce and distribute (via Internet or in any other manner) such modification, alteration, translation or other derivative works for any purpose.

The license of the Software from Brother hereunder is granted "AS IS." BROTHER HEREBY DISCLAIMS ANY WARRANTIES WITH RESPECT TO THE SOFTWARE, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO WARRANTY FOR THE QUALITY, MERCHANTABILITY, FITNESS FOR PARTICULAR PURPOSE OR NON-INFRINGEMENT.
Brother shall have no liability in contract, tort (including negligence or breach of statutory duty) or otherwise for any interruption of use, loss of data, or for any indirect, incidental, punitive or consequential loss or damage, or for any loss of profit, revenue, data, goodwill or anticipated savings that arises under, out of, or in contemplation of this Agreement or otherwise arises due to any error, inaccuracy or defect in the Software even if Brother has been advised of the possibility of such loss or damage.
Further, Brother shall have no liability to disclose and/or distribute the source cord of the Software to User under any circumstances. In no case shall the above license by Brother to modify, alter, translate or otherwise prepare derivative works of the Software be construed as Brother's implied agreement or undertakings to disclose and/or distribute the source cord of the Software.
=========================================
Do you agree? [Y/n] ->y

wget -T 10 -nd --no-cache http://www.brother.com/pub/bsc/linux/packages/brscan4-0.4.8-1.amd64.deb
--2019-06-12 12:33:03--  http://www.brother.com/pub/bsc/linux/packages/brscan4-0.4.8-1.amd64.deb
Resolving www.brother.com (www.brother.com)... 184.25.198.43
Connecting to www.brother.com (www.brother.com)|184.25.198.43|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 114244 (112K) [application/x-troff-man]
Saving to: ‘brscan4-0.4.8-1.amd64.deb’

brscan4-0.4.8-1.amd 100%[===================>] 111.57K  --.-KB/s    in 0.07s   

2019-06-12 12:33:03 (1.63 MB/s) - ‘brscan4-0.4.8-1.amd64.deb’ saved [114244/114244]

dpkg -i --force-all brscan4-0.4.8-1.amd64.deb
Selecting previously unselected package brscan4.
(Reading database ... 156351 files and directories currently installed.)
Preparing to unpack brscan4-0.4.8-1.amd64.deb ...
Unpacking brscan4 (0.4.8-1) ...
Setting up brscan4 (0.4.8-1) ...
This software is based in part on the work of the Independent JPEG Group.
You are going to install following packages.
   brscan-skey-0.2.4-1.amd64.deb

=========================================
Brother License Agreement

Brother retains any and all copyrights to the Software. In no case this Agreement shall be construed to assign or otherwise transfer from Brother to User any copyrights or other intellectual property rights to whole or any part of the Software.

Brother grants User a non-exclusive license: to reproduce and/or distribute (via Internet or in any other manner) the Software. Further, Brother grants User a non-exclusive license to modify, alter, translate or otherwise prepare derivative works of the Software and to reproduce and distribute (via Internet or in any other manner) such modification, alteration, translation or other derivative works for any purpose.

The license of the Software from Brother hereunder is granted "AS IS." BROTHER HEREBY DISCLAIMS ANY WARRANTIES WITH RESPECT TO THE SOFTWARE, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO WARRANTY FOR THE QUALITY, MERCHANTABILITY, FITNESS FOR PARTICULAR PURPOSE OR NON-INFRINGEMENT.
Brother shall have no liability in contract, tort (including negligence or breach of statutory duty) or otherwise for any interruption of use, loss of data, or for any indirect, incidental, punitive or consequential loss or damage, or for any loss of profit, revenue, data, goodwill or anticipated savings that arises under, out of, or in contemplation of this Agreement or otherwise arises due to any error, inaccuracy or defect in the Software even if Brother has been advised of the possibility of such loss or damage.
Further, Brother shall have no liability to disclose and/or distribute the source cord of the Software to User under any circumstances. In no case shall the above license by Brother to modify, alter, translate or otherwise prepare derivative works of the Software be construed as Brother's implied agreement or undertakings to disclose and/or distribute the source cord of the Software.
=========================================
Do you agree? [Y/n] ->y

wget -T 10 -nd --no-cache http://www.brother.com/pub/bsc/linux/packages/brscan-skey-0.2.4-1.amd64.deb
--2019-06-12 12:33:06--  http://www.brother.com/pub/bsc/linux/packages/brscan-skey-0.2.4-1.amd64.deb
Resolving www.brother.com (www.brother.com)... 184.25.198.43
Connecting to www.brother.com (www.brother.com)|184.25.198.43|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 50852 (50K) [application/x-troff-man]
Saving to: ‘brscan-skey-0.2.4-1.amd64.deb’

brscan-skey-0.2.4-1 100%[===================>]  49.66K  --.-KB/s    in 0.04s   

2019-06-12 12:33:06 (1.11 MB/s) - ‘brscan-skey-0.2.4-1.amd64.deb’ saved [50852/50852]

dpkg -i --force-all brscan-skey-0.2.4-1.amd64.deb
Selecting previously unselected package brscan-skey.
(Reading database ... 156401 files and directories currently installed.)
Preparing to unpack brscan-skey-0.2.4-1.amd64.deb ...
Unpacking brscan-skey (0.2.4-1) ...
Setting up brscan-skey (0.2.4-1) ...
apt-get install libusb-0.1-4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libusb-0.1-4
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 17.1 kB of archives.
After this operation, 57.3 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libusb-0.1-4 amd64 2:0.1.12-31 [17.1 kB]
Fetched 17.1 kB in 0s (91.0 kB/s)       
Selecting previously unselected package libusb-0.1-4:amd64.
(Reading database ... 156407 files and directories currently installed.)
Preparing to unpack .../libusb-0.1-4_2%3a0.1.12-31_amd64.deb ...
Unpacking libusb-0.1-4:amd64 (2:0.1.12-31) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Setting up libusb-0.1-4:amd64 (2:0.1.12-31) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
 enter IP address ->192.168.86.186

brsaneconfig4 -a name=MFC-9130CW model=MFC-9130CW ip=192.168.86.186
scott@scott-p7-1234:~/Downloads$ 


```

---

