---
title: "Citrix Client"
date: 2008-05-16
forum: General Help
---

### Post by jfrenil_II on 2008-05-16
I am longing for an Official Citrix-package for Ubuntu that can provide a hassle-free installation of the Citrix Client. Today one has to cross some threads and learn the best way, that in the end, hopefully will bring the ICA protocol to the Ubuntu Desktop. 

The task consists of creating symbolic links, installing some related packages and uncompress a tar-ball in the right path...etc etc

Please, can anyone with the right contacts at Citrix look into this and help me out.



Fredrik Nilstromer
IT-directory, The Municipality of Ulricehamn, Sweden

Get down to Ubuntu-business!

---

### Post by Vadi on 2008-05-16
I think you should poke the Citrix people about it too, afaik Canonical doesn't exactly go about offering the service.

---

### Post by dtmilano on 2008-05-23
The first they should do (IMHO) is to completely rewrite the Linux client and use more modern libraries and desktop integration.

---

### Post by windependence on 2008-05-25
> **dtmilano said:**
> The first they should do (IMHO) is to completely rewrite the Linux client and use more modern libraries and desktop integration.

Huh? Oh you mean like Windoze. A tightly coupled front and back end is never a good idea. Look at the most tightly coupled OS on the planet and tell me if you want THAT to be Linux.

-Tim

---

### Post by Caseyjp on 2008-07-20
Yeah, but in the interim we NEED this freakin' p.o.s. to work.  Right now the seamless stuff is useless with compiz (the seamless windows of citrix clients zero out on change of desktop or cube face), and under metacity the stability and positioning of windows is frankly attrocious.  

The current level of "work" is going to force our group back to XP.

---

### Post by Vadi on 2008-07-20
That sucks. Have you tried contacting them about this issue?

---

### Post by brion@cbkidder.com on 2008-07-24
I too need a Citrix client app for use within Ubuntu. I hate being chained to Windows!

---

### Post by rahmath on 2008-07-25
This note is prepared for our team... have a look at it.. it is straight to the task... Hope this will help u...



HOWTO:	Citrix ICA Client Installation on Linux Box
Date:	22/07/2008
Author: Rahmathulla K M
	Linux Admin
	IT Department
	

Introduction
------------

This HOWTO defines the easy procedures to perform a successfull installation of Citrix ICA Client on Linux Box. Practically i had done this only on Ubuntu 8.04. But accroding to my experience, most probably this procedure should work with many of the other distribution as in the same way.

