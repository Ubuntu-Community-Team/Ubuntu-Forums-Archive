---
title: "Skype installation and use on Ubuntu 6.10"
date: 2006-12-31
forum: General Help
---

### Post by mhenriday on 2006-12-31
Following the instructions on [***Skype**'s website*]("http://www.skype.com/intl/sv/download/skype/linux/"), I downloaded the **Dynamic binary tar.bz2** to my user directory and, using the line command «tar xjvf skype-1.3.0.53-generic.tar.bz2», proceeded to install it there. The installation process seemed to proceed normally with, if I've counted correctly, 52 lines of files, among which «skype-1.3.0.53/skype.desktop» and three separate lines of icon files. But I can't find a **Skype** icon on my desktop or under «Internet» or any other subcategory under «Applications». I've tried packing up the tarball to a new **skype-1.3.0.53** directory under my user directory, and checked to see if the executable file is there (it is), but this doesn't seem to make any difference - I still can't access **Skype** ! Any suggestions as to what I'm doing wrong, and what can be done to correct it ?...

Henri

PS : I'm using a standard **Gnome** interface....

---

### Post by mdurham on 2006-12-31
Can you try [http://www.skype.com/download/skype/linux/"]http://www.skype.com/download/skype/linux/](") and download the DEB
This was the easiest thing I've ever installed on Linux.

---

### Post by bulldog on 2006-12-31
Or hit ALT+F2 and type skype in the box and see if it appears on your screen.

---

### Post by mhenriday on 2007-01-01
Curiouser and curiouser ! I took **mdurham**'s kind suggestion, and after removing the **Skype** files remaining from my earlier download - Alt+F2 did indeed give access to this latter on my screen, but I was unable to run it - downloaded **skype_debian-1.3.0.53-1_i386.deb**. I then opened the package with the standard **GDebi** package installer, and found to my joy that I now had a **Skype** icon under Applications&#8594;Internet. But when I double-clicked on the icon, nothing happened ! I decided to check by writing a «skype» command in my terminal, which resulted in the following line :
[INDENT]*** glibc detected *** skype: free(): invalid pointer: 0x08ae6f60 ***[/INDENT]
followed by literally hundreds of lines of code, which ended in the following :
[INDENT]Avbruten [i e, terminated] (SIGABRT) (core dumped).[/INDENT]

I then tried first saving the download to my harddisk (as **/home/mhenriday/skype_debian-1.3.0.53-1_i386.deb** under my user directory) and _then_ opening the package, with the same results - the program cannot be run ! As before, it appears when I use Alt+F2, but no matter whether I attempt to run it in the terminal (the core is always dumped) or with a file name after the command (nothing happens), I can't get it to work. I've lived long enough to make a certain acquaintance with **Murphy's Law**, but this is carrying things to extremes !...

Any suggestions ?...

Henri

---

### Post by bulldog on 2007-01-01
Well I used automatix2 to install skype and so far no problems with it.

[http://getautomatix.com/wiki/index.php?title=Installation#Easy_Direct_Installation](http://getautomatix.com/wiki/index.php?title=Installation#Easy_Direct_Installation)

---

### Post by energiya on 2007-01-01
Hi,

The easyest way to install Skype is using apt-get.
Write in a terminal window
> sudo nano /etc/apt/sources.list
(if you don't like nano, use gksudo gedit /etc/apt/sources.list)
then add at the end of the file
> # Skype packages
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

... do a "sudo aptitude update" and "sudo aptitude install skype" and that's it ! :)

---

### Post by mhenriday on 2007-01-01
Alas, my problem lies not with installing **Skype**, but rather with getting it to _work_, once installed ! I thought maybe I could finesse the matter by uninstalling the version I recently downloaded, and then reinstalling it from **Automatix 2**, which, if I remember correctly, I originally did, and which seems to work well for **bulldog**. I used the uninstall feature on **Automatix 2** to remove **Skype**, and then proceeded to install it again using the same programme. But despite crossing my toes (I find it difficult to type with crossed fingers) during the process, I now find myself unable to get the new version of **Skype** to work any better than I did the old. My conclusion is that something must be gumming up the works, presumably remnants of a previous **Skype** download (I did have it working well enough to be able to send and receive chat messages a couple of weeks ago, but since then, zilch). On **Windows**, I should have no difficulty checking this out, but in **Ubuntu**, I'm not sure how best to go about it. Any suggestions ?...

Henri

---

### Post by mhenriday on 2007-01-21
Like a bad penny, I turn up again ! After re-installing **Edgy** and then **Skype** (via **Automatix2**, apt-get and aptitude on the console, and directly from the **Skype** website) and making sure, just to be safe, that

[INDENT]## Official Skype Repository
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free[/INDENT]

is on my sources list, I still find it impossible to launch **Skype** via **Applications&#8594;Internet&#8594;Skype** ; when I double-click on the **Skype** icon, nothing happens at all. When I attempt to start the application through the console, by typing «skype» or «sudo skype», the following message (the code of the «invalid pointer» can vary slightly) :

[INDENT]*** glibc detected *** skype: free(): invalid pointer: 0x08ae2138 ***[/INDENT]
and after a long «backtrace» and an even longer «memory map», I'm still winding up with

[INDENT]Avbruten (SIGABRT) (core dumped).[/INDENT]

If any readers have suggestions differing from those given above in earlier postings to the thread, and which could help me to launch the **Skype**, I'd be most grateful to hear/see them !...

Henri

---

### Post by biggunks on 2007-02-02
I've got the exact same problem running Skype on Edgy.  I get a floating point exception (core dumped) through the console and nothing happens when using the menu.  I've tried apt, both the deb and tar files on skype.com, and automatix.  The end result is the same no matter which way I go.

---

### Post by biggunks on 2007-02-02
I'm not sure what kind of video card you have.  I have an ATI Radeon 9550.  Anyways, the skype problem goes away when I restored my xorg.conf from the fglrx version to the original version.  I guess it couldn't draw the GUI.  I know that is what fixed the problem because I restored the file and restarted gdm then the problem was fixed.  I go back to the fglrx and the problem reappears.  I also had a similar problem to with mythtv a while back.

---

### Post by mhenriday on 2007-02-08
Thanks for your two messages, **biggunks**! I have an **NVidia5** (**RIVA TNT2/TNT2 Pro**), which came with this ancient **Dell** machine when I purchased it in the last year of the last century. **Skype** always worked well on **Windows,**, and if memory serves, it also worked on **Dapper**. Since upgrading to **Edgy**, however, it's been no go. Can I perform some sort of action similar to yours to make it work again ?...

Another problem, which, as the causes of my difficulties may just possibly be related to the above, I post here : I've been having difficulty reading from a CD with a pdf programme which I use in teaching computer-naive retired persons how to cope with their (**Windows**) machines. At first, I couldn't get my machine to accept the programme password and was thus unable to open it, but by adding **Adobe Reader** (7.0) to the **xpdf** programme I had already installed, this problem was resolved. I am still, however, unable to open the _embedded videos_ in the programme ; on attempting to do so, I get a message to the effect that «The plug-in required by this 'Rendition' action is not available. Information about the missing plug-in may be available on Adobe's Web site.» I've tried looking for relevant information on the **Adobe** site, but with no success. Could this also be a graphics problem, which a minor change like that described by **biggunks** above, could eliminate ?...

Henri

---

### Post by S!ian on 2007-03-20
Maybe it is a little late, but this [http://www.ubuntuforums.org/showthread.php?t=304764&highlight=skype+glibc](http://www.ubuntuforums.org/showthread.php?t=304764&highlight=skype+glibc) helped me to  solve the same problem you have.  However, it will not allow to use SCIM and skype together.

---

### Post by mhenriday on 2007-04-08
> **S!ian said:**
> Maybe it is a little late, but this [http://www.ubuntuforums.org/showthread.php?t=304764&highlight=skype+glibc](http://www.ubuntuforums.org/showthread.php?t=304764&highlight=skype+glibc) helped me to  solve the same problem you have.  However, it will not allow to use SCIM and skype together.

Thanks for the heads-up, **Slian** ! Using the command «XMODIFIERS=@im=none QT_IM_MODULE=xim skype», which I found on the thread to which you provided a link, I was able to open **Skype** and send a chat message, despite the fact that I have **SCIM** opened as well (I didn't, however, test to see if I could use **SCIM** to write the message - that will have to await a later trial). Do you know if it is possible to _receive_ a chat message, if **Skype** has not already been opened using the above command - i e, will it open itself automatically on an **Edgy** machine using **SCIM** ? My guess is that it will not, and that **Skype** must be opened via the above command before messages (or, for that matter, calls) can be received, but it would be nice to hear from someone who possesses more experience in this matter....

If I have to choose between **SCIM** and **Skype**, I'll take the former, on which I am utterly dependent when I have to write in East Asian languages. Think how convenient it would be were this interference to be fixed in time for the **Feisty** upgrade, which will be released in little more than a week ! But as **]Nbx*cmD[ ** pointed out on the other thread, it's a **Skype** rather than an **Ubuntu** problem, and I suspect that **Skype** developers have their priorities elsewhere....

Henri

PS : Tried to write a **Skype** message in Chinese directly from my keyboard, but not surprisingly it didn't work. So can it go....

---

### Post by S!ian on 2007-04-13
Hallo mhenriday, I'm not sure if I understand what you mean. You can't use skype and SCIM together at this point, but it seems that the skype developers rewriting the code, so maybe the new release won't have this problem anymore. I agree, not being able to use East Asian languages is a pain.

P.S.: If you don't want to write "XMODIFIERS=@im=none QT_IM_MODULE=xim skype" all the time in a terminal, you can do this (post #13 method B): [http://forum.skype.com/index.php?showtopic=64211&hl=scim](http://forum.skype.com/index.php?showtopic=64211&hl=scim)

---

### Post by nevernamed on 2007-04-15
> **mdurham said:**
> Can you try [http://www.skype.com/download/skype/linux/"]http://www.skype.com/download/skype/linux/](") and download the DEB
This was the easiest thing I've ever installed on Linux.

I downloaded the debian package from the skype website and it was a very easy install, the icon even shows up nicely under the Applications>Internet menu.
However, when I try to run it (even with the alt+f2) nothing happens. When I type "skype" into console I get the following
```
Inconsistency detected by ld.so: dl-runtime.c: 77: _dl_fixup: Assertion `((reloc->r_info) & 0xff) == 7' failed!

```
Does anybody know how I can solve this problem and run skype?
Thanks,

---

### Post by mhenriday on 2007-04-21
> **S!ian said:**
> Hallo mhenriday, I'm not sure if I understand what you mean. You can't use skype and SCIM together at this point, but it seems that the skype developers rewriting the code, so maybe the new release won't have this problem anymore. I agree, not being able to use East Asian languages is a pain.

P.S.: If you don't want to write "XMODIFIERS=@im=none QT_IM_MODULE=xim skype" all the time in a terminal, you can do this (post #13 method B): [http://forum.skype.com/index.php?showtopic=64211&hl=scim](http://forum.skype.com/index.php?showtopic=64211&hl=scim)
Thanks, **Slian**, for the link to **PV_Milk**'s posting on the **Skype** forum for **Linux**. I tried his first suggestion without success, but the second solution worked like a charm on my new **Feisty** installation, and allows a **SCIM** user to open **Skype** directly from **Applications&#8594;Internet**. Here below, for the convenience of visitors to this thread, is the procedure suggested by **PV_Milk**, with a few linguistic and orthographic modifications :
[INDENT]This solution uses the bash file to call up skype. In the bash file one adds the following command : 
1) Rename /usr/bin/skype to /usr/bin/skype0 :
$ sudo mv /usr/bin/skype /usr/bin/skype0
2) Make a new file call "skype" in /usr/bin :
$ sudo gedit /usr/bin/skype

********************in the file***************************

#!/bin/bash

export LANG=c
#Call to original skype file that you just rename
QT_IM_MODULE=xim skype0

*********************end file*****************************

3) Change skype permission to executable :
$ sudo chmod 755 /usr/bin/skype[/INDENT]

The only problem which remains is that even in **Feisty**, **SCIM** cannot be used to write Asian languages in **Skype** chat. I hope the **Skype** programmers find a way to resolve this problem !...

Henri

---

