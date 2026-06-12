---
title: "Error message: &quot; cannot be installed on your computer type (i386) &quot;"
date: 2006-11-02
forum: General Help
---

### Post by 9812713 on 2006-11-02
Hello 

I would not consider myself a newbie to Ubuntu, but I started using Ubuntu Edgy, 2nd release of the beta, before the RC release.

Now here is the problem. The default install is great, I do the following "after Tweaking"

Un-install:
   + Games
 
Install:
   + Gstreamer plugins
   + K9copy
   + libdvdcss2
   + Flash 9
   + System Patches / Updates.

Here is my story.

I just did a fresh install, and went to remove the default games in Unbuntu, and it gave me the error message 

" Ataxx cannot be installed on your computer type (i386) "

I get the same error message when I go to Install k9copy..

" k9copy cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type. "

what am I missing, this warning message has only started today (November 2nd 2006) and wish I could get these programs install / removed.

I am currently using ubuntu on my notebook (IBM T41) and everything worked without a hitch. 

Please guide me / let me know if there is a "Global" problem with my install. 

Furthermore, please put this in the correct forum if this is a incorrect post.

Thank you..

---

### Post by 9812713 on 2006-11-03
As a follow-up, I reinstalled the complete OS, and it has something to do with the community... 

Who do I have to talk to enable this community release ?

Is there anyone out there?

Wil

---

### Post by redthongandbrains on 2006-11-04
This is not an answer, but to point out that this same error is  experienced here. I need to install applications I need, and they simply won't. Any help would be very welcome... or should I just return to Dapper, where installs are error-free :) No, wanna stay with Edgy...

---

### Post by lompa on 2006-11-05
Hi

I'm not an expert, but it simply looks that edgy supports a package authentication feature: some packages are encrypted with public keyx, to install them you need to get the key and add it in synaptics (repositories, authentication tab). I did it for amarok, and it worked

Bye!

Lompa

---

### Post by andy456 on 2006-11-07
hello, I have here the same problem. The strange thing is that I installed ubuntu 6.10 on 2 pc's and did (according to me) everything the same way, and one is working perfectly and the other one has problems. 

The working one is a Dell Inspiron 8200 (Pentium 4). The not working one is a Dell Dimension 9150 (Pentium D930)

They are both located on the same network and the sources.list is completely the same.

My guess is that there is a problem with the processor (since everything else seems to work :D ). But I haven't got alot of experience with linux and I have no idea how to check for such problems. Do I maybe need to install the 64bits version ? (the D930 has EMT64) and if so can this help me ?

I hope somebody can help me, and otherwise thanks for listening ;) 

ps. with not working I mean: cannot install software :neutral:

---

### Post by andy456 on 2006-11-07
hello, I have here the same problem. The strange thing is that I installed ubuntu 6.10 on 2 pc's and did (according to me) everything the same way, and one is working perfectly and the other one has problems. 

The working one is a Dell Inspiron 8200 (Pentium 4). The not working one is a Dell Dimension 9150 (Pentium D930)

They are both located on the same network and the sources.list is completely the same.

My guess is that there is a problem with the processor (since everything else seems to work :D ). But I haven't got alot of experience with linux and I have no idea how to check for such problems. Do I maybe need to install the 64bits version ? (the D930 has EMT64) and if so can this help me ?

I hope somebody can help me, and otherwise thanks for listening ;) 

ps. with not working I mean: cannot install software :neutral:

---

### Post by 9812713 on 2006-11-10
Hi All,

I do have a fix ... but it is not using the add/remove module in ubuntu..

On the machine you are having problems with run this command in a terminal


sudo aptitude install k9copy

Also, you have to make sure you have the Decss library installed. I use the debian version, but it you install Automatix (2) .. you will be able to install the appropriate decrypt library.

Let me know if this helps.
Wil

---

### Post by jallain on 2006-11-10
If you live in the States you can use this easy fix. Modify your sources.list and remove the "us" from the listings. In other words, don't use the us mirrors. I had the same problem until I did this. Now I can install with no problems.

---

### Post by clubsoda on 2006-11-14
Same problem here, very disappointing.

OpenOffice has not been installed.
Add/Remove says "cannot be installed".
Synaptic doesn't even list it, and won't list the packages off the Xubuntu Edgy Eft CDROM.

Having to connect to the internet in order to install packages from the CD seems bizarre, but I will do so if necessary.

Despite this problem Add/Remove looks great and will be very powerful once it's up and running.

---

### Post by Moonshiner on 2006-11-15
Same problem. And not only with Xubuntu, but very similar thing with Kubuntu:

In Xubuntu I receive "cannot be installed on your computer type (i386)" message when trying to install, for example, any KDE applications.

In Kubuntu's "Add/Remove" most of the applications just grayed out, including, for example, Gimp and Firefox ;(

---

