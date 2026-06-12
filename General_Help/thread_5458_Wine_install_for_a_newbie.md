---
title: "Wine install for a newbie"
date: 2004-11-18
forum: General Help
---

### Post by fotogogo on 2004-11-18
I was lookin' to install either Wine or Bochs (if either is better than the other), and i basically just need step by step instructions.
Aside from keyboard/mouse/right click/left click/double click, please don't assume i know anything (i basically don't as far as Linux goes).
the more dumbed down the instructions the better

thanks a lot.

---

### Post by jdodson on 2004-11-18
[QUOTE=fotogogo]I was lookin' to install either Wine or Bochs (if either is better than the other), and i basically just need step by step instructions.
Aside from keyboard/mouse/right click/left click/double click, please don't assume i know anything (i basically don't as far as Linux goes).
the more dumbed down the instructions the better

thanks a lot.[/QUOTE]

ok, open a command prompt or a terminal window:

install wine and winesetuptk(to configure wine)
```
sudo apt-get update
sudo apt-get install wine
sudo apt-get install winesetuptk
``` 

now lets configure stuff so type:

```
winesetuptk
``` 

click ok to everything, the defaults are fine.  

if all goes well, boom, wine should be rockin on your system.  if you have any questions, feel free.

---

### Post by jdong on 2004-11-18
first, make sure you've added **universe** repositories. Read the Howto forum for more details on that.

---

### Post by R3Mo on 2005-02-25
Hi everyone,

i'm using ubuntu for a month now, and I managed to install some programs myself, so I understand the basic commands.

But when I type exactly the lines above,
so 'apt-get update' -> 'apt-get install wine' I get the following error;
```

Pakket wine is niet beschikbaar, hoewel er naar verwezen wordt door
een ander pakket. Mogelijk betekent dit dat het pakket ontbreekt,
verouderd is, of enkel beschikbaar van een andere bron
E: Pakket wine heeft geen installeerbare kandidaat
```

I'm from holland, so the translation will be:
The Wine package is not availble, it seems though that another package was meant. Possible the package is missing, outdated or is just availble from another source.

I'm sorry for my bad technical english, but i hope someone does understand my problem

Thanks in advance

Remo,
The Netherlands

---

### Post by R3Mo on 2005-02-25
I'm sorry for the reply

I found a good howto at [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb), and managed to install Wine :)

Thanks,
Remo

---

### Post by biggaloo on 2005-02-27
I oficially feel like "that guy": :roll: 
after bailing (tentatively) on attempting a dual partition Ubuntu / XP in favor of wine, I followed the above directions and, when typing "winesetuptk", get:

bash: winesetuptk: command not found

any ideas? (I tried same as root (sudo) and no dice...)
 
Thanks!
-that guy ](*,)

---

### Post by spiritraveller on 2005-02-27
Wine is a major pain in the a##.  The only thing I have been able to get to run reliably is WordViewer97 (for checking Word documents that OpenOffice has created).

New versions of Wine frequently will break compatibility with Windows applications that worked in last month's release.  It's a very difficult technology, even for someone who has been trying it for years.

Even the commercial versions of Wine that I have tried (Crossover, Cedega) are not completely reliable.

I think QEMU is a much better option.  QEMU is slower than Wine, because it virtualizes an entire PC that's running Windows.  However, it is faster than Bochs (unbearably slow).  Bochs emulates the entire system and CPU, whereas QEMU is able to more closely interface some of the hardware to the virtual machine.

The two drawbacks to using QEMU instead of Wine are speed and the need for a Windows license.  Because QEMU pretends to be another PC, it requires that you install Windows onto a virtual harddisk first.

It is slower than Wine... but it's not unbearably slow.  Do not even consider using Bochs.  It is incredibly insanely slow, and you will die of old age before you get anything useful done with it.

The advantage to QEMU is that once you have Windows installed to your virtual hard drive, it is pretty reliable and works well.  If you have a reasonably modern computer (over 1 ghz) with ample memory (at least 256-512 megs) you should be alright.

