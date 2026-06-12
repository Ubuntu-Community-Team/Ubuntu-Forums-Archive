---
title: "adobe reader 7.0 problem in Breezy"
date: 2005-10-16
forum: General Help
---

### Post by bsun on 2005-10-16
I just upgraded to Breezy yesterday and installed Adobe Reader7.0. But Adobe R eader  doesn't work in my system. I cannot launch it!  What is the problem?  Does anyone have encounter this problem?

---

### Post by Hikaru79 on 2005-10-16
We'll need a bit more info than that. What happens when you try to launch acroread from the command line?

---

### Post by traherom on 2005-10-16
I can run it fine, just for the record.

---

### Post by yage on 2005-10-16
[QUOTE=bsun]I just upgraded to Breezy yesterday and installed Adobe Reader7.0. But Adobe R eader  doesn't work in my system. I cannot launch it!  What is the problem?  Does anyone have encounter this problem?[/QUOTE]
Did you install it from source or via synaptic?

Can you paste the output from the Terminal when writing```
acroread
```
Need this to help you ;)

---

### Post by zuoliang on 2005-10-16
One possible reason for this is the conflict between some other program with acroread. I've encountered the same problem and it turns out that acoread is not compatable with SCIM -- a chinese input environment. 

Try following command from shell:
 "GTK_IM_MODULE=xim acroread"
see if that works.

---

### Post by bsun on 2005-10-17
If I start acroread from the terminal, there is no output there. 

I don't know whether its because the conflict between SCIM and acroread because I tried "GTK..." and still I cannot launch acroread. 

By saying " I cannot launch ...", I mean there is no such process except the start figure when I input "acroread" in the terminal.

---

### Post by ember on 2005-10-17
I had basically the same problem. Look at /usr/bin/acroread ... I guess it's not executable and empty. 
What I did was downloading a localized version from Adobe and then creating a symlink instead of the empty shellscript.

Thus:
1. Open a terminal
2. Become root (or use sudo for the following commands)
3. rm -f /usr/bin/acroread
4. ln -s /usr/local/Adobe/Acrobat7.0/bin/acroread /usr/
5. You will get an error about PPKLite.api not working, but if you move that file out of the Acrobat plugin directory, it disappears and the Reader works flawlessly.

HTH,
ember

---

### Post by plumcreek on 2005-10-18
[quote=zuoliang]One possible reason for this is the conflict between some other program with acroread. I've encountered the same problem and it turns out that acoread is not compatable with SCIM -- a chinese input environment. 

Try following command from shell:
 "GTK_IM_MODULE=xim acroread"
see if that works.[/quote]

That worked for me on my alien installed Adobe Reader.

Does you (or anyone else) know of any way to get Adobe Reader and SCIM to be happy together? I really need to have both programs.

Thanks.

---

### Post by zuoliang on 2005-10-18
You can add 
  GTK_IM_MODULE=xim
to the very beginning of the file acroread which can be found by 
  which acroread
Same methode works for realply

[QUOTE=plumcreek]That worked for me on my alien installed Adobe Reader.

Does you (or anyone else) know of any way to get Adobe Reader and SCIM to be happy together? I really need to have both programs.

Thanks.[/QUOTE]

---

### Post by EricZapletal on 2005-10-18
Hi,

the README file says you have to install libstdc++5 library (Breezy comes with version 6)

It was useful in my case, I hope it will help you too.

EZ

---

### Post by bsun on 2005-10-18
I installed Adobe Reader using Synpatic Package Manager and everything is OK!  I don't have SCIM in my computer.   Thanks guys.

---

### Post by maulattu on 2005-10-19
[QUOTE=EricZapletal]Hi,

the README file says you have to install libstdc++5 library (Breezy comes with version 6)

It was useful in my case, I hope it will help you too.

EZ[/QUOTE]

the same for me. with libstdc++ 6 acroread didn't start at all (without any error message too:???: ), but with libstdc++ 5 works well:cool: \\:D/

---

