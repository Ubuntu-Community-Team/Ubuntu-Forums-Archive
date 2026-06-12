---
title: "I Need help with VM Additions"
date: 2007-04-15
forum: General Help
---

### Post by Loki-uk on 2007-04-15
Hi recently Microsoft have released vm additions for virtual server. Now these additions have only been tested on red hat and suse but I have read comments of users getting them to work on ubuntu and I would like to do the same. I'm using Virtual PC not server and Ubuntu not Red Hat/Suse but it's achievable so I've read. I have only been using Linux for 4 days now so I'm not really sure how to do what I need to do.

I have read other users posts who have it working but I must be missing something. I have  tried lots of ways to get these going, I have installed the file using rpm and I have even converted it to a .deb and installed them, To do both I have to install chkconfig which was a mission in itself. If I try to run the rpm version I get the follow error message during installation

error: Failed dependencies:
        /bin/bash is needed by vmadd-full-0.0.1-1.i386
        /bin/sh is needed by vmadd-full-0.0.1-1.i386
        /sbin/chkconfig is needed by vmadd-full-0.0.1-1.i386
        /sbin/ldconfig is needed by vmadd-full-0.0.1-1.i386
        fileutils is needed by vmadd-full-0.0.1-1.i386
        libc.so.6 is needed by vmadd-full-0.0.1-1.i386
        libc.so.6(GLIBC_2.1.3) is needed by vmadd-full-0.0.1-1.i386

Converting it to a deb using alien and installing everything seems to install (once chkconfig is up and running) without any errors but when I try to run /etc/init.d/vmadd start I get an error saying kernel module not found. I suspect that this is related to the errors in the rpm install about missing files.


user@user-desktop:~$ //etc/init.d/vmadd start
(kernel module not found)...fail!
user@user-desktop:~$


 I suspect that both installation are in the right places but just missing things to make them work. Any help anyone could give me would be greatly appreciated. I have learned so much in this 4 for days I've been amazed although I may be starting out with something that's a bit beyond me skill set lol :D  If you never stretch yourself you'll neverr grow...

 have had a look in the /bin and /sbin foldes and the files listed are present. Can anyone help. Obi Wan are you there dude?

I'm away froom my PC now for 4 days AAARRRHGGGHHHH lol

Thanks

Brian

---

### Post by Loki-uk on 2007-04-15
Do I need to be a 'root' user to run these commands? If so how do I  change to the root user in ubuntu. I've enabled a password in the  terminal and show in the manual (man sudo_root) but I can not login from the main login screen? How does the 'root' user login?

Thanks

---

### Post by spankymasterc on 2007-04-15
well i dont know what u are doing but im sure i could help

ok in order to run a command a root u have to add sudo before any command 

eg. sudo alien (file_name)

now when u made the .rpm file into a .deb what command did u use?

if im not mistaked u problably didnt include the scripts...

so my suggestion would be do this 

sudo alien --sripts File_name -d and that will create a deb package with everything in it.....

hope it helps and if u need further help add me on msn,yahoo. or aim look at my profile cheers::::::

---

### Post by Loki-uk on 2007-04-15
Hello

If I tell you what setup I have first and what it is I'm trying to do. I am running Ubuntu 6.06.1 LTS in a virtual machine under Virtual PC 2007. MS offer two free emulators virtual pc and virtual server. They produce vm additions which include things like upgraded graphices card drivers, better mouse integration between OS's etc. The defalut config for Virtual PC only emulates a basic s3 video card which supports 800 x 600 x 16. They have released VM Additoins for most windows OS's running as a guest OS to imrpove this. They have just released VM Additions for Virtual Server for Red Hat and Suse (Virtual PC & Server are very similar and largely interchangable, server has better support for server OS's and some extra tools and options). What I am trying to do is get the VM Additions installed so that I can get the updated drivers into Ubuntu.

The vm additions are distributed as a file called vmadd-full-0.0.1-1.i386.rpm now I have tried installing this using the following command rpm -i vmadd-full-0.0.1-1.i386.rpm --force which causses the errors which are listed below. Originally 'chkconfig' was missing but eventually I found out how to make and install that phew that was a mission lol i installed the build-essential package and got it going but now I know how to do that it'll always be useful) and I saw on  a post elsewhere sommeone using rpm -i vmadd-full-0.0.1-1.i386.rpm --force --nodeps to install it but this makes no difference and it just hides the problem. 

Someone sugguested to me that I needed to convert the rpm to a deb and install that instead. You are right the first time I did it it prompted me about the scripts so I did it again with the --scripts parameter 'sudo alien ./vmadd-full-0.0.1-1.i386.rpm --scripts', it does give a warning on one line but no errors. Which I did and it does indeed install now without any errors using 'sudo dpkg -i ./vmadd-full_0.0.1-2_i386.deb' alien changed the name slightly not me. But when I try to run it with the //etc/init.d/vmadd start command as I'm supposed to I get (kernel module not found)...fail!. I can only assume that I am missing something relating to the original rpm error messages below but when I look in the /sbin and /bin folders the programs look to be there bash /sh etc, im not sure what the fileutil is but the libc sees to be installed.