[QEMU](http://fabrice.bellard.free.fr/qemu/) is available via apt-get.  There is a new kernel module that makes it somewhat faster, but to use that you have to download the QEMU CVS sources and compile them... if you are feeling adventurous, you might try that, but the version in apt is good enough.

---

### Post by R3Mo on 2005-02-28
[QUOTE=biggaloo]I oficially feel like "that guy": :roll: 
after bailing (tentatively) on attempting a dual partition Ubuntu / XP in favor of wine, I followed the above directions and, when typing "winesetuptk", get:

bash: winesetuptk: command not found

any ideas? (I tried same as root (sudo) and no dice...)
 
Thanks!
-that guy ](*,)[/QUOTE]

Did you try it using Synaptic? (see the link in my previous post)
When I added the new packetsource of Wine to Synaptic everything worked fine, it updates the list and includes Wine.

R3Mo

---

### Post by Dragonfly_X on 2005-03-03
[QUOTE=R3Mo]I'm sorry for the reply

I found a good howto at [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb), and managed to install Wine :)

Thanks,
Remo[/QUOTE]
I followed the instructions on the howto page, but i'm unable to save changes i made in the nano editor. The message i get says "Could not open file for writing: No such file or directory"  :confused:

---

### Post by Dragonfly_X on 2005-03-03
the sources.list file doesn't have write permisions so how do i change the contents of that file?

---

### Post by R3Mo on 2005-03-07
You could do it with chown (CHange OWNer) I think...

remo@r3mo:~ $ sudo -u root -s
root@r3mo:~ chown r3mo /etc/apt/sources.list

Did you try to complete the whole installation as root user?

R3Mo

---

### Post by gw90se on 2005-03-07
[QUOTE=biggaloo]I oficially feel like "that guy": :roll: 
after bailing (tentatively) on attempting a dual partition Ubuntu / XP in favor of wine, I followed the above directions and, when typing "winesetuptk", get:

bash: winesetuptk: command not found

any ideas? (I tried same as root (sudo) and no dice...)
 
Thanks!
-that guy ](*,)[/QUOTE]
 I had the same message, but then I just entered 

$ winesetup

(no tk on the end} and the set screen came right up.

---

### Post by acascianelli on 2005-03-07
do a 'find / -name winesetuptk -print'

---

### Post by Dragonfly_X on 2005-03-08
[QUOTE=R3Mo]You could do it with chown (CHange OWNer) I think...

remo@r3mo:~ $ sudo -u root -s
root@r3mo:~ chown r3mo /etc/apt/sources.list

Did you try to complete the whole installation as root user?

R3Mo[/QUOTE]

I've got it sorted! I used: $ chmod 777 ./souces.list \\:D/

---

### Post by acascianelli on 2005-03-08
[QUOTE=jdong]first, make sure you've added **universe** repositories. Read the Howto forum for more details on that.[/QUOTE]

i have the universe repositories enabled and i cannot find wine in them.

---

### Post by goedson on 2005-03-08
[QUOTE=biggaloo]I oficially feel like "that guy": :roll: 
after bailing (tentatively) on attempting a dual partition Ubuntu / XP in favor of wine, I followed the above directions and, when typing "winesetuptk", get:

bash: winesetuptk: command not found

any ideas? (I tried same as root (sudo) and no dice...)
 
Thanks!
-that guy ](*,)[/QUOTE]

winesetuptk is in a separate package named winesetuptk, not in the wine package.

---

### Post by goedson on 2005-03-08
[QUOTE=Dragonfly_X]the sources.list file doesn't have write permisions so how do i change the contents of that file?[/QUOTE]

You should do:

sudo nano /etc/apt/sources.list

You'll be editing the file with root permissions. Then you'll be able to save your changes.

---

### Post by nbell on 2005-04-03
[QUOTE=jdodson]ok, open a command prompt or a terminal window:

install wine and winesetuptk(to configure wine)
```
sudo apt-get update
sudo apt-get install wine
sudo apt-get install winesetuptk
``` 

now lets configure stuff so type:

```
winesetuptk
``` 

