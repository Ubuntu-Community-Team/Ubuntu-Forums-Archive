---
title: "sources.list 'E:Malformed line 53 in source list /etc/apt/sources.list (dist parse)'"
date: 2014-02-04
forum: General Help
---

### Post by henryf61 on 2014-02-04
The title is the error message when I try to open the update manager.  

A subsequent error message added "This usually means that your installed packages have unmet dependencies.:

True. My problems started when I tried to install Skype from its website. got an unmet dependencies message and didn't know what to do about it. I have floundered around for a few days and this is where I have gotten to.

I apologize in advance if I'm not following the proper protocal. I have spent serveral hours trying to learn and this is the best I can do.

TIA for any help. 

henryf61

---

### Post by sandyd on 2014-02-04
hi, can you open a terminal window, and type in
```

sudo apt-get -f install
```

---

### Post by Bashing-om on 2014-02-04
henryf61; Hi !

Pleased ya made the thread here.
See sandyd's last .

Also would be enlightening to show us the out put - between code tags - of terminal code:
```

cat -n /etc/apt/sources.list

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We are here to help, in whatever way is needed and in any way we can .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by deadflowr on 2014-02-04
I think that line is typically(if you didn't add any lines to sources.list) the partner repos.
Like above posted by Bashing-OM post the output.

---

### Post by henryf61 on 2014-02-04
Let me combine two replies for more clarity:

Sandyd told me to execute this line of code:   sudo apt-get -f install

Here is the output from that code:

Begin output
Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 linux-headers-3.2.0-31 libubuntuoneui-3.0-1
  linux-headers-3.2.0-31-generic-pae
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
End output

Then Bashing-om suggested another line of code, thus:   cat -n /etc/apt/sources.list

Here is the output:

Begin output
     1	# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
     2	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     3	# newer versions of the distribution.
     4	
     5	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
     6	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    11	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
    17	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
    18	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
    19	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
    27	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
    28	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    29	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    30	
    31	## Uncomment the following two lines to add software from the 'backports'
    32	## repository.
    33	## N.B. software from this repository may not have been tested as
    34	## extensively as that contained in the main release, although it includes
    35	## newer versions of some applications which may provide useful features.
    36	## Also, please note that software in backports WILL NOT receive any review
    37	## or updates from the Ubuntu security team.
    38	# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
    39	# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
    40	
    41	## Uncomment the following two lines to add software from Canonical's
    42	## 'partner' repository.
    43	## This software is not part of Ubuntu, but is offered by Canonical and the
    44	## respective vendors as a service to Ubuntu users.
    45	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
    46	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
    47	
    48	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    49	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    50	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    51	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    52	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    53	deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
    54	deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
    55	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
End output

I hope this helps to find a fix.

TiA,
henryf61

---

### Post by deadflowr on 2014-02-04
Do you see how the line for the old partners for lucid looks.
(line 45)
Change the line for the precise to look like that
Your old line
```
[COLOR=#000000]53    deb [/COLOR][http://archive.canonical.com/precise](http://archive.canonical.com/precise)[COLOR=#000000] partner[/COLOR]
```
Try changing it to
```
[COLOR=#000000]53    deb [/COLOR][http://archive.canonical.com/ubuntu precise]("http://archive.canonical.com/precise")[COLOR=#000000] partner[/COLOR]
```
To do so open a teminal and run
```
gksu gedit /etc/apt/sources.list
```
enter your password when it asks, then go to line 53 and make the changes.
then save and close.
then re-run
```
sudo apt-get update
```

Sidenote: Change the line 54 the same way.

---

### Post by Bashing-om on 2014-02-04
henryf61; Hey ;

Are you comfortable editing files ?

Always as Standard Operating Procedure make a back up of any file that you are going to edit: This case:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-bak

```

edit the file:
```

gksudo gedit /etc/apt/sources.list

```
Make lines 53 and 54 to this:
> 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

adding "ubuntu" to "/archive.canonical.com/" to make a correct URL

Save the file and exit back to terminal:
Terminal codes:
```

sudo apt-get update
sudo apt-get upgrade

```

All good now ? Please advise.

[INDENT][INDENT]should workie great and last long time
[/INDENT][/INDENT]

---

### Post by henryf61 on 2014-02-04
I did everything that Deadflowr and Bashing-om recommended, down to but exclluding 

sudo apt-get upgrade

I did the update and software manager ran fine and installed many updates.  I hesitated doing the upgrade because I wasn't sure what it might do. I am running Ubuntu 12.04 LTS and am content to stay with it. Will the upgrade command take me to a later version of Ubuntu or not? If it leaves me in 12.04, I will be glad to run the command.

Thanks very much to both of you and the others who have helped me with this problem. I will sleep much better tonight. <grin>

With all my gratitude,

Henryf61

---

### Post by deadflowr on 2014-02-04
No, running the dist-upgrade command won't change the version of Ubuntu.
It'll only do the actual updating of the system

The apt-get update command updates the package lists that are available for you.
The apt-get upgrade and apt-get dist-upgrade do the package updating.

Hope that makes sense.

Basically when you run the update manager and select the install option when new updates come, you're running the upgrade or dist-upgrade command.

If you wanted to actually upgrade to a new version you would run
```
sudo do-release-upgrade
```

But it sounds like you're content, so don't bother.

There are differences between upgrade and dist-upgrade.
From man apt-get
>  upgrade           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.


       dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. The dist-upgrade
           command may therefore remove some packages. The
           /etc/apt/sources.list file contains a list of locations from which
           to retrieve desired package files. See also apt_preferences(5) for
           a mechanism for overriding the general settings for individual
           packages.




Hope that helps.

Personally, I run the update manager unless something terrible is going on.

---

### Post by Bashing-om on 2014-02-04
henryf61; Good !

OK, the "upgrade" command will only update the packages on your system to what is current. It will not version upgrade you to a newer version ! Though you may do so with a somewhat similar terminal command - not included so as not to confuse -.

Suffice it to say - do that last command at this time - to take advantage of all the updates and security patches that have been done since the system was last updated.

The neat thing about doing things from terminal, one get to see everything that the system is doing, or going to do.

do the:
```

sudo apt-get upgrade

```
And see this for yourself. The system will tell you what it is going to do, give you an opportunity to review these changes, and await you to tell it to "DO IT !" <do you want to continue ? y/n >. Not needed, but I always pay attention to what is going to be done, just in the event that something should result in a bad kind of way, I have some idea of what where and why. Many pay no heed to this advisory. Which I in no way advocate.

all in the 
[INDENT][INDENT]care and feeding
[INDENT][INDENT][INDENT]of your ubuntu
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by henryf61 on 2014-02-04
Again my thanks to both of you. I ran the upgrade command and it reported that no actions were needed. So it looks like my system is in great shape.

Now I think I am supposed to mark this thread "solved" or some such. It looks like I will have to come back one more time to learn how to do that.

Thanks,
henryf61
P.S. This exercise has been difficult for me but has restored my faith in Ubuntu.

---

### Post by oldos2er on 2014-02-04
> **henryf61 said:**
> Now I think I am supposed to mark this thread "solved" or some such. 

Find the Thread Tools drop-down menu at the top of the page; 'Mark thread as Solved' is there.

---

