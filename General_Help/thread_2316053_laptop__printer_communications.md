---
title: "laptop / printer communications"
date: 2016-03-04
forum: General Help
---

### Post by krssnda on 2016-03-04
Ihave Ubuntu 14.04 LTS with all of the updates added. My laptop is upto date. I also have Windows 8 loaded in my laptop but I never useit.
Ialso have a Brother #DCP7060D three in one laser printer. It shouldscan, print and photocopy. My problem is that my laptop and printerrefuse to talk to each other.
Thereis no problem with the photocopying function as it works independentof my laptop. When I try to scan my laptop indicates that I have noscanner connected. When I try to print my laptop sees the printerproperly identified but my printer will not accept my commands toprint.
Myprinter works perfectly as a scanner and as a printer when connectedto god awful Windows.
Anysuggestions on how I can get this problem fixed?

---

### Post by him610 on 2016-03-04
Did you install the appropriate Linux drivers for your machine? If not, follow the link...
[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcp7060d_all&os=128]("http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcp7060d_all&os=128")
It is a fairly straight forward procedure. It will work if you do everything correctly in the procedure. I downloaded and installed drivers for my Brother MFC 7360n a couple of years ago. Good luck.

---

### Post by krssnda on 2016-03-04
please excuse me
i am extremely dense when it comes to this puter stuff
to me it all seems to be communicated in klingon
how do i find out if my linux system is rpm or deb

---

### Post by $yl9pAR%t on 2016-03-04
If you have Ubuntu as you have written, you need deb.

---