click ok to everything, the defaults are fine.  

if all goes well, boom, wine should be rockin on your system.  if you have any questions, feel free.[/QUOTE]
 jdodson:  I'm following your instructions on installing wine and it works fine... I have another problem though.  Before installing unbuntu I did a live test of kunbuntu and in that environment I could see my windows data files on my FAT32 partition.  The reason I chose Unbuntu over Kunbuntu is because Unbuntu found my wireless setup with no problem and I could never get Kunbuntu to do that.. 

However, now that I am in the Unbuntu environment, I can't see my fat32 drive.  I know that the spreadsheet function in Unbuntu will allow me to continue to work on data files that were originally created in the XP SP2 environment such as Excel files and word files etc.. however.. that capability doesn't do me any good when I can't see that partition on my drive.. 

Can someone help?

Sorry if this is a redundant question.. 

Cheers Mate,

The Oowf

---

### Post by salah on 2005-04-03
this what i got  

salah@zreiq:~$ sudo apt-get install winesetuptk
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  winesetuptk
0 upgraded, 1 newly installed, 0 to remove and 33 not upgraded.
Need to get 840kB of archives.
After unpacking 4219kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe winesetuptk 0.7-1.1 [840kB]
Fetched 840kB in 1s (527kB/s)

Preconfiguring packages ...
Selecting previously deselected package winesetuptk.
(Reading database ... 104035 files and directories currently installed.)
Unpacking winesetuptk (from .../winesetuptk_0.7-1.1_i386.deb) ...
Setting up winesetuptk (0.7-1.1) ...
salah@zreiq:~$ winesetuptk
bash: winesetuptk: command not found
ANY help

---

### Post by az on 2005-04-03
One you install winesetuptk, the command is winesetup.

dpkg -K winesetuptk.




WINESETUPTK IS DEPRECIATED!  You should use winetools.

[http://winehq.com/site/download-deb](http://winehq.com/site/download-deb)

---

### Post by Magitec on 2007-09-29
jdodson,

I'm as experienced as the topicstarter here, I guess. I tried to install Wine before using the installation instructions on [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb), but ended up getting messages that the source location could not be reached.

Now I seem to be left with an incomplete install, because "sudo apt-get update" ends at 99% telling me that there's a problem with "wine.budgetdedicated.com" and I should run the command again, ad infinitum. ><

I realise this might be a different topic altogether, but I've drawn a blank so far on this particular install problem.

---

### Post by trendsettr on 2007-12-17
Type "sudo gedit /etc/apt/sources.list" to edit the sources.list file.

---

### Post by trendsettr on 2007-12-17
> **biggaloo said:**
> I oficially feel like "that guy": :roll: 
after bailing (tentatively) on attempting a dual partition Ubuntu / XP in favor of wine, I followed the above directions and, when typing "winesetuptk", get:

bash: winesetuptk: command not found

any ideas? (I tried same as root (sudo) and no dice...)
 
Thanks!
-that guy ](*,)

I got the same error, but i found that if you go to "Applications->Wine->Configure Wine", then the box will pop up.

---

### Post by kbal on 2008-01-12
i tried to install wine in my system. first i did sudo apt-get install wine. it was successfully completed. then i did  apt-get install winesetuptk,
ehe following appeared.


balaji@balaji-desktop:~$ sudo apt-get install winesetuptk
Reading package lists... Done
Building dependency tree... Done
Package winesetuptk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  wine
E: Package winesetuptk has no installation candidate

what should i do to install wine.

---

### Post by goedson on 2008-01-12
> **kbal said:**
> i tried to install wine in my system. first i did sudo apt-get install wine. it was successfully completed. then i did  apt-get install winesetuptk,
ehe following appeared.


balaji@balaji-desktop:~$ sudo apt-get install winesetuptk
Reading package lists... Done
Building dependency tree... Done
Package winesetuptk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  wine
E: Package winesetuptk has no installation candidate

what should i do to install wine.

You have already installed wine. In the current version, the setup utility is included in the wine package and not on a separate package.

---

