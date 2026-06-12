---
title: "Skype trouble!!"
date: 2005-09-12
forum: General Help
---

### Post by unduality on 2005-09-12
[COLOR=Red]If you want to avoid to go through all hell that i had to in order to get skype working install "lsb" and "lsb-base" with apt before installing skype. Then all will work exept that the colours in skype are really wierd. Enjoy![/COLOR]

Hallo and HELP!

In the obuntu guide (5 .04) at.... 

[http://ubuntuguide.org/#skype](http://ubuntuguide.org/#skype)

...there is instructions on how to install skype. 

Like this...

 
[I]sudo apt-get install libqt3c102-mt
wget -c [http://frankandjacq.com/ubuntuguide/skype_1.2.0.11-1_i386.deb](http://frankandjacq.com/ubuntuguide/skype_1.2.0.11-1_i386.deb)
sudo dpkg -i skype_1.2.0.11-1_i386.deb[/I]

However it do not work for me because "libqt3c102-mt" doesnt exist in the reposiptory and and skype wont start.

Anyone knows how to fix this??

Take care/
Björn!

---

### Post by Leif on 2005-09-13
it is in the repos. enable the extra repos as outlined in ubuntuguide.org

---

### Post by jugalu81 on 2005-10-11
I had the same problem, the problem is that the "libqt3c102-mt" required by Skype is a newer version.

But I downloaded the 

"Static binary tar.bz2 with Qt 3.2 compiled in" 

from th download page of Skype: 

[http://www.skype.com/products/skype/linux/](http://www.skype.com/products/skype/linux/)

and I`m running Skype very well.

---

### Post by Cathbard on 2005-10-12
I'm downloading that now to try (slowly, slowly, I don't think I'm alone)

The actual error when installing skype from the debian package is:

skype:
  Depends: libqt3c102-mt (>=3:3.3.3.2) but 3:3.3.3-7ubuntu3 is to be installed

So my question is: what's the deal with the ubuntu3 tag on that? This is the one that is on my system and the number is higher than the one skype wants. I'm confused:confused: 
Is there a flag using dpkg that will allow/force it to work with this libqt3c102?   ie, should it work with 3:3.3.3-7ubuntu3 if installed correctly and how would one do it?

---

### Post by Cathbard on 2005-10-12
This worked!! 

$sudo apt-get install fakeroot alien
$fakeroot alien --to-tgz skype_1.2.0.17-1_i386.deb
$sudo apt-get install libqt3-mt
$fakeroot alien --to-deb skype-1.2.0.17.tgz
$sudo dpkg -i skype_1.2.0.17-2_all.deb

(from [http://ubuntuforums.org/showpost.php?p=376677&postcount=41](http://ubuntuforums.org/showpost.php?p=376677&postcount=41))

---

### Post by Cathbard on 2005-10-12
Strange occurence........My Skype password is rejected when I start Skype as a user. If I run it as root my password is accepted. I get the following when I start Skype regardless if i type skype or sudo skype:

_IceTransPTSOpenClient: failed to open /tmp/.ICE-unix/7816
_IceTransISCOpenClient: Protocol is not supported by a ISC connection
_IceTransSCOOpenClient: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for local/ubuntubox:/tmp/.ICE-unix/7816

It then runs fine as root. It takes a long time to start and rejects the password as user. I checked the permissions on /tmp/.ICE-unix/7816 and everybody had full access to it.

Ideas anybody?

---

### Post by PeaceMessenger on 2005-10-13
I'm a noob running Breezy.

I am having a similar problem.  I have all the repositories enabled (that are listed), with the possible exceptions of the Breezy Backports- which I tried to check but there was some error about not being able to connect to those.... I tried to install Skype according to the instructions at [https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto)

However, I also get stuck with the error:
skype:
Depends: libqt3c102-mt (>=3:3.3.3.2) but 3:3.3.3-7ubuntu3 is to be installed but is not installable.

Cathbard, I see you found a workaround, almost anyway-  but since I'm a noob- I don't understand how to do it.  I've figured out how to use the Synaptic interface to get software, but I don't know the first place to start to type in your work around.  Could you take the time to gently walk me through it?

---

### Post by Cathbard on 2005-10-14
To try this work around all you need to do is start a terminal from the accessories menu and start typing those commands. The problem is that the qt libraries are all changed. This gets around that.
If you need more info follow the link I provided to the thread I got it from. Talk to the driver not the donkey ;)

---

### Post by eburcat on 2005-10-14
I downloaded from [http://www.skype.com/products/skype/linux/]("http://www.skype.com/products/skype/linux/") the 'Debian package' (the file's name is skype_1.2.0.17-1_i386.deb) to home. From there I ran the commands:

```

sudo apt-get install fakeroot alien
fakeroot alien --to-tgz skype_1.2.0.17-1_i386.deb
sudo apt-get install libqt3-mt
fakeroot alien --to-deb skype-1.2.0.17.tgz
sudo dpkg -i skype_1.2.0.17-2_all.deb

```

But when I run skype I get the message:
skype: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I have also tried to follow the instructions on the site:
dowload the files: skype-1.2.0.17.tar.bz2, skype_staticQT-1.2.0.17.tar.bz2, open them using
```

tar xjvf skype-version.tar.bz2

```
Then entering the directory that was created, and running skype.
Same result.

Any ideas?
Thanks,
Eitan.

p.s. I'm a newbe, so this might be a stupid mistake I do here...

---

### Post by Cathbard on 2005-10-15
I was using hoary when I made that post.....go to this thread:

[http://ubuntuforums.org/showthread.php?t=68283](http://ubuntuforums.org/showthread.php?t=68283)

---

### Post by eburcat on 2005-10-15
When I used the synaptic package manager to upgrade my skype, it offered to upgrade the  libstdc++.so.5 library. After installation skype started to work.

Thanks,
Eitan.

---

### Post by Cathbard on 2005-10-16
I have installed skype onto my fresh Breezy installation. I had trouble with the deb on that thread so I did this and it worked a treat:

download the mandriva rpm from skype.

[http://www.skype.com/go/getskype-linux-mdk]("http://www.skype.com/go/getskype-linux-mdk")


then in a terminal session type:

```
sudo apt-get install libqt3-mt
```     *if you haven't already

now navigate to the folder where you stored your downloaded skype rpm and type:

```
fakeroot alien --to-deb skype-1.2.0.17-mdr.i586.rpm
sudo dpkg -i skype_1.2.0.17-1_i386.deb
```

I am assuming that you have fakeroot alien installed. If not type:
```
sudo apt-get install fakeroot alien
``` and try again

You may also want to visit this thread if you sound screws up after you make a call
[http://www.ubuntuforums.org/showthread.php?t=32063]("http://www.ubuntuforums.org/showthread.php?t=32063")


Goodluck

---

### Post by aev on 2005-10-25
hmmm... I tried all of the above.. But for me it works only the text chat. I have skype-out service and when I dial the number skype freezes. Then I have to kill the process. :???: Anybody else with similar problem? could it be a sound device problem?:confused:

---

### Post by aev on 2005-10-27
well... after the today's system update i was able to make a call. :) still not sure what was the obstacle before.

---

### Post by aev on 2005-10-31
[QUOTE=Cathbard]This worked!! 

$sudo apt-get install fakeroot alien
$fakeroot alien --to-tgz skype_1.2.0.17-1_i386.deb
$sudo apt-get install libqt3-mt
$fakeroot alien --to-deb skype-1.2.0.17.tgz
$sudo dpkg -i skype_1.2.0.17-2_all.deb

(from [http://ubuntuforums.org/showpost.php?p=376677&postcount=41](http://ubuntuforums.org/showpost.php?p=376677&postcount=41))[/QUOTE]


u r the man.. thanks a lot.:)

---

### Post by paddy2706 on 2005-11-07
or you just download my repackaged deb from the original deb, with just changed dependencies: [http://www.patrick-brueckner.de/?download=skype_1.2.0.18-1_i386-libqt3-mt.deb](http://www.patrick-brueckner.de/?download=skype_1.2.0.18-1_i386-libqt3-mt.deb)

---

