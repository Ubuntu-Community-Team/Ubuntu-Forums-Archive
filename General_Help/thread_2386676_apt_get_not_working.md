---
title: "apt get not working"
date: 2018-03-08
forum: General Help
---

### Post by feddozz2 on 2018-03-08
hello
I was trying to install skype on ubuntu 16.04 (i386) but skype comes only for amd64, or so i understood.

I used GDebi to install it. At some point apt got uninstalled and now it is not working anymore. 
I would like to restore everything as it was, nearly a fresh so install...I don't really want to re-install ubuntu


I know I am not giving much useful info. i did it a while ago and i struggle to remember what i did exactly:
Could you please give me some pointers and ill give you more info.
could you please help?

---

### Post by #&amp;thj^% on 2018-03-08
> **feddozz2 said:**
> hello
I was trying to install skype on ubuntu 16.04 (i386) but skype comes only for amd64, or so i understood.

I used GDebi to install it. At some point apt got uninstalled and now it is not working anymore. 
I would like to restore everything as it was, nearly a fresh so install...I don't really want to re-install ubuntu


I know I am not giving much useful info. i did it a while ago and i struggle to remember what i did exactly:
Could you please give me some pointers and ill give you more info.
could you please help?

Show us all of this (Copy and Paste)
```
sudo apt update
```
Paste back using [paste.bin]("https://paste.ubuntu.com/")
Link it here

---

### Post by deadflowr on 2018-03-08
Is dpkg still installed?
Try something like
```
dpkg -l
```
if anything shows dpkg is still there.
Otherwise you're left with 2 choices, really.
1)the painstaking work of trying to compile at least dpkg in order to then install the apt packages.
or
2)reinstall.

---

### Post by feddozz2 on 2018-03-08
No need for paste.bin...I guess
```
~$ sudo apt update 
/usr/bin/apt: 1: /usr/bin/apt: Syntax error: "(" unexpected

```
Thanks for the quick response

---

### Post by monkeybrain20122 on 2018-03-08
Skype is only for 64 bit. There is an old skype 4.3.0.37 for 32 bits [here]("https://skype.en.uptodown.com/ubuntu/download"). But I doubt that it works, or even install and most importantly, I don't know its origin so can't vouch for its safety. I think you can use Skype on Chrome but then Chrome also only supports 64 bit.

---

### Post by #&amp;thj^% on 2018-03-08
> **feddozz2 said:**
> No need for paste.bin...I guess
```
~$ sudo apt update 
/usr/bin/apt: 1: /usr/bin/apt: Syntax error: "(" unexpected

```
Thanks for the quick response

