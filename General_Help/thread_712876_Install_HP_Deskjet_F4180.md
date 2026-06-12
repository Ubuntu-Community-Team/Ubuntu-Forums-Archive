---
title: "Install HP Deskjet F4180"
date: 2008-03-02
forum: General Help
---

### Post by Stephen Shellard on 2008-03-02
I have been attempting to follow the manual install instructions for this printer at [http://hplip.sourceforge.net/install/manual/distros/ubuntu.html](http://hplip.sourceforge.net/install/manual/distros/ubuntu.html)   I have stumbled at instruction 5: 

[I]Step 5: Run Make

A. This step will compile the HPLIP source.

Important

You want to run make as a regular user, NOT as root.

Enter this command:

make[/I]

I don't don't understand what is meant by the distinction between regular user and root in this case.  I ran the command but the return made it clear that there was no make file to activate. (although I do note a makefile.am (locked) and a makefile.in contained in  the decompressed hlip folder on my desktop.)  

My original source for the approach I am using was an earlier thread:  [http://ubuntuforums.org/showthread.php?t=562964](http://ubuntuforums.org/showthread.php?t=562964)  

I am using: Dapper Drake 6.06

Help appreciated!

---

### Post by pointone on 2008-03-02
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You'll also want to install the "build-essential" package:

```
sudo apt-get install build-essential
```

---

### Post by Stephen Shellard on 2008-03-02
Thank you for taking an interest.  

I have looked at the link you provided with information on root users though really would need more time to make real sense of this, though I think I get the gist;  I have run the script you provided but seem no further forward.  I have once again run the Make command, but to no effect. 

The command preceding the Make command in the set of instructions generates a huge amount of activity but concludes with an error: *configure: error: "cannot find libjpeg support"*   Does this mean I have something further to install?  If so how do I go about this?

The command in question is:  

./configure --enable-network-build --disable-pp-build --enable-fax-build --enable-gui-build --enable-scan-build --enable-doc-build --enable-foomatic-ppd-install --disable-foomatic-drv-install --with-hpppddir=/usr/share/ppd/hpijs/HP --disable-hpijs-only-build --prefix=/usr

---

### Post by pointone on 2008-03-02
You'll need to get configure to succeed before running make.

In general, when configure says you're missing "x", you need to install "x-dev". In this case, install libjpeg-dev with:

```
sudo apt-get install libjpeg-dev
```

---

### Post by Stephen Shellard on 2008-03-03
Thank you again.

Actually, I think some of my problems derive from following a manual install route rather than an "automatic" route which was also I now see offered as an option.  The printer is now working, but I the scanner functions are still inoperative.  At one point in the automatic install process I was asked to activate the universe and multiverse repositories, and whilst the instructions for this seemed straightforward, for some of the options, each time I returned to verify the changes had been made [ to system/administration/software options]  and viewed the Ubuntu 6.06LTS options, the universe and multiverse options remain unchecked despite the fact that I have checked them and selected add and then reloaded as instructed.  Doubtless I have overlooked or misunderstood something.

---

### Post by Stephen Shellard on 2008-03-03
Happy to say scanner is now working via Xsane.  Just slow wittedness I am afraid.  Thanks again for patient assistance.

---

### Post by stchman on 2008-03-03
> **Stephen Shellard said:**
> I have been attempting to follow the manual install instructions for this printer at [http://hplip.sourceforge.net/install/manual/distros/ubuntu.html](http://hplip.sourceforge.net/install/manual/distros/ubuntu.html)   I have stumbled at instruction 5: 

[I]Step 5: Run Make

A. This step will compile the HPLIP source.

Important

You want to run make as a regular user, NOT as root.

Enter this command:

make[/I]

I don't don't understand what is meant by the distinction between regular user and root in this case.  I ran the command but the return made it clear that there was no make file to activate. (although I do note a makefile.am (locked) and a makefile.in contained in  the decompressed hlip folder on my desktop.)  

My original source for the approach I am using was an earlier thread:  [http://ubuntuforums.org/showthread.php?t=562964](http://ubuntuforums.org/showthread.php?t=562964)  

I am using: Dapper Drake 6.06

Help appreciated!

According to the OpenPrinting database that printer works perfectly using the hpijs driver.

---