### Post by clubsoda on 2006-11-15
I've had some progress.  Although I really wanted to achieve a stand-alone installation, Synaptic kept telling me "the list of applications is out of date", so I gave in and connected it to the net, let it download another list.  This has restored my powers to install packages and extra language support, however Synaptic wants to download everything from the 'net and won't use what's on the CD.  I've posted a [bug report](https://launchpad.net/distros/ubuntu/+source/synaptic/+bug/71964).  Wish me/us luck!

Question: Did everyone suffering this problem do something unusual in their installation settings, like city/language/manual-partitioning etc.?
Personally I don't believe in the "hardware features"/"computer type" error message as my machine is a vanilla Pentium, old but standard, and Xubuntu recognised all my devices.  
Isn't it more likely that installation settings are upsetting the scripts somehow?  I may try reinstalling with default settings (as far as possible) to see if that works.

---

### Post by Moonshiner on 2006-11-15
Personally, I don't think it has something to do with PC configuration. Had nothing of this sort on Dapper on same machine :-?

---

### Post by clubsoda on 2006-11-16
Hi Moonshiner,

Yeah, you're probably right.  I tried a default installation (except for manual partitions) and it didn't help.

How does Synaptic decide that the list of applications is out of date?  Is that just based on the computer's clock & calendar?  How about if I set the date to the Edgy Eft release date and install...

Maybe as lompa suggested it's a key problem.  Synaptic thinks the package list is out of date so it discards the key(s) which are needed to install from the CD.  Once you "reload" the list and keys from the repository the packages are no longer identical so you never get a chance to install from the CD.  Just my speculation.

---

### Post by Moonshiner on 2006-11-16
Just as Alice said: curiousier and curiousier :)

---

### Post by jimi_bond on 2006-12-04
I had the same problem but managed to fix it by goint to System->Administration->Software Sources and deselecting the "source code" option, I now have the other 4 ticked and it works fine.

---

### Post by bottleman on 2006-12-23
i had this same problem.  EVERY program in the Add/Remove interface got that same error message. 

but jallain & jimi_bond's tips worked for me.  i just went to the System>Administration>Software Sources and deselected downloads from the mirrors.  now the interface works as promised.  thanks!

---

### Post by AnEnglishmaninIreland on 2007-02-28
All of the above and more errors in different places.  I had thought (in error) that the sudo password defaults to blank (because it didn't give me an authentication errorr) but in fact the sudo password is the same as the logged on user.  Using that password fixed the lot.

---

### Post by jtchupp on 2007-03-21
> **bottleman said:**
> i had this same problem.  EVERY program in the Add/Remove interface got that same error message. 

but jallain & jimi_bond's tips worked for me.  i just went to the System>Administration>Software Sources and deselected downloads from the mirrors.  now the interface works as promised.  thanks!

Works great here! thanks!

---

### Post by revelation.now on 2007-03-23
again, selecting the main server seemed to fix things. It actually changed the behaviour of my add / remove applications all together. before i clicked on the check boxes and things installed immediately. now they wait for an apply.

---

### Post by nakedfanatic on 2007-04-10
> **jallain said:**
> If you live in the States you can use this easy fix. Modify your sources.list and remove the "us" from the listings. In other words, don't use the us mirrors. I had the same problem until I did this. Now I can install with no problems.

I fixed the same problem today by moving from the "main" server over to the "US server". As this is the opposite of Jallain's advice I'm led to believe that this error is caused by temporary problems with the selected server.

btw, I'm a New Zealand user and the default list of servers was "Main server" "US server" and "New Zealand server". The New Zealand server seems to have disappeared from my list now however. :-s

---

### Post by amme_psycho on 2007-10-30
> **bottleman said:**
> i had this same problem.  EVERY program in the Add/Remove interface got that same error message. 

but jallain & jimi_bond's tips worked for me.  i just went to the System>Administration>Software Sources and deselected downloads from the mirrors.  now the interface works as promised.  thanks!

what do you mean by downloads from the mirrors?...is it the "main","universe","restricted", or "multiverse"?

---

### Post by bevroren on 2008-07-02
Hii
I am new to Linux
I just installed Ubuntu 8.04 from inside xp as dual boot on my IBM Thinkpad R51, celeron 1.3 Ghz, 512 MB RAM..

I just dont know anything about Linux yet and installed it to learn it cuz i am fed up of windows Vulnerabilities and its slowdown thingss..

I tied to open mp3 files in Ubuntu but i cannot as easily it opens in windows. I tried to install the media player listed in linux list of programs, but i get an error message which says something like
"Cannot be installed on your computer type(i386)"
Please help me out to fix this..
Thanks a lot in advance

---

### Post by evilopinions on 2008-07-22
> **jimi_bond said:**
> I had the same problem but managed to fix it by goint to System->Administration->Software Sources and deselecting the "source code" option, I now have the other 4 ticked and it works fine.

Works perfectly...

Thanks a heap...

---

