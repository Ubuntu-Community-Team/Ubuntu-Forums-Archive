---
title: "Anyone running XSI in Ubuntu?"
date: 2005-06-01
forum: General Help
---

### Post by fxgogo on 2005-06-01
I am thinking of getting the Foundation version of XSI for Linux. Have you had any problems running it in Ubuntu? How does it match up?

---

### Post by BMWolf on 2006-03-19
I know this is old, but i would like to know as well.

I'd like to switch the majority of my work over to Ubuntu rather than Fedora or Suse, and do all my video work on windows. 

The foundation trial installs ok by tcsh, but i get a segmentation fault when i launch the application. Ubuntu isn't on the supported list at softimage.com, so i'm curious if anyone here is running it or if they could give the trial a shot. I'm no linux Expert by any means so any help would be appreciated. 

PS. I know it's possible as someone on cgtalk mentioned running the trial.

[http://www.softimage.com/products/xsi/system_requirements/linux/Default.aspx](http://www.softimage.com/products/xsi/system_requirements/linux/Default.aspx)

---

### Post by ralfsmith on 2006-03-22
Oh its very interesting. Could you provide me more information ?

[email]max@digitalhardcore.us[/email]

---

### Post by BMWolf on 2006-03-24
Information on the Seg Fault?

---

### Post by oZen on 2006-05-27
Hello, I'm looking for a solution about segmentation fault, if you have any, could you provide me the solution please ?

Thx in advance !

PS: I'm running Dapper Drake.

---

### Post by BMWolf on 2006-07-13
Thought I'd bring this back again. Someone is actually running XSI on Ubuntu.
[http://www.xsibase.com/forum/index.php?board=9;action=display;threadid=23898;start=42](http://www.xsibase.com/forum/index.php?board=9;action=display;threadid=23898;start=42)

I'll be giving it another shot here soon.

---

### Post by jmadman on 2006-09-04
Ubuntu Dapper - 'scn could not be opened' error
--------------------------------------------------------------------------

I have XSI 5.11 running on dapper 6.06.1 LTS.
I've solved the seg faults on startup, and it seems to run very nicely apart from two crippling problems.

1) consistent 'scn could not be opened error' at the 'Loading environment... 65%" stage.
2) segfaults on MERGE scenes.

The only error during installation is 'Error: Creating libgcc_s.so symbolic link'

So close yet so far...

Has any one come any closer to a solution for this insanely irritating problem?

Below are all the steps i've taken to get this far, if anybody can think of anything I haven't tried, or actually has XSI opening scenes in Dapper, please help!

-------------------------------------------------------------------
HARDWARE: Intel Xeon CPU 3.60GHz , 2GB RAM , Nvidia Quadro FX 3400 

Firewall
    There are no firewalls or antivirus running on ether localhost or license server.

Video Drivers
    The latest Nvidia drivers caused XSI to segfault on start up. Installing the 7676 as certified on the [XSI site]("http://www.softimage.com/Products/Xsi/v5/sysreqs/Linux.htm") fixed the problem. The driver installer had to be patched to compile on 2.6.16 kernel. Patch is [here]("http://www.nvnews.net/vbulletin/showthread.php?t=66750&highlight=7676+dapper")for any interested. I've compiled the nvidia kernel successfully for both 2.6.16-26-386 and 2.6.16-26-686. Compiling was done with gcc 4.0 ( i tried gcc 3.6 as well but compile failed ) 
    glxinfo | grep "direct rendering" confirms direct rendering. 

XSI Requirements
    Kernel 2.4.18-3 – 2.6.11
        Tested on both 2.6.16-26-386 and 2.6.16-26-686 producing exactly the same problem.

    XFree86, XFree86-libs: 4.2.0, 4.3.0
        dapper uses Xorg instead of Xfree86. Latest version of xserver-xorg-core is installed : 1:1.0.2-0Ubuntu10.4        
        I can find no way to actually install Xfree86 even if i wanted to, but indications are that i shouldn't have to as they're effectively the same thing.

    Windows manager
        Metacity 1:2.14.5

    glibc 2.2.x, 2.3.x   
        dapper ships with glibc 2.3.6 
        possibly related packages installed : libc6 libc6-dev libc-1686 libglib1.2 libglib2.0-0 libglib2.0-0-data

    libjpeg
        installed : libjpeg62 libjpeg62-dev libjpeg-progs libjpeg-mmx-progs

    libncurses
        installed : libncurses4 libncurses5 libncuresew5 libncurses5-dev libncurses5-dbg

    e2fsprogs
        installed : e2fsprogs

    fam-server or gamin
        installed : gamin    

    sed, textutils, grep, fileutils, xinetd, bzip2, tar
        all installed