### Post by krssnda on 2016-03-05
just when i thought it was safe to get back in the water
jaws is back and looking lovingly at my butt
there are four deb packages
[COLOR=#000000][FONT=sans-serif][B][LPR printer driver (deb package)]("http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=dcp7060d_all&os=128&dlid=dlf005479_000&flang=4&type3=559")
[/B][/FONT][/COLOR][COLOR=#000000][FONT=sans-serif][B][CUPSwrapper printer driver (deb package)]("http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=dcp7060d_all&os=128&dlid=dlf005481_000&flang=4&type3=561")
[/B][/FONT][/COLOR][COLOR=#000000][FONT=sans-serif][B][Generic LPR printer driver (deb package)]("http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=dcp7060d_all&os=128&dlid=dlf101123_000&flang=4&type3=10032")
[/B][/FONT][/COLOR][COLOR=#000000][FONT=sans-serif][B][Generic CUPSwrapper printer driver (deb package)]("http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=dcp7060d_all&os=128&dlid=dlf101125_000&flang=4&type3=10033")
again all glingon to me
any suggestions
many thanks for all of your help so far

[/B][/FONT][/COLOR][COLOR=#000000][FONT=sans-serif][B]

[/B][/FONT][/COLOR]

---

### Post by $yl9pAR%t on 2016-03-05
1. Download only Driver Install Tool

2. Go to directory where you downloaded the Driver Install Tool, right click it and choose unzip here (I am not sure if you have such option under right click, I am on Xubuntu now), you should get file linux-brprinter-installer-2.0.0-1

3. Open in terminal your directory where you have your linux-brprinter-installer-2.0.0-1 and run:

```
sudo sh linux-brprinter-installer-2.0.0-1
```

4. You will have to answer a few questions, you should know at this stage what you want, but one important notice from Brother website I wiil give you here:

> [COLOR=#000000][FONT=sans-serif]When you see the message "Will you specify the DeviceURI ?",[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif] For USB Users: Choose N(No)
 For Network Users: Choose Y(Yes) and DeviceURI.[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]The install process may take some time. Please wait until it is complete[/FONT][/COLOR]

edit: [Before you start installation, go to Printers and remove your previously installed printer.]

---

### Post by kurt18947 on 2016-03-05
> **mefisto888 said:**
> 1. Download only Driver Install Tool

2. Go to directory where you downloaded the Driver Install Tool, right click it and choose unzip here (I am not sure if you have such option under right click, I am on Xubuntu now), you should get file linux-brprinter-installer-2.0.0-1

3. Open in terminal your directory where you have your linux-brprinter-installer-2.0.0-1 and run:

```
sudo sh linux-brprinter-installer-2.0.0-1
```

4. You will have to answer a few questions, you should know at this stage what you want, but one important notice from Brother website I wiil give you here:



edit: [Before you start installation, go to Printers and remove your previously installed printer.]

Another tip - be sure you're in an account with SUDO privileges when you download and install. Using the script seems to do a good job of downloading any additional required packages.

---

### Post by krssnda on 2016-03-14
After many manyattempts I have made some progress.
I was able to removethe printer that was specified in my Ubuntu hardware.
There are now noprinters shown.
By the way theprinter that was shown and I deleted was the Brother DCP7060D that Iam trying to connect.
I was able todownload the Brother Driver Install Tool.
I located it inDownloads.
Is Unzip the same asExtract?
Perhaps I unzippedit accidentally without knowing I was doing it because I now have thefile [COLOR=#000000][FONT=Liberation Serif, serif]linux-brprinter-installer-2.0.0-1.[/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif, serif]gzin my Downloads.[/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif, serif]Doesthat look like I am on track?[/FONT][/COLOR]
[FONT=Liberation Serif, serif]Pleaseexplain to me like I am an idiot four year old Step 3 as the Klingonis quite beyond me.[/FONT]
[FONT=Liberation Serif, serif]Manymany thanks![/FONT]
[FONT=Liberation Serif, serif]Kris [/FONT]

---

### Post by kurt18947 on 2016-03-14
> I now have thefile [COLOR=#000000][FONT=Liberation Serif]linux-brprinter-installer-2.0.0-1.[/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif]gzin my Downloads.[/FONT][/COLOR]

You are indeed making progress. gzip(which is what I suspect) is actually a form of zip. Is this in the original user's Download folder? It needs to be because the installer requires sudo privileges.  I would try right-clicking the file and see if 'extract' is one of the options. If so, go ahead and extract it. If the extractor asks for a destination, I've used the Download folder in the past with no issues.  Once the file is extracted, you should be able to open it with a text editor like gedit. It should look something like this:

```
#! /bin/bash
#
# Copyright(c) 2011-2013 Brother Industries, Ltd.  
#    All Rights Reserved.
#
#Brother retains any and all copyrights to the Software. 
#In no case this Agreement shall be construed to assign 
#or otherwise transfer from Brother to User any copyrights 
#or other intellectual property rights to whole or any part 
#of the Software.
#
```

There's much more but if the beginning of the file looks like that you're on the right track. It should have execute permission set. If not, post back and someone will help you with that. Presuming the extracted file is in your Downloads file, open a terminal and type

```

cd Downloads
ls

```

the file 'linux-brprinter-installer-2.0.0-1 should be there. If it is, type

```
sudo bash linux-brprinter-installer-2.0.0-1
```
<enter>

You should be prompted for your sudo user's password. Enter that and the script should start. Enter the machine's model(as with everything linux letter case matters), agree to the licenses and you should be on your way.

---

### Post by Edison_James on 2016-03-14
> **krssnda said:**
> After many manyattempts I have made some progress.
I was able to removethe printer that was specified in my Ubuntu hardware.
There are now noprinters shown.
By the way theprinter that was shown and I deleted was the Brother DCP7060D that Iam trying to connect.
I was able todownload the Brother Driver Install Tool.
I located it inDownloads.
Is Unzip the same asExtract?
Perhaps I unzippedit accidentally without knowing I was doing it because I now have thefile [COLOR=#000000][FONT=Liberation Serif]linux-brprinter-installer-2.0.0-1.[/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif]gzin my Downloads.[/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif]Doesthat look like I am on track?[/FONT][/COLOR]
[FONT=Liberation Serif]Pleaseexplain to me like I am an idiot four year old Step 3 as the Klingonis quite beyond me.[/FONT]
[FONT=Liberation Serif]Manymany thanks![/FONT]
[FONT=Liberation Serif]Kris [/FONT]
Hello Kris. I understand your plight, I have a brother printer myself. The instructions from the Brother site won't help you much.
Try to install your drivers this way.

[https://sites.google.com/site/easylinuxtipsproject/15](https://sites.google.com/site/easylinuxtipsproject/15)

[URL="https://sites.google.com/site/easylinuxtipsproject/15"]https://forums.linuxmint.com/viewtopic.php?f=90&t=213292&p=1112970&hilit=dorian#p1112970


[/URL]

Hello Kris. To clarify a couple of things. Make sure your printer is connected and switched on, go to your printer settings and and set your DCP7060D as the default printer.
Read the info in the links I gave you, completely before you proceed.  The second link is particularly helpful.
Good luck.:D

---

### Post by krssnda on 2016-03-14
[FONT=Liberation Serif, serif]HiKurt![/FONT]
[FONT=Liberation Serif, serif]Notquite sure what you mean by _**original user's**_DownloadFile.[/FONT]
[FONT=Liberation Serif, serif]MyUbuntu has the following choices: Desk / Documents / Downloads.[/FONT]
[FONT=Liberation Serif, serif]Thatis the Downloads that it was deposited in.[/FONT]
[FONT=Liberation Serif, serif]Leftclick once and twice does nothing.[/FONT]
[FONT=Liberation Serif, serif]Itwill not even highlight the file.[/FONT]
[FONT=Liberation Serif, serif]Rightclick gives me a choice of Show Hidden Files / Show Size Column –no Extraction choice.[/FONT]
[FONT=Liberation Serif, serif]Kris [/FONT]

---

### Post by $yl9pAR%t on 2016-03-14
The file "linux-brprinter-installer-2.0.0-1.gz" is what you downloaded.

The file "linux-brprinter-installer-2.0.0-1" is what you should get after extracting the above mentioned file.

> [COLOR=#000000]Is Unzip the same asExtract?[/COLOR]

Yes, if you have under right click "Extract here" you should choose it.

---

### Post by krssnda on 2016-03-14
[FONT=Liberation Serif, serif][COLOR=#000000]Thefile [/COLOR][COLOR=#000000]linux-brprinter-installer-2.0.0-1[/COLOR][COLOR=#000000]isalso in my Downloads folder so I guess it was extracted.[/COLOR][/FONT]
[FONT=Liberation Serif, serif][COLOR=#000000]Kris[/COLOR][/FONT]

---

### Post by $yl9pAR%t on 2016-03-14
OK, now you can go to point 3 in my post #6 in this thread.

First question will be "Input model name", you should write DCP7060D and hit enter.
Second question about installing packages, write Y and again hit enter.

---

### Post by krssnda on 2016-03-14
[COLOR=#000000][FONT=Liberation Serif, serif]Openin terminal your directory where you have yourlinux-brprinter-installer-2.0.0-1[/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif, serif]Itake it this means go to my Downloads folder.[/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif, serif]Icannot seem to get it to Run.[/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif, serif]Oneand two Left Clicks on linux-brprinter-installer-2.0.0-1 doesnothing.[/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif, serif]Samegoes for Right Click on linux-brprinter-installer-2.0.0-1 other thanchoice of Show Hidden Files / Show Size Column.[/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif, serif]Iam sorry to be so dense[/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif, serif]Kris[/FONT][/COLOR]

---

### Post by $yl9pAR%t on 2016-03-14
As kurt18947 suggested, open terminal and type:

```
cd Downloads
```

it will take you to the directory, where you (should)have your extracted file "linux-brprinter-installer-2.0.0-1"

---

### Post by krssnda on 2016-03-14
[COLOR=#000000][FONT=Liberation Serif, serif]Pleaseforgive me I do not know how to open a terminal.[/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif, serif]Ido have the linux-brprinter-installer-2.0.0-1 file in my Downloadsfolder.[/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif, serif]Ican see it but I cannot do anything with it.[/FONT][/COLOR]

---

### Post by $yl9pAR%t on 2016-03-14
To open terminal press:

Ctrl+Alt+T or Alt+T

In Ubuntu 14.04 it is probably:

Super key(Windowskey)+T

This tutorial can be helpful in the future, when opening folders in terminal

[https://www.youtube.com/watch?v=nWLaAZu-PzE](https://www.youtube.com/watch?v=nWLaAZu-PzE)

---

### Post by krssnda on 2016-03-14
Ctrl+Alt+T gets me the following and I added cd Downloads
kris@kris-X551CAP:~$ cd Downloads
what do I do next?

Windowskey+T got me Trash

---

### Post by $yl9pAR%t on 2016-03-14
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo sh linux-brprinter-installer-2.0.0-1[/FONT][/COLOR]
```

You will be asked about your password, type it and press "Enter".

---

### Post by krssnda on 2016-03-14
I tried Windowskey+T
It got me into Trash.

I typed in the code.
I was asked for my password which I entered.
A note came up stating that the file could not be opened.
I tried a second time with the same results.
Are thoughts of suicide or burning your computer normal when trying to download software?

---

### Post by $yl9pAR%t on 2016-03-14
Ok, forget about this Trash, previously you have got it by Ctrl+Alt+T you said, and it was OK. I am now on Xubuntu 16.04 and some shortcuts are different, but it does not matter.

Go back to this point 
> [COLOR=#000000]kris@kris-X551CAP:~$ cd Downloads[/COLOR]

---

### Post by krssnda on 2016-03-14
got it
now what

---

### Post by Edison_James on 2016-03-14
> **krssnda said:**
> got it
now what

Did you bother to read these links I gave you?


[https://sites.google.com/site/easylinuxtipsproject/15](https://sites.google.com/site/easylinuxtipsproject/15)

[https://forums.linuxmint.com/viewtopic.php?f=90&t=213292&p=1112970&hilit=dorian  #p1112970]("https://sites.google.com/site/easylinuxtipsproject/15")[URL="https://sites.google.com/site/easylinuxtipsproject/15"]
[/URL]

---

### Post by $yl9pAR%t on 2016-03-14
To be sure where we are, type:

```
ls
```

and give me the output of it.

---

### Post by krssnda on 2016-03-14
is that ls as in Lima Sierra

i guess it was ls
this is what I got

CHRIS1.doc  Documents  examples.desktop  Pictures  Templates       Videos
Desktop     Downloads  Music             Public    Untitled 1.doc

---

### Post by $yl9pAR%t on 2016-03-14
yep

Once again, type:

```
cd Downloads
```

and press "Enter"

...and again, type:

```
ls
```

and press "Enter"

and give me the output. 

I think you should see the file we are need here.

---

### Post by krssnda on 2016-03-15
perhaps this will help
/home/kris/Downloads/linux-brprinter-installer-2.0.0-1.gz
the icon for this file is a cardboard box
/home/kris/Downloads/linux-brprinter-installer-2.0.0-1
the icon for this file is a page of script
many thanks
kris

hi james
i somehow never saw this email that you sent me until now
in nay case i followed the instructions as you laid them out in your google site
this is what i got
Driver-packages cannot be found.
 Confirm the model name.


kris@kris-X551CAP:~/Downloads$ dcp7060d
dcp7060d: command not found

many thanks for your help
kris

---

### Post by $yl9pAR%t on 2016-03-15
I see some progress here. As you wrote above, you are able to navigate in terminal to this place:

> [COLOR=#000000]kris@kris-X551CAP:~/Downloads$[/COLOR]

All you have to do now is start reading this thread again from the beginning, and choose one of three similar ways (how-to), you have recived.

---

