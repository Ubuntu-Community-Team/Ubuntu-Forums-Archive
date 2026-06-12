---
title: "Openoffice.org2 Base SCREWY! Please don't make me go back to Microsoft Office!!"
date: 2005-10-28
forum: General Help
---

### Post by robinchew on 2005-10-28
Hi all,

My computer spec summary:
AMD Thunderbird 1.3 Ghz
Nvidia Geforce2 MX

A good OS (Ubuntu) is one that can run on crappy specs (ie. [COLOR="Red"]NOT[/COLOR] winblows!)

I used debian and openoffice.org RC and made an ODB file which of course works fine.
Not long ago I got breezy and very happy about it, EXCEPT it does not run Base properly. I'll list the 2 major problems I have  below:

1. When I open one of the table, it gives me:
[COLOR="Red"]"the date content could not be loaded. No data is available"[/COLOR]

When I click on '**More**' 
It says: 

[COLOR="Red"]SQL Status: S1000
Error code: -35

No data is available[/COLOR]

2. All my dates are showing up as [COLOR="Red"]1 Jan 70[/COLOR] . Even if I create a brand new database, create a table, and try to input Dates, whatever you put in, it will change into [COLOR="Red"]1 Jan 70[/COLOR] right after you finish entering it.

But everything is fine with Windows Openoffice.org2, All dates shows up fine and all tables open. So I'm thinking it is not the prob with the ODB file. I've been googling and getting whole bunch of different older versions of openoffice.org2 (beta, RC). And they still have the same problem. 

Sooooo what's up?? Any solution would be maaaarrvelous! That database contains pretty vital information. And I don't think I wanna take all the trouble to go back to Debian and Ubuntu is much more user-friendly anyway, I like it! Except Base is causing me pain!. 

I've been telling people to convert to Ubuntu, and use Openoffice2 as a waaay better alternative to Microshit Windows and Office!! This Base prob is not making me look good!

Thanks all,
Robin

---

### Post by matthewv on 2005-10-28
I've never used Base, but you could always download the final release of openoffice.org 2 from [http://www.openoffice.org/](http://www.openoffice.org/) . It might fix your problems, it helped when I had some printing problems.

---

### Post by robinchew on 2005-10-28
But those files are all RPMs. Alien don't work for me. Keeps giving me:

[COLOR="Red"] sudo alien *.rpm
Use of uninitialized value in die at /usr/share/perl5/Alien/Package/Deb.pm line 488, <GETPERMS> line 32.
Package build failed. Here's the log:
find: openoffice.org-base-2.0.0: No such file or directory[/COLOR]

I thought theres no proper official release of openoffice.org2 for ubuntu/debian yet

But anyway like i said, I used the older openoffice2 RC/beta on debian before and it worked fine. So there should be no reason why this openoffice2 provided by ubuntu breezy has this problem. Strange!

Thanks for replying,
Robin

---

### Post by angrykeyboarder on 2005-10-28
[quote=robinchew]But those files are all RPMs. Alien don't work for me. Keeps giving me:

[COLOR=Red] sudo alien *.rpm
Use of uninitialized value in die at /usr/share/perl5/Alien/Package/Deb.pm line 488, <GETPERMS> line 32.
Package build failed. Here's the log:
find: openoffice.org-base-2.0.0: No such file or directory[/COLOR]

I thought theres no proper official release of openoffice.org2 for ubuntu/debian yet

But anyway like i said, I used the older openoffice2 RC/beta on debian before and it worked fine. So there should be no reason why this opoenoffice2 provided by ubuntu breezy has this problem. Strange!

Thanks for replying,
Robin[/quote]

I sure hope somebody comes through before too long on that.  A recent update to Fedora Core 4 included OOo 2.0, official.

It would seem to me that it should be showing up in Debian Sid any time now..

---