Downloading ICA
---------------
Citrix ICA Client is free to download from Citrix website. Current version of ICA client can be downloaded from [http://download2.citrix.com/FILES/en/products/Linux10/en.linuxx86.tar.gz](http://download2.citrix.com/FILES/en/products/Linux10/en.linuxx86.tar.gz)

Installation - A,b,c...
------------

Once you compelte the download, you will have a file called en.linuxx86.tar.gz in your local hard disk. Keep in your mind that this is a zipped archive file (in this file name, the .gz specifies that its a gzipped file and the .tar specifies that its a tape archive file).

So its always better to do the extraction and other installation related activities from a temporary directory, so that if something goes wrong, we can
easily delete the entire directory without causing any problem to our working environment

Right now, i am in my home directory --> /home/kmr (and our downloaded file is in my home directory --> /home/kmr/en.linuxx86.tar.gz

So create a directory called citrix (it can be any name) in the /tmp
$ mkdir /tmp/citrix

Then copy our dowloaded package file to this newly created directory
$ cp en.linuxx86.tar.gz /tmp/citrix 

Now unpack the zipped file
kmr@KMRLapBEM:~$ cd /tmp/citrix/
kmr@KMRLapBEM:/tmp/citrix$
kmr@KMRLapBEM:/tmp/citrix$ ls
en.linuxx86.tar.gz
kmr@KMRLapBEM:/tmp/citrix$ gunzip en.linuxx86.tar.gz

Now if you run 'ls' command on /tmp/citrix, you will see the pacakge file which is extracted, without the .gz extension
kmr@KMRLapBEM:/tmp/citrix$ ls
en.linuxx86.tar
kmr@KMRLapBEM:/tmp/citrix$

Next is to unpack the archive with 'tar' command
kmr@KMRLapBEM:/tmp/citrix$ tar xf en.linuxx86.tar
kmr@KMRLapBEM:/tmp/citrix$ ls
en.linuxx86.tar  eula.txt  install.txt  linuxx86  PkgId  readme.txt  setupwfc
kmr@KMRLapBEM:/tmp/citrix$

note that, few more files and directories and files are in place after the successfull extraction from the tape archive

Now run the installation script with 'sudo'
kmr@KMRLapBEM:/tmp/citrix$ sudo ./setupwfc

Answer the questions prompted during installation. When it prompts for install directory, go with the default location (/usr/lib/ICAClient) itself. But when it prompts for "Integrate Citrix Automatically", say NO. We will do it manually.

Now the installation is over, and its the time to place a link on our desktop for an easy access to our citrix server.

Required Dependencies
---------------------

In order to go further, we need 3 dependent packages to run our Citrix client. So, now we are going to install those dependencies.

kmr@KMRLapBEM:~$ sudo aptitude install menu motif-clients libmotif3

This command will install those 3 dependencies.

Creating Desktop Link
---------------------

For this, go to your 'Desktop' directory in your home directory.
kmr@KMRLapBEM:~$ cd Desktop
kmr@KMRLapBEM:~/Desktop$ pwd
/home/kmr/Desktop
kmr@KMRLapBEM:~/Desktop$

Then run the following command;
kmr@KMRLapBEM:~/Desktop$ ln -s /usr/lib/ICAClient/wfcmgr citrix-client
kmr@KMRLapBEM:~/Desktop$ ls
citrix-client
kmr@KMRLapBEM:~/Desktop$

Thats all!!! Alhamdulillahhh, things are configured and now you can just double click on the 'citrix-client' icon shown in your desktop.

Conclusion
----------

The document is prepared straight to the point. So you will find it easy for installation but at the same time, this will not save you in troubleshooting 
this procedures. So if anything goes wrong, or if you are in need of a supportive hand, please feel free to post here...

---

### Post by brion@cbkidder.com on 2008-07-25
Thank you Rahmath, but when I try to launch the Citrix window I still get an error saying I need to download the web client. Without it, the applet just tries to launch the ICA and doesn't know how. Thanks anyway.

---

### Post by rahmath on 2008-07-26
Brion,

I didnt understand about ur problem.

1. Did u completed all those steps, in the same order...
2. In which OS/version u tried it?

If any error message is there, please let me know that too...

---

### Post by ozzyprv on 2008-09-29
This is the error I get:
> wfcmgr: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory


---

### Post by TpyKv on 2008-10-03
You need the libmotif libraries - 

sudo apt-get install libmotif3

thinking about it you're most likely going to need to create a security certificate as well....

(type this in the terminal)

sudo gedit ~/ICAClient/linuxx86/keystore/cacerts/UTN-USERFirst-Hardware.crt

(and paste into it the following lines (including those with BEGIN and END)):

-----BEGIN CERTIFICATE-----
MIIEdDCCA1ygAwIBAgIQRL4Mi1AAJLQR0zYq/mUK/TANBgkqhkiG9w0BAQUFADCB
lzELMAkGA1UEBhMCVVMxCzAJBgNVBAgTAlVUMRcwFQYDVQQHEw5TYWx0IExha2Ug
Q2l0eTEeMBwGA1UEChMVVGhlIFVTRVJUUlVTVCBOZXR3b3JrMSEwHwYDVQQLExho
dHRwOi8vd3d3LnVzZXJ0cnVzdC5jb20xHzAdBgNVBAMTFlVUTi1VU0VSRmlyc3Qt
SGFyZHdhcmUwHhcNOTkwNzA5MTgxMDQyWhcNMTkwNzA5MTgxOTIyWjCBlzELMAkG
A1UEBhMCVVMxCzAJBgNVBAgTAlVUMRcwFQYDVQQHEw5TYWx0IExha2UgQ2l0eTEe
MBwGA1UEChMVVGhlIFVTRVJUUlVTVCBOZXR3b3JrMSEwHwYDVQQLExhodHRwOi8v
d3d3LnVzZXJ0cnVzdC5jb20xHzAdBgNVBAMTFlVUTi1VU0VSRmlyc3QtSGFyZHdh
cmUwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQCx98M4P7Sof885glFn
0G2f0v9Y8+efK+wNiVSZuTiZFvfgIXlIwrthdBKWHTxqctU8EGc6Oe0rE81m65UJ
M6Rsl7HoxuzBdXmcRl6Nq9Bq/bkqVRcQVLMZ8Jr28bFdtqdt++BxF2uiiPsA3/4a
MXcMmgF6sTLjKwEHOG7DpV4jvEWbe1DByTCP2+UretNb+zNAHqDVmBe8i4fDidNd
oI6yqqr2jmmIBsX6iSHzCJ1pLgkzmykNRg+MzEk0sGlRvfkGzWitZky8PqxhvQqI
DsjfPe58BEydCl5rkdbux+0ojatNh4lz0G6k0B4WixThdkQDf2Os5M1JnMWS9Ksy
oUhbAgMBAAGjgbkwgbYwCwYDVR0PBAQDAgHGMA8GA1UdEwEB/wQFMAMBAf8wHQYD
VR0OBBYEFKFyXyYbKJhDlV0HN9WFlp1L0sNFMEQGA1UdHwQ9MDswOaA3oDWGM2h0
dHA6Ly9jcmwudXNlcnRydXN0LmNvbS9VVE4tVVNFUkZpcnN0LUhhcmR3YXJlLmNy
bDAxBgNVHSUEKjAoBggrBgEFBQcDAQYIKwYBBQUHAwUGCCsGAQUFBwMGBggrBgEF
BQcDBzANBgkqhkiG9w0BAQUFAAOCAQEARxkP3nTGmZev/K0oXnWO6y1n7k57K9cM
//bey1WiCuFMVGWTYGufEpytXoMs61quwOQt9ABjHbjAbPLPSbtNk28Gpgoiskli
CE7/yMgUsogWXecB5BKV5UU0s4tpvc+0hY91UZ59Ojg6FEgSxvunOxqNDYJAB+gE
CJChicsZUN/KHAG8HQQZexB2lzvukJDKxA4fFm517zP4029bHpbj4HR3dHuKom4t
3XbWOTCC8KucUvIqx69JXn7HaOWCgchqJ/kniCrVWFCVH/A7HFe7fRQ5YiuayZSS
KqMiDP+JJn1fIytH1xUdqWqeUQ0qUZ6B+dQ7XnASfxAynB67nfhmqA==
-----END CERTIFICATE-----


let me know if it works!!

---

### Post by R.Bucky on 2008-10-03
I successfully installed a Citrix ICA client on my Ubuntu 7.10 box last year. It worked perfectly for acessing my employers Citrix Server. It functioned for MS Office Suite and ArcGIS - no problem
[http://www.citrix.com/English/SS/downloads/details.asp?downloadID=3323&productID=-1](http://www.citrix.com/English/SS/downloads/details.asp?downloadID=3323&productID=-1)

---

### Post by TpyKv on 2008-10-03
sorry didn't see the first page in all this... silly me!

---

### Post by ericesque on 2008-10-06
For those still struggling to get the linux version of the citrix client going, try the Win client in WINE.  It works flawlessly for me.

---

### Post by nanonils on 2008-10-07
(type this in the terminal)

sudo gedit ~/ICAClient/linuxx86/keystore/cacerts/UTN-USERFirst-Hardware.crt

(and paste into it the following lines (including those with BEGIN and END)):

[...]

let me know if it works!![/QUOTE]

So close... Been messing with Ubuntu on and off for about 6 months... Citrix is the only thing preventing me from killing my Vista on my Lenovo T61 to replace it with Intrepid 64bit... Currently, I'm trying this on an old pentium III Compaq Presario that runs very smoothly with Xubuntu 8.10.

When I follow your instructions (replacing gedit with mousepad), I get the error message "can't open file to write" despite the sudo. What to do?

When I run the Citrix server and attempt to connect to this website: [https://cwp.ucsd.edu/Citrix/AccessPlatform/site/default.aspx](https://cwp.ucsd.edu/Citrix/AccessPlatform/site/default.aspx) Citrix Presentation Server is starting but produced the error message: "You have not chose to trust "Thawte Premium Server CA", the issuer of the server's security cerificate (SSL error 61)." WAIT - isn't Thawte what got Shuttlefield his riches? I use firefox 3. 
I suppose the key that you posted is somehow related to that? 

Thanks much!
Nils

---

### Post by nanonils on 2008-10-07
> **ericesque said:**
> For those still struggling to get the linux version of the citrix client going, try the Win client in WINE.  It works flawlessly for me.

It should be called "whine" not "wine". 

When I try getting linux to run via wine I get the following message:

Runtime Error! Program: C:\windows\system32\regsvr32.exe
R6034
An application has made an attempt to load the C runtime library incorrectly.
Please contact the applications support team for more information.

The installation ended prematurely because of an error.

---

### Post by kalkems on 2008-10-10
I have an employee who works for our school part time and for another company part time. She needs to reach her other job online using Citrix. We use LTSP thin client system at our school. Has anyone got Citrix working in LTSP and how did you get this working. We run a 8.04 server system.
/ernie

---

### Post by TVAbuntu on 2008-10-17
I have *almost* got Citrix working, except for the certificates. I followed the posts here as well as the readme that came with the download from Citrix. However when I try to log on I get "the security certificate "xxx.xxxxxx.xxx" could not be validated. (ssl provider code:20, ssl error 86)
I have clicked on the security icon in Firefox and "exported" the certificate and copied to the ~/cacerts folder and renamed the extension .crt, but still no luck.

---

### Post by TVAbuntu on 2008-10-17
addnedum: tried the certificate posted above by TtyPkv, and it worked like a charm (though I have no idea why) Thanks!

---

### Post by TVAbuntu on 2008-10-18
Sorry, misspelt your name: TpyKv
Have now configured on 3 different Ubuntu machines, working great! Thanks again.

---

### Post by iamfuzz on 2008-10-29
FWIW, we are in contact with them and plan to offer it in the Partner Repo at some point in the future, but it may be some time yet due to distribution agreements and such.

-Brian

---

### Post by ThomasMarkas on 2008-10-30
I am a Citrix Client, user using it to allow me to work from home on the odd occasion. More important, it allows me to read my emails before leaving for work.

I am an user of Ubuntu, not a XP box in the house and for various reasons need periodically re-install. Well I will play. I have tried the approaches here, but always have problems with the editing required.

Below are the instruction I follow to install Citrix. all the bit can be found in the HOWTO, but this could be updated/better presented.

1. Download latest client from Citrix website, the rpm one.

2. In a command window, run the following instructions. For USERNAME, enter your own and this was prepared with the latest version of Citirx I downloaded.

cd /home/USERNAME/Desktop
sudo apt-get install libmotif3
sudo apt-get install alien
alien ICAClient-10.6-1.i386.rpm
sudo gdebi-gtk ICAClient-10.6-1.i386.deb


(if asked convert scripts as well).


3. In a File Browser

Dragged the icons from /usr/lib/ICAClient/icons onto the toolbar.

4. Now good to go, just double click on the manager item.


Hope this is of use to someone

---

### Post by ThomasMarkas on 2008-11-08
Thanks to the colleague who pointed out the alien command above should be:-

sudo alien ICAClient-10.6-1.i386.rpm --scripts

---

### Post by mgmiller on 2008-11-09
I had created a howto a few months ago that seems to work well for folks.
Here is a link....[http://ph.ubuntuforums.com/showthread.php?t=891022](http://ph.ubuntuforums.com/showthread.php?t=891022)

---

### Post by 081105jk on 2008-11-16
&#22823;&#27721;[**&#38452;&#33550;&#22686;&#22823;**](http://www.yinjing120.com/)&#22120;&#26159;&#37319;&#29992;&#32654;&#22269;&#22823;&#27721;&#21307;&#30103;&#35774;&#22791;&#26377;&#38480;&#20844;&#21496;&#24378;&#21170;&#25216;&#26415;&#65292;&#30001;&#21271;&#20140;&#24247;&#30334;&#24180;&#21307;&#30103;&#35774;&#22791;&#26377;&#38480;&#20844;&#21496;&#29983;&#20135;&#30340;&#30007;&#24615;&#38452;&#33550;&#22686;&#22823;&#19987;&#29992;&#22120;&#26800;&#12290;&#22823;&#27721;[**&#38452;&#33550;&#22686;&#22823;**](http://www.yinjing120.com/)&#22120;&#22806;&#35266;&#31934;&#32654;&#65292;&#36896;&#22411;&#26102;&#23578;&#65292;&#20351;&#29992;&#33298;&#36866;&#12290;&#23427;&#26681;&#25454;&#20154;&#20307;&#24037;&#31243;&#21407;&#29702;&#35774;&#35745;&#30340;&#65292;&#20855;&#26377;&#35843;&#33410;&#21151;&#33021;&#65292;&#22312;&#20351;&#29992;&#26102;&#21487;&#20197;&#26681;&#25454;&#33258;&#36523;&#24773;&#20917;&#35843;&#25972;&#38452;&#33550;&#23610;&#23544;&#21644;&#21147;&#24230;&#65292;&#20351;&#29992;&#38750;&#24120;&#23433;&#20840;&#65292;&#38750;&#24120;&#33298;&#36866;&#12290;&#22823;&#27721;[**&#38452;&#33550;&#22686;&#31895;**](http://www.yinjing120.com/yinjingzengcu.html)&#22120;&#26368;&#22823;&#29305;&#28857;&#26159;&#19981;&#20250;&#25439;&#20260;&#38452;&#33550;&#20307;&#65292;&#20329;&#25140;&#33298;&#36866;&#26080;&#30171;&#33510;&#65292;&#23433;&#20840;&#39640;&#25928;&#12290;&#21516;&#26102;&#20351;&#29992;&#21518;&#20063;&#21313;&#20998;&#26041;&#20415;&#20174;&#38452;&#33550;&#20307;&#21368;&#19979;&#65292;&#22312;&#25972;&#20010;&#25110;&#38388;&#26029;&#20351;&#29992;&#36807;&#31243;&#20013;&#65292;&#20202;&#22120;&#21313;&#20998;&#22362;&#22266;&#32780;&#19988;&#23481;&#26131;&#28165;&#27927;&#12290;      &#22823;&#27721;[**&#38452;&#33550;&#22686;&#31895;**](http://www.yinjing120.com/yinjingzengcu.html)&#32463;&#36807;&#22810;&#24180;&#20020;&#24202;&#35797;&#39564;&#65292;&#24471;&#21040;&#20102;&#21307;&#23398;&#30028;&#30340;&#39030;&#21147;&#25903;&#25345;&#21644;&#20840;&#29699;&#26080;&#25968;&#28040;&#36153;&#32773;&#20449;&#36182;&#65292;&#22823;&#27721;&#38452;&#33550;&#22686;&#22823;&#22120;&#21487;&#20197;&#22312;&#30701;&#26102;&#38388;&#20869;&#24110;&#21161;&#24744;&#23454;&#29616;&#27704;&#20037;&#30340;&#29289;&#29702;&#24615;&#38452;&#33550;&#22686;&#22823;&#12289;&#22686;&#31895;&#65292;&#20351;[**&#38452;&#33550;&#24310;&#38271;**](http://www.yinjing120.com/yinjingyanchang.html)&#65292;&#24182;&#19988;&#33021;&#22815;&#24443;&#24213;&#25913;&#21892;&#38452;&#33550;&#21151;&#33021;&#22833;&#35843;&#21644;&#38452;&#33550;&#24367;&#26354;&#12290;&#22823;&#27721;&#38452;&#33550;&#22686;&#22823;&#22120;&#35753;&#24744;&#30340;&#38452;&#33550;&#23610;&#23544;&#12289;&#21187;&#36215;&#30828;&#24230;&#12289;&#24615;&#24555;&#24863;&#12289;&#30007;&#24615;&#39749;&#21147;&#12289;&#30007;&#24615;&#26426;&#33021;&#21516;&#26102;&#24471;&#21040;&#20840;&#38754;&#25552;&#21319;&#65292;&#26356;&#37325;&#35201;&#30340;&#26159;&#32473;&#29983;&#27963;&#21697;&#36136;&#24102;&#26469;&#36136;&#30340;&#39134;&#36291;&#65292;&#35753;&#26080;&#25968;&#22827;&#22971;&#20805;&#20998;&#20139;&#21463;&#24615;&#29983;&#27963;&#24102;&#26469;&#30340;&#20048;&#36259;&#12290;&#38452;&#33550;&#22686;&#22823;&#22120;&#21151;&#33021;&#21407;&#29702;      &#22823;&#27721;&#38452;&#33550;&#22686;&#22823;&#22120;&#30340;&#32467;&#26500;&#22522;&#20110;&#25289;&#20280;&#30340;&#21407;&#29702;

---

### Post by mma8x on 2008-11-16
is this method only valid for 32 bit installs?  i tried a method for 64 bits mentioned here: [http://ubuntuforums.org/showthread.php?t=39556](http://ubuntuforums.org/showthread.php?t=39556)
this allowed me to install (and open) the client.  however, when trying to go through my work's web site, when i click on an app, i get the message "sorry.  this functionality is not supported with your browser".  not really sure how to proceed here.

---

### Post by mac-i-bear on 2008-11-18
ThomasMarkas,

I followed your instructions and got almost there...
citrix starts and attempts to connect then just seats there
nubie to all this universe with no luck
how do i uninstall what i have done
glad did not give my xp box away
thanks for your help

---

### Post by watsbe on 2008-11-21
I haven't been able to use the Citrix native client since Gutsy.  Interestingly enough, I recently scrapped my firefox profile and suddenly it started running the native client.
Then I noticed a popup message and enabled the popups, and it reverted to the java client.
It looks like the client detection doesn't detect the client on my machine, and it was probably related to an "upgrade" at the Citrix end rather than Ubuntu.
It's not a problem for me because I don't notice any difference between the native and java client anyway.  Just thought it might be useful for someone.

---

### Post by mma8x on 2008-11-21
hmmm.  i didn't realize there was a java client.  i can't find any installation instructions.  i untar and get some .jar files, which i'm not sure what to do with.  certainly, if i can get this working i won't need the native client (hopefully).  btw, i get the same issues when installing on my hardy 32 bit box using firefox 2.

---

### Post by Cheap Webcam on 2008-11-28
[**wholesale cheap 10 Pieces CX400 earphones10 Pieces CX400 earphones**](http://www.agoodic.com/viewproduct.asp?/10_Pieces_CX400.htm), free shipping, the cheap earphones

---

### Post by Andrew Arthur on 2008-12-14
Hi,

Did you upgrade from 6.10 > 7.04?

I am still working with 6.10 and it seems that it is not possible to upgrade.

---

### Post by Sef on 2008-12-14
> Did you upgrade from 6.10 > 7.04?

I am still working with 6.10 and it seems that it is not possible to upgrade.

You can do a clean install if you want to upgrade, it is the best way to upgrade now.   There are no more security updates or patches for 6.10 being produced.  It would be best to upgrade to Hardy Heron - the most recent LTS or to Intrepid Ibex.

---

### Post by mma8x on 2008-12-17
> **Andrew Arthur said:**
> Hi,

Did you upgrade from 6.10 > 7.04?

I am still working with 6.10 and it seems that it is not possible to upgrade.

not sure who that was directed at, but i'm using 8.04 on 1 box and 8.10 on another.

---

### Post by cbahimsa on 2008-12-25
Just got citrix to work on my ubuntu 8.10 intrepid amd64, through firefox. Very sluggish however. My system is dual boot. On vista 64, using ie7 32 and 64, and also minefield, it works lighting fast. Not a bandwidth problem. Any suggestions? Also, I have this icon called citrix presentation server client but it does not seem to do anything when I click it. Thanks.

---

### Post by nanonils on 2009-01-18
Strange - when I recently tried to install Citrix again as native Ubuntu application and not using Wine on my 8.10 with most recent updates it workes like a charm. I followed these instructions: [http://www.emielmolenaar.com/2008/12/installing-the-citrix-presentation-server-client-under-ubuntu-810/](http://www.emielmolenaar.com/2008/12/installing-the-citrix-presentation-server-client-under-ubuntu-810/)

I think I was better able to locate the directory for the security key. It might not have been in the right place.

Now my next challenge as a noob will be to figure out how to setup a home network... our 3 laptops and 1 desktop all run Ubuntu but don't allow network gaming yet.

---

### Post by Sef on 2009-01-18
> Now my next challenge as a noob will be to figure out how to setup a home network... our 3 laptops and 1 desktop all run Ubuntu but don't allow network gaming yet.

You can use NFS.   Please post any question about networking in the Networking and Wireless forum.  It is under Main Support Categories.

---

### Post by jcarloscamargo on 2009-02-03
Hi,

We've been working with Citrix for years using Windows and now planning to have some of our workstations moved to Linux. I've tried the ica client v10 and it works ..er...fine. Some "but"'s:

1. As I think it's been previously pointed out in this thread,  you'll find problems if you use compiz and activate desktop effects. Windows resizing and positioning will drive you crazy in seconds.

2.- There's no spanish version.
3.- You'll need cups installed and printcap activated if you want to manage your session printers properly.

4.- The client is outdated (2007) and it seems it will remain so.

On the other hand you can also use the Java client for Citrix. Latest version is 9.6, in spanish as well, and dated 2008. You wont need to install anything else but your browser and a java runtime. Well, use Sun's, openjdk or recent flavors are out of the question. 

Now the problem , BIG problem, with the java option: It doesnt work with Firefox in Ubuntu when running applications in seamless windows. The first one you run goes smoothly, the second one will crash them all.

Any other combination (either using Opera+Ubuntu or using Fedora+Firefox, Windows+Firefox) works properly. I'm still digging the causes, no success so far. Anyone sharing the same issue?

Regards!

---

### Post by tuxusa on 2009-02-04
I hope this is an easy problem because I need Citrix to remote into my company. I have tried the the how to linked here and other configurations that I have found on the forum but I still get the same error. This is the latest install I tried [https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)                                                                            No matter what what I try I get this message "You have not chosen to trust "DigiCert Global CA", the issuer if the server's security certificate (SSL error 61)."

---

### Post by ebeyer on 2009-06-09
> **TVAbuntu said:**
> I have *almost* got Citrix working, except for the certificates. I followed the posts here as well as the readme that came with the download from Citrix. However when I try to log on I get "the security certificate "xxx.xxxxxx.xxx" could not be validated. (ssl provider code:20, ssl error 86)
I have clicked on the security icon in Firefox and "exported" the certificate and copied to the ~/cacerts folder and renamed the extension .crt, but still no luck.

I'm getting this exact same error.  I'm using the security certificate sent to me by our corporate IT guy (X.cer for the purpose of this post), which I put in my /keystore/cacerts folder which is giving me this error.

Please help! I have no experience or skill with IT security or Citrix and am barely literate on Ubuntu.

Solving this problem would make my work life enormously easier.  Thanks in advance.

---

### Post by TVAbuntu on 2009-06-10
sorry if you tried this, but

sudo gedit ~/ICAClient/linuxx86/keystore/cacerts/*yoursecuritycert*.crt
 
then paste in the entire certificate, and save, including headers and footers

---

### Post by mojohn on 2009-07-26
Hello. I am running Jaunty on my Dell Inspiron 1420 and am having great difficulty getting the Citrix client up and running. I followed rahmath's instructions on page 1 of this thread. 

I'm trying to connect to my employer's web site and the employer uses a Go Daddy certificate. I've tried downloading certificate from the Go Daddy web site, as well as exporting it from Firefox. 

I was able to connect after uninstalling and reinstalling the Citrix client, placing the certificate in /usr/lib/ICAClient/keystore/cacerts. However, after shutting down the laptop (both hard shutdown and reboot as well as hybernate and wake), I am no longer able to connect without the "you have chosen not to trust" error popping up, even if I uninstall and reinstall the client and save the certificate in cacerts.

This is about to drive me crazy. Any help you can provide will be much appreciated!

Thanks, mojohn

---

### Post by TpyKv on 2009-07-27
I have a feeling you are editing/creating the certificate as a normal user, and not using sudo?


sudo gedit (whereever this file is)

?



> **mojohn said:**
> Hello. I am running Jaunty on my Dell Inspiron 1420 and am having great difficulty getting the Citrix client up and running. I followed rahmath's instructions on page 1 of this thread. 

I'm trying to connect to my employer's web site and the employer uses a Go Daddy certificate. I've tried downloading certificate from the Go Daddy web site, as well as exporting it from Firefox. 

I was able to connect after uninstalling and reinstalling the Citrix client, placing the certificate in /usr/lib/ICAClient/keystore/cacerts. However, after shutting down the laptop (both hard shutdown and reboot as well as hybernate and wake), I am no longer able to connect without the "you have chosen not to trust" error popping up, even if I uninstall and reinstall the client and save the certificate in cacerts.

This is about to drive me crazy. Any help you can provide will be much appreciated!

Thanks, mojohn

---

### Post by dingo dog on 2010-04-23
what would i put down if i need the go daddy cert? thanks in advance

---

### Post by brion@cbkidder.com on 2010-04-23
disregard

---

### Post by dingo dog on 2010-04-23
i had a problem a few months back with thwates root cert. ok till this morning. now it says GO DADDY cert required. Can anyone tell me how I get the cert which I have saved on the desktop to the lib/ICAclient/keystore/cacerts? From memory I had the same problem last time as I am a different user from the ROOT user? I see the godaddy .crt but I can't cut & paste to the appropriate file. Thanks in advance

---

### Post by brion@cbkidder.com on 2010-04-24
This may help in getting the godaddy cert:

In Terminal type:

sudo wget [https://certs.godaddy.com/repository/gd-class2-root.crt](https://certs.godaddy.com/repository/gd-class2-root.crt)

Find the file downloaded and copy it to the target directory.

---

### Post by dingo dog on 2010-04-24
Thanks for your help, Got it!!

---

### Post by dhoenisch on 2010-06-02
I've tried the steps for the GoDaddy certificate for Citrix, but I am still receiving the following error message:

You have not chosen to trust "Go Daddy Secure Certification Authority", the issuer of the server's security certificate (SSL error 61).

Any other ideas?  I am completely stumped.

Thanks,
Dan

---

### Post by pigphish on 2010-06-16
try this (from [http://geekpete.com/blog/tech-guides/linux-citrix-client-error-61-ubuntu-810-intrepid-ibex](http://geekpete.com/blog/tech-guides/linux-citrix-client-error-61-ubuntu-810-intrepid-ibex))

basically uses mozilla's certificates which should already have all that you need. 

mv /usr/lib/ICAClient/keystore/cacerts /usr/lib/ICAClient/keystore/cacerts_old
cp /usr/lib/ICAClient/keystore/cacerts_old/* /usr/share/ca-certificates/mozilla/
ln -s /usr/share/ca-certificates/mozilla /usr/lib/ICAClient/keystore/cacerts

Also note I installed the deb package from cytrix and installed the motif-clients.
[http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755#top](http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755#top)

Hope this helps. 

- George

---

### Post by 98cwitr on 2010-06-16
my CC is working great on 10.04 minus the fact that the mouse pointer is about 10-15 pixels off it's click point. I have to use the bottom of the pointer instead of the top :?

---

### Post by uzersk on 2010-06-26
> **pigphish said:**
> try this (from [http://geekpete.com/blog/tech-guides/linux-citrix-client-error-61-ubuntu-810-intrepid-ibex](http://geekpete.com/blog/tech-guides/linux-citrix-client-error-61-ubuntu-810-intrepid-ibex))

basically uses mozilla's certificates which should already have all that you need. 

mv /usr/lib/ICAClient/keystore/cacerts /usr/lib/ICAClient/keystore/cacerts_old
cp /usr/lib/ICAClient/keystore/cacerts_old/* /usr/share/ca-certificates/mozilla/
ln -s /usr/share/ca-certificates/mozilla /usr/lib/ICAClient/keystore/cacerts

Also note I installed the deb package from cytrix and installed the motif-clients.
[http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755#top](http://www.citrix.com/English/ss/downloads/details.asp?downloadId=3323&productId=186&c1=sot2755#top)

Hope this helps. 

- George

Hello.  Thanks for this.  I am trying to figure out how to get rid of the "You do not trust entrust.net certificate" etc. error messages.  Attempting your workaround results in a Permission denied error.  Also what exactly are these commands accomplishing?  Thanks for your help..

Uzer

---

### Post by pigphish on 2010-06-27
> **uzersk said:**
> Hello. Thanks for this. I am trying to figure out how to get rid of the "You do not trust entrust.net certificate" etc. error messages. Attempting your workaround results in a Permission denied error. Also what exactly are these commands accomplishing? Thanks for your help..
 
Uzer
 
 
I am not in front of my own computer so as to not delay the response, just try putting sudo before the commands that are giving you access denied. 
 
Meaning: 
```

sudo mv /usr/lib/ICAClient/keystore/cacerts /usr/lib/ICAClient/keystore/cacerts_old
sudo cp /usr/lib/ICAClient/keystore/cacerts_old/* /usr/share/ca-certificates/mozilla/
sudo ln -s /usr/share/ca-certificates/mozilla /usr/lib/ICAClient/keystore/cacerts

```
 
also fire up the synaptic package manager and make sure the motif-client is installed. 
or try 
```
sudo apt-get install motif-clients
```
 
I am doing this from memory so I may be off on which needs what and proper names.
 
One other quick note the cacerts directory should already exist. Older versions of mozilla had cacert (singular and no "s"). Perhaps your issue is coming from not referencing the correct directory.

---