### Post by lonetree on 2005-10-19
I have the same kind of problem with breezy too. Just for the record, I have SCIM installed and yes, it started off well if I type "GTK_IM_MODULE=xim acroread" in terminal, but if I use acroread itself, it won't start after seeing the splash screen.

Anyone has any work around for this?


thanks

*** My confidence drops tremendously after using Breezy ***

---

### Post by Riverside on 2005-10-19
Not the answer to the original poster's question I know, but I recently switched from using Acrobat Reader to using xpdf.  xpdf is open source software, and in my experience works extremely well as a PDF viewer.  There are no "phoning home" potential privacy issues with xpdf as there are with Acrobat Reader 7.0 either, of course.

---

### Post by hunteramor on 2005-10-19
i have both the libstdc++5 and libstdc++6 packages, but i'm still encountering this problem.  if i remove libstdc++6, a ton of other packages have to be removed to.

those who fixed this problem in this way: did you remove libstdc++6, get acroread to use libstdc++5 instead of the 'most recent' one, or what?

---

### Post by stevetxt on 2005-10-19
I just installed Breezy but can not find acroread in the repositories.  I uncommented the two lines for universe sources in /etc/sources.list.  Can someone tell me where to get it and then how to configure it, or where to find instructions for that.  Do instructions on acrobat for Hoary work in Breezy?

Thanks.

Steve

---

### Post by EricZapletal on 2005-10-19
Hi,

another comment on this problem :

I have just install (this morning) a new PC with Breezy. On this fresh installation :

- I have downloaded acrobat reader from the Adobe web site (tar.gz format)
- after the installation, Adobe acroread did not correctly start  (it crashes in less than 1 second)
- I installed libstdc++5 (and gcc-3.3) with synaptic (I did not remove libstdc++6)
- then, when I rerun Adobe acroread it works fine !!

I have the same problem on 2 different PC, and the problem was corrected the same way on these 2 PC...

I hope it will help you...

EZ

---

### Post by arfon on 2005-10-19
I have had the same issue here where I can't "apt-get install acroread" on a fresh install of breezy.  Just to confirm that if you download the acrobat.tar.gz file from the adobe pages and run the installer you should be set.

Btw, rather than symlinking to /usr as someone mentioned before I did
"ln -s /usr/local/Adobe/Acrobat7.0/bin/acroread /usr/bin/" 

as /usr/bin are already in the default path :)

---

### Post by lonetree on 2005-10-24
[QUOTE=EricZapletal]Hi,

another comment on this problem :

I have just install (this morning) a new PC with Breezy. On this fresh installation :

- I have downloaded acrobat reader from the Adobe web site (tar.gz format)
- after the installation, Adobe acroread did not correctly start  (it crashes in less than 1 second)
- I installed libstdc++5 (and gcc-3.3) with synaptic (I did not remove libstdc++6)
- then, when I rerun Adobe acroread it works fine !!

I have the same problem on 2 different PC, and the problem was corrected the same way on these 2 PC...

I hope it will help you...

EZ[/QUOTE]

Hi EricZapletal,

did you try with SCIM? My Adobe reader was installed fine but after installing SCIM, Adobe reader just stop responding.

regards,

---

### Post by EricZapletal on 2005-10-26
[QUOTE=lonetree]Hi EricZapletal,

did you try with SCIM? My Adobe reader was installed fine but after installing SCIM, Adobe reader just stop responding.

regards,[/QUOTE]

Hi,

I did not try SCIM ...