error: Failed dependencies:
/bin/bash is needed by vmadd-full-0.0.1-1.i386   [COLOR="red"]<< This is present[/COLOR]
/bin/sh is needed by vmadd-full-0.0.1-1.i386   [COLOR="red"]<< This is present[/COLOR]
/sbin/chkconfig is needed by vmadd-full-0.0.1-1.i386   [COLOR="red"]<< This wasn't present but is now[/COLOR]
/sbin/ldconfig is needed by vmadd-full-0.0.1-1.i386  [COLOR="red"]<< This is present[/COLOR]
fileutils is needed by vmadd-full-0.0.1-1.i386  [COLOR="red"]<< Not sure about this[/COLOR]
libc.so.6 is needed by vmadd-full-0.0.1-1.i386   [COLOR="red"]<< I think this is present[/COLOR]
libc.so.6(GLIBC_2.1.3) is needed by vmadd-full-0.0.1-1.i386   [COLOR="red"]<< I think this is present[/COLOR]

One of the posts I read said that I needed to be in full 'root' to do this but I'm not sure how true that is. I know Ubuntu doesn't have that enabled by default and that you can turn it on with the 'sudo passwd root' command and off again with the 'sudo passwd -l root' command. I have turned it on but then I don't know how to log in as 'root' I can't do it from the main login it says root can not log in from there and being so new I don't know where else to login from.

Any help you could give me would be appreciated I've been at this for two days solid (i'm not joking lol must be 20hrs + lol but it's fun and i'm learning so...). But it would just be nice to get it to work it seems to be so close. VMAdd modifies system modules which I why I was wondering if the root user was need.

Thanks

Brian

I just noticed that I should of been using -ivh 'rpm -ivh vmadd-full-0.0.1-1.i386.rpm --force'. It just did and it did the same thing. Using the --nodeps this time was slightly different.

root@user-desktop:/home/user# rpm -ivh vmadd-full-0.0.1-1.i386.rpm --force --nodeps
Preparing...                ########################################### [100%]
   1:vmadd-full             ########################################### [100%]
Messages displayed during installation will be logged to /var/log/vmadd-install.log

It still has exactly the same error.

This is the LOG FILE

*** VM additions kernel module ***
make: Entering directory `/lib/modules/vmadd/module'
Cannot build module, kernel sources are probably not installed
make: *** [/lib/modules/2.6.15-28-386/build/Makefile] Error 1
make: Leaving directory `/lib/modules/vmadd/module'
Could not build kernel module

Installing...
make: Entering directory `/lib/modules/vmadd/module'
Cannot build module, kernel sources are probably not installed
make: *** [/lib/modules/2.6.15-28-386/build/Makefile] Error 1
make: Leaving directory `/lib/modules/vmadd/module'
Could not install kernel module

Installing kernel module system service...
*** Done ***
*** VM additions SCSI kernel module ***
make: Entering directory `/lib/modules/vmadd/scsi'
Cannot build module, kernel sources are probably not installed
make: *** [/lib/modules/2.6.15-28-386/build/Makefile] Error 1
make: Leaving directory `/lib/modules/vmadd/scsi'
Could not build SCSI kernel module

Installing...
make: Entering directory `/lib/modules/vmadd/scsi'
Cannot build module, kernel sources are probably not installed
make: *** [/lib/modules/2.6.15-28-386/build/Makefile] Error 1
make: Leaving directory `/lib/modules/vmadd/scsi'
Could not install SCSI kernel module

Installing SCSI kernel module system service...
*** Done ***

I just read in the VM Additions readme - A kernel module of the additions is built at compile time. so, the virtual machine should have the linux kernel source and build tools installed [COLOR="Red"]Do you think that means I have to recompile the kernel? I'm even more confused now :)[/COLOR]

---

### Post by Loki-uk on 2007-05-04
It's OK I finally figured it out and have it installed what a mission. Thanks

Loki

---

### Post by raf2u on 2007-08-05
Hi Loki,

Could you, please, publish a short overview of the steps you took to get the VM Additions installed in Ubuntu? Also, did you notice any improvements (SCSI drivers, time sync, etc.)?

Thanks,
R.

---

### Post by Richard Hunt on 2007-11-21
I'd also appreciate a step-by-step guide to installing the VM Additions in Ubuntu.  Has it been published please?

---

### Post by brakness on 2008-02-20
Looks like he/she forgot about us!
[http://www.eggheadcafe.com/software/aspnet/29873803/vm-additions-in-ubuntu-.aspx](http://www.eggheadcafe.com/software/aspnet/29873803/vm-additions-in-ubuntu-.aspx)

---