### Post by robinchew on 2005-10-28
I'll be an angry-dvorak-keyboarder too if I don't get this working soon! I really looked forward to playing more with base. Disappointing! :(

---

### Post by ofek on 2005-10-28
I still think u should try the final version.
u can try [this]("http://www.ubuntuforums.org/showthread.php?t=80392") ubuntu howto for installin easly with .deb package.

---

### Post by robinchew on 2005-10-28
cool thanks ofek!
I shall see if it works
but i dunno I've been to many HOWTO install openoffice.org2 forums.
many don't really work for me
especially the ones where they say use alien to convert RPMs to DEB. Bloody don't work!! See the error I mentioned above in post #3

Ill try this source though deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./
Ill do that later
Right now, ubuntu is upgrading my openoffice2 or adding ANOTHER one, I dont know!!

---

### Post by robinchew on 2005-10-28
NOPE not working!

It just says [COLOR="Blue"]openoffice.org2 is already the newest version.[/COLOR]
Blooooddyyy heeelll! Damn man!

I'm thinking of reformatting the comp man, but I've already done that 3 times.

But this is BS! Why is this problem only happening to me!! I am like the only one in the world with this lame ass problem. Now 'writer' is givin me some weird activity!

I wanna try the 'alien' way now, but someone gotta help me solve that problem too in post #3

Heeeellp! I don't want to go back to windoze! I cant afford Macs either! Debian is too overloaded with stuff I don't use!

I'm thinking, it's probably not the version problem, ubuntu is already automatically ensuring that I get the newest version. So anybody know people from Ubuntu or Openoffice? OR someone really really really smart?

Anyway good day,
Robin

---

### Post by Velvet Elvis on 2005-10-28
FYI:

[http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

This is a shot in the dark, but you might want to try downloading the blackdown JRE and setting OO to use it.

---

### Post by ofek on 2005-10-28
Have u tried the repository from my howto? if u did and it told u u got the newest ver, u probably do have it.
I would offer u to try to reinstall oo, but u probably tried that and if u didn't chanses it won't help.
You can try crossoffice and microsoft office, although i won't say working with windows programs on linux is realy clean.
anyways don't give up, it's not a problem worth leaving linux for.
oh and u can always dual-boot with windows microsoft for ur office work :D .

---

### Post by robinchew on 2005-10-28
hey ofek,
I've been uninstalling and installing more than 6 versions of openoffice2 from many sources to solve the problem but all in vain. 
Right now I am doing:
[COLOR=Blue]wget [http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/RC3/OOo_OOO680_m3_LinuxIntel_install_en-GB_deb.tar.gz](http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/RC3/OOo_OOO680_m3_LinuxIntel_install_en-GB_deb.tar.gz)[/COLOR]
after i [COLOR=Blue]tar -xf[/COLOR] and [COLOR=Blue]dpkg -i[/COLOR] it , it probably won't work still. But maybe something will happen.

This forum automatically adds the [url] tags to site URLs, like above. anyway to get rid of that? Not important, fixing my base is important

Using anything microshit is OUT OF THE QUESTION! my hate for them is eternal.
But go HALO!

hey elvis,
Ill try the blackdown JRE, although I've already installed sun-j2re1.5_1.5.0+update05_i386 .
Can you explain more about it and how to get OO to use it?

Thanks all for the attempting help,
Robin

---

### Post by robinchew on 2005-10-28
I'll summarize the problem here again in case new people come in:
-----------------------------------------------------------------------
1. When I open one of the table, it gives me:
"the date content could not be loaded. No data is available"

When I click on 'More'
It says:

SQL Status: S1000
Error code: -35

No data is available

2. All my dates are showing up as 1 Jan 70 . Even if I create a brand new database, create a table, and try to input Dates, whatever you put in, it will change into 1 Jan 70 right after you finish entering it.
------------------------------------------------------------------------------------------------------------
Problem ONLY appears in Ubuntu Version of Openoffice.org2
Problem is probably not to do with OO versions, it is ubuntu (well MY ubuntu) specific or 'openoffice2 only in ubuntu' specific

Hey when i do [color="blue"]dpkg -r -P open*[/color]
it gives me [color="red"]Options marked [*] produce a lot of output - pipe it through `less' or `more' ![/color]
I don't get it. Where do I put the 'less' or 'more'?

---

### Post by robinchew on 2005-10-28
when I do  sudo dpkg -l openoff*

it comes up with:
[color="#999999"]
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
pn  openoffice-sna <none>         (no description available)
un  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
un  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
un  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
un  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
rc  openoffice.org 1.9.76-0ubuntu Debian specific parts of OpenOffice.org
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
un  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
un  openoffice.org <none>         (no description available)
rc  openoffice.org 1.9.129-0.1ubu English_british language package for OpenOff
pn  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
un  openoffice.org <none>         (no description available)
pn  openoffice.org <none>         (no description available)
[/color]
How do I DESTROY them all??

[color="blue"]sudo dpkg -r openoff*[/color] doesnt work
it gives [color="red"]dpkg - warning: ignoring request to remove openoff* which isn't installed.[/color]


Thanks all,
Robin

---

### Post by robinchew on 2005-10-29
Hi there,

I want to re-install my breezy without booting from the ubuntu disk, reformat the harddrive again, blah blah. I just want to do the step right after the CD setup where you don't need the CD anymore. I wanna use a freshly installed ubuntu again.

But I don't really want to do it again, because I fluked getting my nvidia geforce2 card to work. 

It is because of my problem here with openoffice.org2 base
[http://www.ubuntuforums.org/showthread.php?t=83224](http://www.ubuntuforums.org/showthread.php?t=83224)

If you could visit that thread and help me solve the prob, then I don't need to reformat again for the 4th time.
I think even if I reformat again, the problem will still be there anyway.

Thanks a lot,
Robin

---

### Post by aysiu on 2005-10-29
As far as I know, there's no way to reinstall without reformatting and using a CD (or some kind of CD substitute)... that's the very nature of reinstallation.

---

### Post by matthewv on 2005-10-29
And I don't see a reinstall fixing the problem at all. The problem with alien is strange, never happened with me

---

### Post by rykel on 2005-10-29
[QUOTE=robinchew]But those files are all RPMs. Alien don't work for me.[/QUOTE]

This is just another more reason why we Linux users MUST, I emphasise - MUST!, champion for an [***OpenOffice.org autopackage***]("http://www.openoffice.org/issues/show_bug.cgi?id=46333")!

Way toooo many people are _frustrated_ with Linux simply because they cannot install the programs they would love to use (what's the point of freedom/free software if it is f***king difficult to just install it?) and programmers have this, "Hey look, if I gave you the source code, why should I worry about the installer?" while the distro devs said, "Look, you should WAIT for your every latest app 'from us' ~ or jolly well compile it yourself!"     :( 

**Please support [Autopackage]("http://www.autopackage.org")!!!**

---

### Post by robinchew on 2005-10-29
Thank you all for your inputs.

But am I the only one with the base problem??
I could easily install it, only base don't work properly, and maybe other OO apps.
It can't be the package that has the problem right? I mean you all have NO PROBLEM whatsoever with OO right?

Blah, gotta go now, write more later.

Robin

---

### Post by robinchew on 2005-10-30
Finally found a SOLUTION!!!
So if anybody have this kinda prob (which doesnt seem like anyone), solution is here:
[http://www.oooforum.org/forum/viewtopic.phtml?p=102363#102363](http://www.oooforum.org/forum/viewtopic.phtml?p=102363#102363)

Now I can FULLY enjoy Ubuntu!!

Good day all,
Robin

---

### Post by NewbieNik on 2005-10-30
If you've done this I apologise, but have you tried removing OOo then reinstalling it?
It could be an error on the install as mine seems to work fine as a standard Breezy install! (ver 1.9.129)

---

### Post by eternal0void on 2005-10-30
[QUOTE=robinchew]hey elvis,
Ill try the blackdown JRE, although I've already installed sun-j2re1.5_1.5.0+update05_i386 .
Can you explain more about it and how to get OO to use it?[/QUOTE]
I went into the bin folder inside the directory I installed java into (I used a default /usr/java/jre1.5.0 for the install directory) and made symlinks to every executable fitting "java*" (I think it was java, javaws and javavm, or something like that) in the /usr/bin directory.

Of course, I did that before installing OpenOffice.org, and it found the Java install during the OpenOffice.org install.  Not sure how to make a current install of OpenOffice.org see a newly-installed and symlinked JRE.

---

### Post by robinchew on 2005-10-31
it's strange for me, i've re-installed numerous times already, downloading over 5 versions as well, but did not work.

But anyway the solution is above and the problem is with java.

All good,
Robin

---

### Post by Benchrest on 2005-11-02
I see a resolution here but not sure for which or all problems described. I have just started testing base and have found the date problem. Any date I enter gets changed to 01/01/1970. I'm trying to use the very basic hsql included with base rather than the optional choices.

---

### Post by david_finlayson on 2005-11-02
[QUOTE=Benchrest]I see a resolution here but not sure for which or all problems described. I have just started testing base and have found the date problem. Any date I enter gets changed to 01/01/1970. I'm trying to use the very basic hsql included with base rather than the optional choices.[/QUOTE]

I found for my purposes using sqlite was a better replacement for Access than Base. It requires that you know a little SQL, but that isn't too hard to pick up. Otherwise, it is simple to use, cross-plaform and powerful (very large databases possible, faster than MySQL for some types of work). Easy to automate with a little scripting.

David

---

### Post by robinchew on 2005-11-03
The Solution is below.

First you need Sun Java Runtime Environment

[COLOR="Blue"]wget [http://davyd.ucc.asn.au/projects/misc/sun-j2sdk1.5_1.5.0_i386.deb](http://davyd.ucc.asn.au/projects/misc/sun-j2sdk1.5_1.5.0_i386.deb)
apt-get install java-package (may not work, if not, then use source.list below temporarily)
apt-get install fakeroot
fakeroot make-jpkg jre-1_5_0_05-linux-i586.bin
dpkg -i sun-j2re1.5_1.5.0+update05_i386.deb[/COLOR]

sources.list :
```
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse
```


then to fix the prob with OO:
[COLOR="Blue"]tools > options > openoffice.org > java[/COLOR]
Then I click on '[COLOR="Blue"]ADD[/COLOR]' then select the path of the JRE which mine is located in [COLOR="Blue"]/usr/lib/j2re1.5-sun/bin[/COLOR]

All problems fixed!
Enjoy Base!! Because Microsoft Access SUCKS!!!
Tell me if my instructions are not clear enough.

Robin

---

### Post by jeremy on 2005-11-03
You may also need to do:
sudo update-alternatives --config java
and select the sun one.

---

### Post by robinchew on 2005-11-03
That sounds good too Jeremy.
I'm just wondering what is this 'alternative' if anybody care to answer?

Thanks,
Robin

---

### Post by frankieus on 2008-02-10
I was reading this thread since I had the same problem, so when you said that it would work in windows then I realised what the problem was.

You have to change the JAVA engine in OO, I installed the latest from SUN and now it works with no problem. ;-)

---