but I found something with SCIM and acroread :
[http://www.scim-im.org/wiki/faq/gtk_gnome/why_firefox_mozilla_acrobat_reader_7_other_gtk_2_based_apps_can_not_be_installed_started]("http://www.scim-im.org/wiki/faq/gtk_gnome/why_firefox_mozilla_acrobat_reader_7_other_gtk_2_based_apps_can_not_be_installed_started")

it seems the problem is still coming from incompatible versions of libc ...

EZ

---

### Post by lonetree on 2005-10-26
[QUOTE=EricZapletal]Hi,

I did not try SCIM ...

but I found something with SCIM and acroread :
[http://www.scim-im.org/wiki/faq/gtk_gnome/why_firefox_mozilla_acrobat_reader_7_other_gtk_2_based_apps_can_not_be_installed_started]("http://www.scim-im.org/wiki/faq/gtk_gnome/why_firefox_mozilla_acrobat_reader_7_other_gtk_2_based_apps_can_not_be_installed_started")

it seems the problem is still coming from incompatible versions of libc ...

EZ[/QUOTE]

Thanks to EricZapletal

the link will definitely help a lot of us having problem with acroread with SCIM installed. I have resolved the problem.

For those who are not sure what to do, this is what I did.

# sudo gedit /usr/bin/acroread

then add the line GTK_IM_MODULE=xim

exit and run acroread, plugin for firefox fox will also run if it is installed

cheers all

---

### Post by alfred on 2005-12-28
Adding libstdc++5 worked for me.
Did it mess anything else up?
Also I made the link in /usr/bin as mentioned above.
Evince and xpdf are great but sometime from Gnucash I print pdf files only to find out the person I sent it to can not read it so this is one way to test it.
Otherwise I have no use for it.
Thanks for the threads...
Al

---

### Post by colours on 2005-12-30
SCIM was my problem too! Thanks all.

---

### Post by John Jason Jordan on 2006-01-01
[QUOTE=alfred]Adding libstdc++5 worked for me.
Did it mess anything else up?
Also I made the link in /usr/bin as mentioned above.[/QUOTE]
I've tried everything I can think of to get Acrobat Reader 7.0 to run on my Breezy-64 computer. The INSTALL script appears to run OK. It is installed in /usr/local/Adobe/Acrobat7.0, which has several subfolders and sub-subfolders, full of interesting files whose purpose I have no idea about.

It did not install a menu item in my Gnome panel. I tried running it from the command line ("acroread") but all I get is "command not found." Maybe I'm not in the right folder? I searched for acroread and found it in /usr/local/Adobe/Acroread7.0/intellinux/bin. Right clicking on it reveales that it is an executable file (16.5 Mb). Double-clicking on it does nothing at all. I navigated to that folder in the command line and gave it the "acroread" command again, but still nothing happens. Permissions for the acroread file are rwxr-xr-x. Being a n00b to Linux I have no idea what that means. I also tried running it from the command line with sudo, but still all I get is "command not found."

I checked in Synaptic and I already have libstdc++5 installed. The README file says it requires libstdc++.so.5, which I assume is the same thing. Searching for files reveals that I have one each in the /usr/lib folder (829,854 buytes) and in the /usr/lib32 folder (737,496 bytes). There are also various other versions installed.

Can anyone shed some light as to why it appears to be installed but does not launch?

---

### Post by hiaw on 2006-01-03
[QUOTE=zuoliang]You can add 
  GTK_IM_MODULE=xim
to the very beginning of the file acroread which can be found by 
  which acroread
Same methode works for realply[/QUOTE]


Don't forget to add "export" in front of
  GTK_IM_MODULE=xim

Wasted 15 mins of my life trying to get this to work....

---

### Post by Akli on 2006-03-02
I reinstalled Ubuntu and tried to install acrobat 7 but had the same problems as you guys, it seemed very weird since I have installed it before! Installing libstdc++5 worked for me, thanks!! 

In my previous install I installed libstdc++5 for something else but did not know that it was necessary for adobe, thanks again.

---

### Post by rimshot on 2006-03-09
thanks to everyone on this thread. After scrathing my head for a long time I finally came across this disucssion and using one of your suggesstions work.

For the record, I have a very recent breezy installation.

Putting in:
GTK_IM_MODULE=xim
does nothing. Still just get acrobat to launch for a split second and then crash with nothing in the log files.

installed libstdc++5
using: sudo apt-get install libstdc++5
it worked. I now can laucnh acroread.

Also, someone else asked the same question, but WHY can I not just use
apt-get install acroread?

I keep getting the following text. Yes, I have enable the universe and even all of the other repositories that came in my sources.list file.

====
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package acroread has no installation candidate
====

cheers!

---

