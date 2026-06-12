---
title: "smbfs not cifs. accentuated characters solved"
date: 2008-03-19
forum: General Help
---

### Post by _StilLySh°&#945;°rK&#8729; on 2008-03-19
Shared folders for Linux and WinXP via -Ethernet--LAN-

Not only good for accentuated characters, it works with all weird symbols from Unicode set.
Any of those works fine to access shared folders:
```

mount  //192.168.15.123/a /home/b/c -t cifs -o username=d,password=e,uid=f,gid=g,iocharset=utf8
mount  //192.168.15.123/a /home/b/c -t cifs -o username=d,password=e,uid=f,gid=g,iocharset=utf8,codepage=cp437
mount  //192.168.15.123/a /home/b/c -t cifs -o username=d,password=e,uid=f,gid=g,iocharset=utf8,codepage=cp850

```
At first I was on the wrong track, believing that smbfs was better than cifs. It took me days to Google it out. In the following code box is this epic journey. It goes in minute details of what a Newbie will see.
This post has the top Google Rank in this topic: "accentuated + ...". Please improve it as needed or drop me a pm (private message) using this site.

If your Google search leads to the box below, please look up here.

**Further reading:**
Please search for: cifs smbfs      at     [http://ubuntuforums.org](http://ubuntuforums.org)

--------------------------- Your dedicated,  StiLy Shark

```

Again, this was the long difficult way:  ( ... the Newbie 's perspective )
---------------------------------------

My point is:  ( no, it was... )
smbfs works with accentuated character. cifs does not, as of march 2008.
This detailed overview allows readers to verify and improve knowledge on this topic.

Solution: a working example:
mount  //Host/a  /home/b/c -t smbfs -o username=d,password=e,uid=f,gid=g,iocharset=utf8,codepage=cp437

To have it done each time computer starts, just copy the line in the "/etc/rc.local" file.
The "/home/b/c" folder has to exist first. User "f" will own this directory (folder).
All users in group "g" will have full access.

Components:
-----------
Good PC with:     Linux
  Distribution:   Ubuntu 
  version:        7.04 (fiesty...!), or any Linux really...
  Installed:      samba software pakages: smbfs, samba, smbclient.
                  (throught Synaptic Package Manager) (again steep learning curve)

Bad P.C. with:    WinXP
  Abuser:         M$ (Micro$omething?)
  Virus:          WinDozeXP (Biggest virus ever ! )

Connection:       Ethernet, LAN... (local area network)
  Router:         Yes, or a long piece of copper and blue plastic with RJ45, wired pin to pin.
  Ethernet card:  That too... Or a socket on the motherboard of each PC. Or WiFi...


Context:
--------
Newbie ( someone who is new to Linux ), will be balked by the fact that, on a fresh install of Ubuntu 7.04, commands typed in a console (Accessories--> Terminal) will not work with the identifiers given for a network disk drive. The Newbie will first find through the Nautilus file browser such "not-connecting" syntax for network folders:
   network:///      (from: Menu--> Go--> Network)
   smb://hostName   (from: double clicking one of the connected hosts items)

Situation gets much worse when Newbie needs correct display of files names and directories, when such names includes accentuated characters ( à, é, è... and so on). After days+ of Googeling the mater & experimenting to reach a complete solution, the URGENT need for this funny & sound "HowTo" appears clearly.


Time line:
==========
Next logical step:
                  Google search for the most obvious command that fails to operate from console:
(Please note that "cp" is a Linux command for copying files.)


Google:  "cp smb://"
 ==>
    [http://www.unixboard.de/vb3/showthread.php?t=19928](http://www.unixboard.de/vb3/showthread.php?t=19928)
    20.05.2006, 10:31
 this thread refers to:  man smbmnt
===============


Next logical step:
                  Test this at the console:
                  man smbmnt
   ==> ...The program 'smbmnt' is currently not installed.  You can install it by typing:
                                                            sudo apt-get install smbfs
===============


Next logical steps:
                   Go to Synaptic and install that missing "smbmnt"
                   [ Here follows the "Package description" from Synaptic: ]
mount and umount commands for the smbfs (for kernels >= than 2.2.x) 
Smbfs is a fileSystem which understands the SMB/CIFS protocol.
 This is the protocol Windows for WorkGroups, Windows NT or
LAN Manager use to talk to each other. It was inspired by
samba, the program by Andrew Tridgell that turns any unix
site into a file server for DOS or Windows clients.


If you want to use command-line utilities like smbclient, smbtar
and/or smbspool you just need to install the smbclient package.
===============


Next logical steps:
                   Find related information so:

Google:  "man smbmnt"
    ==>
    [http://pwet.fr/man/linux/administration_systeme/smbmnt](http://pwet.fr/man/linux/administration_systeme/smbmnt)

man smbmnt (8) - helper utility for mounting SMB filesystems
------------------------------------------------------------
NAME
	smbmnt - helper utility for mounting SMB filesystems

SYNOPSIS
	smbmnt {mount-point} [-s <share>] [-r] [-u <uid>] [-g <gid>] [-f <mask>] [-d <mask>] [-o <options>] [-h]

DESCRIPTION
> smbmnt is a helper application used by the smbmount program to do the actual mounting of SMB shares.smbmnt can be installed setuid root if you want normal users to be able to mount their SMB shares.
> A setuid smbmnt will only allow mounts on directories owned by the user, and that the user has write permission on.
> The smbmnt program is normally invoked by smbmount(8). It should not be invoked directly by users.
> smbmount searches the normal PATH for smbmnt. You must ensure that the smbmnt version in your path matches the smbmount used.


OPTIONS
-r
    mount the filesystem read-only 
-u uid
    specify the uid that the files will be owned by 
-g gid
    specify the gid that the files will be owned by 
-f mask
    specify the octal file mask applied 
-d mask
    specify the octal directory mask applied 
-o options
    list of options that are passed as-is to smbfs, if this command is run on a 2.4 or higher Linux kernel. 
-h|--help
    Print a summary of command line options. 
===============


Next logical step:
                  Trying "smbmnt --help" in a Linux console:
  smbmnt --help
  ==> version 3.0.24
      ... less informative than the "man page" yet no contradictions... So:


Next logical step:
                  Trying to run the "smbmnt" with experimental variations:

## smbmnt /home/z/. -s temp
## crash in root            It CRASHES the computer every times !!!

Next logical step: Since the "smbmnt man page" refers to "smbmount":
                   Try at the console:
                                      smbmount --help
--------------------------------------------->  so to get this help: --->

Usage: mount.smbfs service mountpoint [-n] [-o options,...]

Version 3.0.24

Options:
      username=<arg>                  SMB username
      password=<arg>                  SMB password
      credentials=<filename>          file with username/password
      krb                             use kerberos (active directory)
      netbiosname=<arg>               source NetBIOS name
      uid=<arg>                       mount uid or username
      gid=<arg>                       mount gid or groupname
      port=<arg>                      remote SMB port number
      fmask=<arg>                     file umask
      dmask=<arg>                     directory umask
      debug=<arg>                     debug level
      ip=<arg>                        destination host or IP address
      workgroup=<arg>                 workgroup on destination
      sockopt=<arg>                   TCP socket options
      scope=<arg>                     NetBIOS scope
      iocharset=<arg>                 Linux charset (iso8859-1, utf8)
      codepage=<arg>                  server codepage (cp850)
      unicode                         use unicode when communicating with server
      lfs                             large file system support
      ttl=<arg>                       dircache time to live
      guest                           don't prompt for a password
      ro                              mount read-only
      rw                              mount read-write

This command is designed to be run from within /bin/mount by giving
the option '-t smbfs'. For example:
  mount -t smbfs -o username=tridge,password=foobar //fjall/test /data/test
---------------------------------------->


Next logical step:
There is evident lack of product consistency and support so:
Since all experimentation so far was dismally bad, the following information would be a minimal level of support to convince a Newbie that this time it will work well:

P.S. : Complementary usage of "smbmount"  --AKA--Also Known As-- "mount.smbfs"
---------------------------------------->

Usage:
      mount.smbfs "service" "mountpoint" [-n] [-o options,...]

|--> where "service" is typed like in the example above (//fjall/test),  Or this way:
     //hostName/shareName
     |--> where "hostName" is the name of the Bad computer.
              For WinXP, computer name is set through:
                    MyComputer--> ...properties--> "System properties"--> "Computer name"--> "Full computer name..."
     |--> where "shareName" is the name used when setting a folder as a "shared folder".
              Right-click a folder--> ...properties--> Sharing...--> (please try things in there...)
              For WinXP, simple file sharing can be set with:
                    "M$oft WinExlorer"--> Tools--> "Folder Options"--> View-->
                    ... --> "Advancedsettings"--> check the: "Use simple file sharing"
                    |--> any WinXP accounts will have access to the "shared folders"
                    |--> each accounts has: userName & password. password can be left empty, it will still connect.
                    |--> this setting is good for first trial but less secure.

              When: uncheck the: "Use simple file sharing" ==> not using simple file sharing:
                    (see above on how to set this, or visit M$oft empire)
                    |--> please create an account with long weird password
                          ...and allow permission only this account in menu setting "shared folders"

|--> where "mountpoint" is the:
     /data/test
     folder as above this post scriptum (P.S.)
     this folder better be set with permissions for the intended users or groups of users
     it is the name in Linux of the folder from the Bad computer that is shared.


Next logical step:
                  Experimenting with the command:

## smbmount //Host/a  /home/b/c
   ==> at this point the system pases a message to the user to go root.
       this seems to be ill advice since previous command crashed in root.
       Some more information and confirmation seems needed, so:

Next logical step:
                  See if any more information is available with this method:

Bar(Start)--> System--> HelpAndSupport-->  (help page of Ubuntu 7.04)
 --> AdvancedTopics--> InstallingServerApplications--> WindowsNetworking--> "Configuring Samba"--> 12.3.2.--Clients
The information in there has a different twist since it goes with the more classic and basic "mount" command, so:

Next logical step:
                  Trying this new approach:
mount  //Host/a  /home/b/c -t smbfs -o username=d,password=e,uid=f,gid=g,iocharset=utf8,codepage=cp437
# sudo mount -t smbfs -o username=d //Host/a /home/b/c

Much better ! Now the system asks for passwords. First the one for root and the the one for the host.
Since the system does not ask specifically which password it wants and in which order there is still a bit of experimenting but this is quick solved:
# Password: (rootPassWord)                <-- the first one asked by the system
# Password: (passWord for Bad computer)   <-- the second one asked.
## the "-t" means: type (of file system) in this ordinary mount command
## the "-o" means: options.
#############################################
#########  AND FINALLY IT WORKS !!! #########
#############################################

From here a bit more of experimenting to select what to trust from supplied more or less reliable documents will lead to the solution:
mount  //Host/a  /home/b/c -t smbfs -o username=d,password=e,uid=f,gid=g,iocharset=utf8,codepage=cp437
...that was already stated at the top of this "post--HowTo--Document".

Experimenting:
--------------
If despite help provided here, need for experimenting is still required, the following could be typed to Linux console:
  sudo sh /home/user/oneFile.sh
  password? ___________         <----(give the one for root...)
Before typing this, the file "oneFile.sh" is edited with gEdit (Text Editor)
...and saved to the "home" directory of the user e.g.: /home/user
Inside this file will be placed (by copy & paste...), the commands to be tested.

Each inadequate mounting can be undone at the console with:
  sudo umount /data/test

Previous commands typed at the console can be obtained using the arrows keys of the keyboard, so less typing is needed.

Experiments:
 sudo mount -p passWdFd
      ...to try many passWords when in doubts
 sudo chmod u+rwx /home/user/folder
      ...no use because the mount locks the permission. 

 sudo umount /home/z/abb
      ...after each experimental mounts.
=========================================================================================================


Next logical step:
                  Now that a working solution is verified:
                  See what is the reliable knowledge on this.

Accentuate: to accentuate: To mark with a written accent.
    [http://en.wiktionary.org/wiki/accentuate](http://en.wiktionary.org/wiki/accentuate)

Review of some main Sources & Links:
====================================

Google:  "smbfs"
  [http://linux-cifs.samba.org/](http://linux-cifs.samba.org/)
  [http://en.wikipedia.org/wiki/Samba_software](http://en.wikipedia.org/wiki/Samba_software)
  ==>>
      "linux-cifs-client-guide.pdf"
  This is supposed the be the main source and the reference for "smbmnt" which is the command that really works fine. Yet this WebSite states
      " ... smbmnt is deprecated ..."
  This is very odd  ! ! !     So:

Next logical step:
                  Try the new product that this source supports. It is the "cifs" product.
                  First check: yes there is a "mount.cifs" program in the "/sbin/."  folder in the Ubuntu 7.04 install.

Experimentations:
  mount -t cifs //tcp-name-of-server/sharename /mnt -o user=username,sec=lanman,servern=SERVERNAME
  mount -t cifs //9.53.216.11/e$               /mnt -o user=myname,pass=mypassword
  (many trials and errors later...)

Mounting using "cifs" works, yet, it never passes correctly the file or folder names with accentuated characters.
The main "cifs" source WebSite says nothing about the issue.
A Google search confirms that "cifs" users have difficulties with accentuated characters.


Google:  cifs accentuated     ==>
    [http://forums.alfresco.com/viewtopic.php?f=9&t=482&st=0&sk=t&sd=a&sid=85574326bcfb65931ba1bf3440f2eaea&start=15](http://forums.alfresco.com/viewtopic.php?f=9&t=482&st=0&sk=t&sd=a&sid=85574326bcfb65931ba1bf3440f2eaea&start=15)
    [http://readlist.com/lists/lists.samba.org/samba/3/17509.html](http://readlist.com/lists/lists.samba.org/samba/3/17509.html)
    [http://www.usenetlinux.com/archive/topic.php/t-838658.html](http://www.usenetlinux.com/archive/topic.php/t-838658.html)
    Good (it seems) since it confirms "cifs" lack of accentuated characters support.
    As of march 2008

Google:  cifs iocharset     ==>
    [http://lists.samba.org/archive/samba/2005-October/112139.html](http://lists.samba.org/archive/samba/2005-October/112139.html)
    Same thing. Bad "cifs".

Google:  "rc.local" ubuntu   ==>
   [http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)
   Permanent mount. Good explanation on "smbfs" yet not specific on accentuated characters.

Next logical steps:
   1- See if this post gets feedback... No feed back on the firs day.
   2- See if any places links to this -post--thread-   (it may take a while...) 
   3- See what is the Google Rank of this post  ==>

Who links to This -Post--thread-:
=================================
[http://www.google.com/search?as_lq=](http://www.google.com/search?as_lq=)
[http://www.google.com/search?as_lq=ubuntuforums.org%2Fshowthread.php%3Ft%3D728751](http://www.google.com/search?as_lq=ubuntuforums.org%2Fshowthread.php%3Ft%3D728751)



GoogleRank +_Time #Q #S [  -  Search terms   -                ] [ Notes  ...
========== ====== == == ======================================= =========================================
48/2600000 pT +5:H 1 48 accentuated                             -
 8/ 432000 pT +4:H 2  8 accentuated characters                  -
 8/1090000 pT +4:H 3  8 accentuated characters    how           -
 1/ 109000 pT +5:H 0  . accentuated characters    LAN           -
 1/ 252000 pT +3:H 0  . accentuated characters solved           -
 1/ 197000 pT +3:H 0  . accentuated            solved           -
 1/     43 pT+19:H 0  . accentuated            smbfs            -
--/  99900         0  . special     characters    samba         -non spécifique: "musique Samba"
--/  27900         0  . special     characters smbfs            -ok. spécifique
--/   1480         0  2 accent                 smbfs            -
.........................................................................................................
+_Time ==> This is the amount of time elapst betwin the GoogleRank and the moment when the post was made. 
           e.g. : post time +## ( H-Hours, D-Days, ...)
#S: scrutinized the first #S in Google Rank

#Q: Google Querry list:
=======================
0 [http://www.google.com](http://www.google.com)
1 [http://www.google.com/search?hl=en&q=accentuated&btnG=Search&num=100&start=40](http://www.google.com/search?hl=en&q=accentuated&btnG=Search&num=100&start=40)
2 [http://www.google.com/search?q=accentuated+characters&hl=en&start=6&sa=N](http://www.google.com/search?q=accentuated+characters&hl=en&start=6&sa=N)
3 [http://www.google.com/search?q=accentuated+characters+how&hl=en&start=6&sa=N](http://www.google.com/search?q=accentuated+characters+how&hl=en&start=6&sa=N)


Oooh !  This post is the first for this topic !
It better be wright or many Newbies will ...   :O

Next logical steps:
   1- Commitment:   Google ranks this thread as first on this topis so efforts to re-edit and keep up to date will be made.
   2- More sistematic experimentation...
                                                                                    
[--test result with characters:--]     remote          [------ options --------------] [ - Notes ...     
   ASCII        é, à...    russian    location         -t        iocharset= codepage=  
[----------]   [-------]  [-------][----------------]  [---]     [--------][---------] [-----------  ...
       ~100        100          0     //Host/a         smbfs      utf8       cp437      
       ~100        100          0     //Host/a         smbfs      utf8       cp850      
       ~100          0          0     //Host/a         smbfs      utf8                  option "codepage=" not used
       ~100          0          0     //Host/a         smbfs      iso8859-1  cp437      
       ~100          0          0     //Host/a         smbfs      iso8859-1  cp850      
       ~100          0          0     //Host/a         smbfs      iso8859-1             
       ~100          0          0     //Host/a         smbfs      iso8859-15 cp437      
       ~100          0          0     //Host/a         smbfs      iso8859-15 cp850      
       ~100          0          0     //Host/a         smbfs      iso8859-15            option "codepage=" not used
       ~100          0          0     //Host/a         smbfs      utf16      cp437      
       ~100          0          0     //Host/a         smbfs      unicode    cp437      
        --         --         --      //Host/a         cifs       utf8       cp437      **         
      100++        100        100  //192.168.15.100/a  cifs       utf8       cp437      
      100++        100        100  //192.168.15.100/a  cifs       utf8       cp850      
      100++        100        100  //192.168.15.100/a  cifs       utf8                  option "codepage=" not used
      100++        100        100      Host:a          cifs       utf8       cp437      
                                                                                    
**  Mount error: could not find target server.
    TCP name Host/a not found
    No ip address specified and host not found

*** retrying with upper case share name
    mount error 6 = No such device or address
    Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)



Google: accent smbfs
                    (the first in Google rank for this Querry:)  -->
_________________________________________________________________________________________________________
Author:     Steve French
Subject:    Re: Samba fc3: accent problem - smbfs vs cifs: msg#00041
Date:       2004-November
Posted on:  osdir.com
URL:        [http://osdir.com/ml/file-systems.cifs/2004-11/msg00041.html](http://osdir.com/ml/file-systems.cifs/2004-11/msg00041.html)
            [http://osdir.com/ml/file-systems.cifs/2004-11/msg00042.html](http://osdir.com/ml/file-systems.cifs/2004-11/msg00042.html)

Edited:     2008-march -- see the comments in the {} curved brakets.
Reason:     to improve readability
Edit By:    StiLy Shark.

{-------------------------------------------------------in november 2004, "Bertrand" said, Start  Quote:}
 I found a solution to the proper display of the the non-english
 characters (Ã©, Ã , Ã¨ ...Ã ) in the filenames from the server.

 Based on the /etc/samba/smb.conf    and the
              /etc/sysconfig/i18n    .

 As described below, I have changed one command line in the "fstab" file.
 In some case the accents displays properly and in others, it does not.
 Kind of weird... 

Here are the test results for each command lines in "/etc/fstab" file.

//192.168.0.4/bg  /mnt/server  cifs   rw,uid=bgirin,credentials=/etc/samba/pwd_bg,user                0 0
   ==> the accents displays properly. (It also works without the user option.)

//192.168.0.4/bg  /mnt/server  smbfs  rw,uid=bgirin,credentials=/etc/samba/pwd_bg,codepage=cp850      0 0
   ==> still, the accents displays properly.

//192.168.0.4/bg  /mnt/server  smbfs  rw,uid=bgirin,credentials=/etc/samba/pwd_bg,codepage=cp850,user 0 0
   ==> fail; it does not work anymore. {since "user" was included in the list of options.}
       Here, for Nautilus, any filename with accents are "-?-unicode invalid-?-".
{----------------------------------------------------------------------------------------------:End Quote}


That is interesting data.
    { Not kmowledge, not even information, --just data.    Well... ! }
I would expect cifs vfs to work {properly} as long as:

1) The server supports Unicode on the wire (Samba 3 and later can
   support Unicode, as does Windows)

2) The client codepage at mount time (nls charset) - in this case whatever
   code page is the default for the process is automounting  { -  *confused unclear*}
   these entries                                             {...}
   needs to be able to handle these entries                  {...}
   and it probably should match the default code page that nautilus was launched under.
   { ** or not ? ... !!  Speculetion. We need factual ansers. ** }

   cifs vfs also allows overriding the iocharset (the local nls charset used as the target
   of the unicode filename conversions) on the mount parm {parameters} (similar to what smbfs did).
   { So, } There is no need to specify code page.

All that cifs cares about is basically {, chararter code translation, }
 ( Unicode->nls charset and vice versa )
conversions - and the nls charset is taken from what is active when the
mount occurred.   Most earlier versions of smbfs did not support Unicode
so they {failed} had big problems with client codepage conversions.  

There is a bug in the cifs readdir code in unicode translations:
 {it manifests} when the target (e.g. UTF-8 encoded file name) is longer than it would be in Unicode (which is
not that common.  but { ...no, sorry. }

{It} happens often enough to cause problems for multiple {no, not multiple; many} users
who had emailed me).  {...no ")", sorry again}

In any case the cifs readdir code is rewritten from scratch
(available in svn on svn.samba.org in the linux-cifs-client project and the
master copy is in bk://cifs.bkbits.net/linux-2.5cifs pending additional testing
before I push it to Linus).

{-------------------------------------------------------------------------------------------Start Quote:}
Note that the when the user option is set-up, gnome automatically
 displays a shortcut to the mounted file on the desktop.
{------------------------------------------------------------------------------------------:End of quote}

With cifs or with smbfs?

{ Folowing this present post "Bertrand" replied whit this: }
{ "With both cifs and smbfs" }

_________________________________________________________
Steve French
Senior Software Engineer
Linux Technology Center - IBM Austin
     phone: 512-838-2294
     email: sfrench at-sign us dot ibm dot com
linux-cifs-client mailing list
linux-cifs-client@xxxxxxxxxxxxxxx
[http://lists.samba.org/mailman/listinfo/linux-cifs-client](http://lists.samba.org/mailman/listinfo/linux-cifs-client)
_________________________________________________________________________________________________________





```

---