Yuck! :(
Well let's see this:
```
 dpkg -l | grep apt | head -n 1
```

---

### Post by feddozz2 on 2018-03-08
> **deadflowr said:**
> Is dpkg still installed?
Try something like
```
dpkg -l
```
if anything shows dpkg is still there.
Otherwise you're left with 2 choices, really.
1)the painstaking work of trying to compile at least dpkg in order to then install the apt packages.
or
2)reinstall.
[https://pastebin.com/raw/HGxtyfYR](https://pastebin.com/raw/HGxtyfYR)

---

### Post by feddozz2 on 2018-03-08
> **1fallen said:**
> Yuck! :(
Well let's see this:
```
 dpkg -l | grep apt | head -n 1
```

```
 dpkg -l | grep apt | head -n 1
ii  apt:amd64                                  1.2.24                                     amd64        commandline package manager
```

---

### Post by #&amp;thj^% on 2018-03-08
Well I thought we had a chance here but I can't find your version " 1.2.24 " here: [http://security.ubuntu.com/ubuntu/pool/main/a/apt/](http://security.ubuntu.com/ubuntu/pool/main/a/apt/)
Hang tight for a minute till i get it.
This is just recently that this happened right?

---

### Post by feddozz2 on 2018-03-08
I think this key. I have an intel processor...
 at some point I issued this command
```
sudo  dpkg --add-architecture amd64
```

---

### Post by feddozz2 on 2018-03-08
> **1fallen said:**
> Well I thought we had a chance here but I can't find your version " 1.2.24 " here: [http://security.ubuntu.com/ubuntu/pool/main/a/apt/](http://security.ubuntu.com/ubuntu/pool/main/a/apt/)
Hang tight for a minute till i get it.
This is just recently that this happened right?
few weeks ago

---

### Post by #&amp;thj^% on 2018-03-08
> **feddozz2 said:**
> ```
 dpkg -l | grep apt | head -n 1
ii  apt:amd64                                  1.2.24                                     amd64        commandline package manager
```

Ok I found it here I have included a screenshot to help you pick the right package. {snipped due to new information}
Download it to your home directory.
Now i need some time for detailed instructions to try to rebuild it. 
Hang on we are in for a ride.:)
[B]EDIT:See my new post #16
and Note deadflowr's post # 15[/B]

---

### Post by feddozz2 on 2018-03-08
Wow i did not expect responses so quickly. I actually came in just to post the question. I've got to go now. I'll do this later. thanks everyone for the answers!!

---

### Post by #&amp;thj^% on 2018-03-08
Will wait for your return then. :p
EDIT:BTW **Now would be a very important time to have proper back-up's** before proceeding.
And by my looks you have proposed enabled, but no time now to fiddle with that!
Let me know when you have the downloaded "apt.deb" but don't do anything just yet. 
And this:
```
sudo  dpkg --add-architecture amd64
```
should of been:
```
sudo dpkg --add-architecture i386
```
A few weeks in this state is a worrisome addition. (But I'm always optimistic )
But we will see how this all pans out very shortly. :)

---

### Post by deadflowr on 2018-03-08
> **1fallen said:**
> Will wait for your return then. :p
EDIT:BTW **Now would be a very important time to have proper back-up's** before proceeding.
And by my looks you have proposed enabled, but no time now to fiddle with that!
Let me know when you have the downloaded "apt.deb" but don't do anything just yet. 
And this:
```
sudo  dpkg --add-architecture amd64
```
should of been:
```
sudo dpkg --add-architecture i386
```
A few weeks in this state is a worrisome addition. (But I'm always optimistic )
But we will see how this all pans out very shortly. :)

I actually wonder what arch the OP is really on.
I think
```
uname -a
```
should help clear that up.

For the record, amd64 is for all 64-bit processors, amd or intel.
i386 is 32-bit for all, just the same.

Looking at the output from the pastebin link:[https://pastebin.com/raw/HGxtyfYR]("https://pastebin.com/raw/HGxtyfYR")
it looks like this is a 32-bit system.

For what it's worth, adding the amd64 arch to an i386 system should not work, since 32-bit systems cannot run 64-bit programs.
(The opposite does work, as you can run 32-bit programs on a 64-bit system)
Which, really, is all we need to know on why it fails now.

---

### Post by #&amp;thj^% on 2018-03-09
> **deadflowr said:**
> I actually wonder what arch the OP is really on.
I think
```
uname -a
```
should help clear that up.

For the record, amd64 is for all 64-bit processors, amd or intel.
i386 is 32-bit for all, just the same.

Looking at the output from the pastebin link:[https://pastebin.com/raw/HGxtyfYR]("https://pastebin.com/raw/HGxtyfYR")
it looks like this is a 32-bit system.

For what it's worth, adding the amd64 arch to an i386 system should not work, since 32-bit systems cannot run 64-bit programs.
(The opposite does work, as you can run 32-bit programs on a 64-bit system)
Which, really, is all we need to know on why it fails now.
Well with the rapid cross posting yesterday I flat just did not see the pastebin.](*,)
Yeppers deadflowr your absolutely right 32bit. ;)
                                   
As usual there is more here than meets the eye:
```
ii  apt:amd64   1.2.24      amd64   commandline package manager
ii  apt-transport-https:amd64  1.2.24  amd64    https download transport for APT
rc  skype    4.3.0.37-1  i386         Wherever you are, wherever they are
ii  skypeforlinux:amd64  8.15.0.4     amd64        Skype keeps the world talking, for free
ii  zlib1g:amd64 :1.2.8.dfsg-2ubuntu4.1 amd64        compression library - runtime. 
```
Now the risk for breakage has grown significantly, but if the OP is willing to try, and truthfully nothing to lose here.
OP states they don't want to reinstall but, wisdom intact>> a fresh CLEAN install will make for a better experience!
That said, if the OP wants to proceed with all the known risks of total breakage to the system let me know.
BTW I have recovered from worse, but it was my eyes and hands behind the keyboard. (Your mileage** will **vary)
Just to be clear though** "I strongly recommend a Fresh Clean Install"** the time wasted trying to solve this mess and no sure success in the end! (Just makes sense right! :))
And I just can't stress (Point Out) enough **"Now would be a very important time to have proper back-up's before proceeding."**

---

### Post by feddozz2 on 2018-03-10
Right, still thanks for the help. I will consider a fresh install. After all it is not that time consuming. 
The problem is the backup process. its my wife's pc and there is always something she did not tell me to backup and...I should have known...
mind reading/clairvoyance training anyone?
I will keep you posted

---

### Post by #&amp;thj^% on 2018-03-10
> **feddozz2 said:**
> I should have known...
mind reading/clairvoyance training anyone?


Good Luck with the mind reading part. ;) And if you figure that out, write a book>>>I'm sure it will be a Best Seller!:popcorn:
I just wait and ask, you know the old saying "Obey Obey Obey" :D the key to success. ;)
> **feddozz2 said:**
> The problem is the backup process. its my wife's pc and there is always something she did not tell me to backup 
If you have the space on spare USB/Drive copy the Home folder over to it, that should cover it.
Documents, Downloads, Pictures,  Music, Videos, any directory's she may have created in the Home Folder, would be another suggestion as it might be smaller on size.
And on the Install you can choose something else, and **opt out** of formatting the partition. (Should keep your Home Folder intact )
Best of Luck!

---