Xorg Flags
    i have tried adding the following lines to xorg.conf in the Device section
        Option          "MultisampleCompatibility" "1"
        Option          "NvAGP"         "1"              ( i have tested all options 1-4 )

Python path in /usr/Softimage/XSI_5.11/.xsi_5.11
    setenv PYTHONPATH   "${XSI_BINDIR}:${PYTHONPATH}:/usr/lib/python2.4/site-packages"

Permissions
    I've tried running as root, changing permissions on project directories, and ~/Softimage ( also tried completely removing ~/Softimage )

That about covers it i think. 

Any suggestions ?

Need help...

---

### Post by RunsWithScissors on 2006-09-21
XSI installs no problem then I get this


mohawk:/usr/Softimage/XSI_5.11/Application/bin> ./xsi
YOU HAVEN'T DISABLED SET-ID SCRIPTS IN THE KERNEL YET!
FIX YOUR KERNEL, PUT A C WRAPPER AROUND THIS SCRIPT, OR USE -u AND UNDUMP!
YOU HAVEN'T DISABLED SET-ID SCRIPTS IN THE KERNEL YET!
FIX YOUR KERNEL, PUT A C WRAPPER AROUND THIS SCRIPT, OR USE -u AND UNDUMP!
grep: Command not found.
head: Command not found.
sed: Command not found.
xset: Command not found.
xset: Command not found.
xset: Command not found.
hostname: Command not found.
cp: Command not found.
ps: Command not found.
egrep: Command not found.
/usr/Softimage/XSI_5.11/Application/mainwin/mw/bin-linux_optimized/mwcleanup: er ror while loading shared libraries: libkernel32.so: cannot open shared object fi le: No such file or directory
/usr/Softimage/XSI_5.11/Application/bin/linux-x86-p3/XSI: error while loading sh ared libraries: libctrls.so: cannot open shared object file: No such file or dir ectory
mohawk:/usr/Softimage/XSI_5.11/Application/bin>


anyone know whats going on here?

---

### Post by corstar on 2006-09-26
Did your installation succeed?
Mine didn't. it spat out a dozen or so errors about not being able to install a bunch o f stuff.
There doen't seem to be much help for this on the net.

---

### Post by RunsWithScissors on 2006-09-26
nope I still have not gotten any response. Sux too I don't wanna switch to Suse

---

### Post by LedStyle on 2006-10-21
Maybe the solution is here: [http://www.xsibase.com/forum/index.php?board=9;action=display;threadid=21281;start=0](http://www.xsibase.com/forum/index.php?board=9;action=display;threadid=21281;start=0)

But i dont know exactly what to do with the file ".xsi_5.11"

What i have to chance on it?

---

### Post by Lee Davies on 2006-12-21
After downloading the Foundation trial... I have no idea how to get this installed! :confused: 

Can anyone please help me?

---

### Post by RunsWithScissors on 2006-12-21
extract the archive then using a terminal navigate to that directory.

I forget the name on the install script I thik it is just install or setup but anyway once in that directory type 
$sudo ./NameOfInstallScript

but I can tell you now that XSI is not going to work on ubuntu. This is a well documented issue.

---

### Post by Lee Davies on 2006-12-21
Other people seem to have it installed on Ubuntu, mainly in the link provided a few posts up...

But thanks!

It did install, and then spat out several errors about "sireg".

---

### Post by disciplefk on 2007-03-29
Just wanted to see if there is anyone with xsi 6.0 on edgy or dapper?

---

### Post by NNois on 2007-05-04
Yes i want to know too, if xsi 6 works on the greatest ubuntu ;-)

---

### Post by rem7 on 2007-06-16
anybody has 6.1 working?

---

