---
title: "Puzzled... Am I running 12.04.1 or 12.04.2 ?"
date: 2013-02-08
forum: General Help
---

### Post by the8thstar on 2013-02-08
Hello,

I am puzzled as to know if I'm running 12.04.1 or 12.04.2, as the following screenshot will show :

[IMG]http://i.imgur.com/dKFvzFF.png[/IMG]

So which is right ?

Thanks for your help!

---

### Post by Cheesemill on 2013-02-08
You're running 12.04.1.

12.04.2 hasn't been released yet.

[http://ubuntuforums.org/showpost.php?p=12497190&postcount=47](http://ubuntuforums.org/showpost.php?p=12497190&postcount=47)

---

### Post by rnerwein on 2013-02-08
> **Cheesemill said:**
> You're running 12.04.1.

12.04.2 hasn't been released yet.

[http://ubuntuforums.org/showpost.php?p=12497190&postcount=47](http://ubuntuforums.org/showpost.php?p=12497190&postcount=47)
hi
that's nice - here is the "future ????" output of my:
root@tschang:/etc 16:38-> cat lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.[COLOR=Red]2[/COLOR] LTS" [COLOR=Red]<=====[/COLOR]
:confused:
have a nice day
cheers

---

### Post by Cheesemill on 2013-02-08
Did you read the post I linked to? The base-files package has been updated with the 12.04.2 information in ***preparation*** for its release.

> base-files (6.5ubuntu6.5) precise; urgency=low

  * /etc/issue, /etc/issue.net, /etc/lsb-release, /etc/os-release: Bump
    version number to 12.04.2 in preparation for the point release.

 -- Colin Watson <cjwatson@ubuntu.com>  Fri, 25 Jan 2013 11:07:10 +0000

---

### Post by the8thstar on 2013-02-08
Thanks, all. I guess it basically means 12.04.2 is coming VERY soon.

---

### Post by Cheesemill on 2013-02-08
It's due on the 14th.

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule)

---

### Post by the8thstar on 2013-02-08
> **Cheesemill said:**
> It's due on the 14th.

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule)

Yay, thanks for the info!

---

### Post by foberle on 2013-02-10
"In preparation for its release" ... Seriously??

In that spirit, I've changed the number 5 on one of my dollar bills to a 10 in preparation for getting a raise... and, I've changed the size number on my belt and the cholesterol numbers on my blood test results in preparation for the new diet my doctor is sure to put me on.

Doesn't the fact that you are reporting something that isn't true cause support problems? Does this cavalier attitude explain why I seldom get any useful responses from the forum?

Yikes!!!

---

### Post by Bufeu on 2013-02-10
*cat /etc/*-release* will tell you.

---

### Post by Cheesemill on 2013-02-10
> **Bufeu said:**
> *cat /etc/*-release* will tell you.
It doesn't, that's the issue being discussed,

The package that provides the text in the /etc/*-release files has been updated to read 12.04.2 even though it hasn't been released yet.

Unless you are one of the people ISO testing the upcoming 12.04.2 release then you are still on 12.04.1, no matter what the above command says.

---

### Post by howefield on 2013-02-10
> **Cheesemill said:**
> Unless you are one of the people ISO testing the upcoming 12.04.2 release then you are still on 12.04.1, no matter what the above command says.

Which packages aren't available to 12.04.1 but are on the test ISO ?

---

### Post by Cheesemill on 2013-02-11
I would guess the 3.5 kernel and the new graphics subsystem backported from Quantal.

[https://lists.ubuntu.com/archives/ubuntu-devel/2012-August/035615.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-August/035615.html)

---

### Post by howefield on 2013-02-11
That's ok, I didn't expect you'd know.

The lack of running those particular packages doesn't mean the OP isn't running 12.04.2.

---

### Post by GrzesiekC on 2013-02-16
I need some help here. How can I install the X.org back-ports properly. 
I've tried install xserver-xorg-lts-quantal, but after restart I've got only a black screen.
I've got the kernel back-ports already.

Cheers
Gregory

---

### Post by the8thstar on 2013-02-18
> **GrzesiekC said:**
> I need some help here. How can I install the X.org back-ports properly. 
I've tried install xserver-xorg-lts-quantal, but after restart I've got only a black screen.
I've got the kernel back-ports already.

Cheers
Gregory

Hello,

I suggest you open a new thread to address your specific issue, where you will certainly gather a larger audience.

---

### Post by bogan on 2013-02-18
Hi!, **All,**

I am surprised no-one seems to have answered the OP's question, or told him how to find out for themselves.

Quick Answer: run: ```
uname -ar 
# if it shows something like:
# 3.5.0-23-generic #36-Ubuntu SMP Thu Feb 7 05:32:22 UTC 2013 i686 i686 i686 GNU/Linux
#Then it is running the full 12.04.2 version, with the 3.5 Quantal kernal.
# if it shows something like:
# "3.2.0-23-bla-bla-" it is still running the Precise kernal, and may be 12.04 or 12.04.1.
```I am running three versions of what report themselves to be 12.04.2, they are all different.

The first is actually 12.0.4.1, fully updated in Update Manager, but not upgraded to 12.04.2.
 'uname -r' returns: "3.2.0-37-xxx", though: "cat  /etc/lsb-release" shows "12.04.2"

The second is as the first but has been upgraded to 12.04.2 in Update Manager, although it does not have the Precise/Quantal kernals and Backports,  it does have certain "lts-quantal" files necesssary to enable the installation of the 3.5.xx kernals. 'uname -r' still returns: "3.2.0-37-xxx". Searching Synaptic with "backports" as Filter and Status set to 'Installed' will show those additional files.

The third has had the 12.04.1 installation root partition formatted and 12.04.2 installed. 'uname -r' returns: "3.5.0-23", and "cat /etc/lsb-release" shows "12.04.2", the same as previously. Searching Synaptic with "backports", or "quantal," as Filter, and Status set to 'Installed', or 'Not installed', will show a huge number of additional files;  backports, linux-headers, linux-images,and linux-xxx-lts-quantal files.

As installing certain packages such as 'Steam' or nvidia drivers can cause all these, to be uninstalled, there is a potential fourth version, which is probably a disaster and I am glad I can not tell how it can be recognized.

Chao!, **bogan.**

---

