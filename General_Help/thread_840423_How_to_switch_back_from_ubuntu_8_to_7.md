---
title: "How to switch back from ubuntu 8 to 7"
date: 2008-06-25
forum: General Help
---

### Post by ubuntios on 2008-06-25
Hi ,

I just Upgrade from ubuntu 7 to 8.
I had a lot of problems for no reason by upgrading to 8, so can anyone knows how to switch back to 7 ?

Thanks.

---

### Post by avtolle on 2008-06-25
You don't "switch back"; you must do a clean install of 7.10 or 7.04.

---

### Post by ubuntios on 2008-06-25
> **avtolle said:**
> You don't "switch back"; you must do a clean install of 7.10 or 7.04.

So I'm going to lose all the configuration/programs, web and ftp server , ssh everything  that I have made?
Also is a dual boot with windows ,I'm going to lose the boot loader?
In a short question , do I Have to do it ALL from the beginning(partitions as well?) ?
It took me too much time  to configure ubuntu 7  on my laptop and the last thing I want is to start from scratch.

Thank you

---

### Post by cariboo on 2008-06-25
Do you have backups of your configuration files?

Jim

---

### Post by jimv on 2008-06-25
You'll lose anything in Ubuntu that you don't back up.  Your partitions will remain the same.

BTW, what problems were you having with 8.04?

---

### Post by Nepherte on 2008-06-25
> **ubuntios said:**
> So I'm going to lose all the configuration/programs, web and ftp server , ssh everything  that I have made?
Also is a dual boot with windows ,I'm going to lose the boot loader?
In a short question , do I Have to do it ALL from the beginning(partitions as well?) ?
It took me too much time  to configure ubuntu 7  on my laptop and the last thing I want is to start from scratch.

Thank you
Yup unfortunately there's no way of reverting the update process. You might as well want to try out a clean of hardy as well then. The upgrade process only works decently if you didn't do a lot of exotic things in 7.10

---

### Post by ubuntios on 2008-06-25
> **cariboo907 said:**
> Do you have backups of your configuration files?

Jim

Hi Jim and thanks for your reply,

No I don't have and I don't know what to back up . Everything that I have done is through tutorials , forums , step by step.After 2 months I manage to configure ubuntu 7 perfect.
A little help  will be appreciated . 

Thanks 

Costas.

---

### Post by Zorael on 2008-06-25
All your user-specific settings are stored in your home directory - the tricky part is the system-wide ones.

I usually only do backups of the following:
[list][*](home folder, of course)
[*]**/etc/X11/xorg.conf**, not to completely replace but for reference to used options
[*]**/etc/samba/smb.conf**
[*]**/etc/network/interfaces**[/list]
The home folder is the large part, naturally, and lets me keep my bookmarks and all those goodies.

---

### Post by ubuntios on 2008-06-25
> **jimv said:**
> You'll lose anything in Ubuntu that you don't back up.  Your partitions will remain the same.

BTW, what problems were you having with 8.04?

The problems that I have are :

Lets start with the display . I have connect the laptop on a 19' tft screen , with 8.04 every time that I restart the laptop I have to go through all the configuration to de-activate the laptop monitor and even after that ,in that new window where you choose the position of the screens , I also need to make some changes in order my graphics to be smooth.Too much trouble for nothing .
  Other thing is that my kiba-doc is gone , I can see running on the services but nowhere dock.I have configure it to keep the minimize windows there , so know when I minimize a windows is gone to the unknown :)
  When I try to run nautilus as root so I can do some changes as admin , it crush and i can do anything.
 Other, when I try to log in , the log in screen repeat it self, I mean that I need to put user pass once trying to do something then comes again the same screen , the second time it continues .
 Compiz problem the windows from elastic became spastic! they behave like when you don't have too much RAM.

And all this in about 2 hours of use 8.04 , I haven't check other things yet , I hope I don't found other monsters in the cave.

I install 8.04 only because i saw something on the ubuntu site about uninstall option , so I thought I have nothing to lose , but I guess I was wrong  :(

---

### Post by bodhi.zazen on 2008-06-25
> **ubuntios said:**
> Hi Jim and thanks for your reply,

No I don't have and I don't know what to back up . Everything that I have done is through tutorials , forums , step by step.After 2 months I manage to configure ubuntu 7 perfect.
A little help  will be appreciated . 

Thanks 

Costas.

OUCH !!!

First, what problems are you having ? It *may* be easier to fix those problems then re-install.

========

Second, lol, don't play on "production" servers. Try these things on a test box or virtualization first.

If everything is working, ask yourself do I really need to update ? On a production server I advise nothing but security updates.

========

If all else fails we need to backup your data / config and re-install. My advice would actually be to try a fresh install of 8.04 (due to LTS). Just because an upgrade was problematic does not mean a fresh install of 8.04 will be a problem for you ...

OK, lets go through an organized approach.

First what servers are you running ?

The config files are in /etc

You should know the location of the data.

Are you running mysql ?

anything else you editied , installed ?

Last, lets make a list of installed packages to make restoration easier :

#######
First, make the list. Open a terminal and enter these commands:

    ```
dpkg --get-selections | grep -v deinstall > ubuntu-files
```

Now you have got a list of all of your installed debs in a fairly small file. Transfer "ubuntu-files" to the insstallation you want to update (flash drive, email it to yourself, backup partition, etc).

Install Ubuntu on the new system.

Once Ubuntu is up and running, copy your ubuntu-files back into your home directory and do the following:

    sudo apt-get update

    sudo apt-get dist-upgrade

    dpkg --set-selections < ubuntu-files

These commmands tell the fresh install of Ubuntu what it needs to be installed. To install the packages .

```
sudo dselect
```

This will open up a dselect session. Type "I" and allow dselect to install of the the packages listed in your ubuntu-files document. When finished, type "Q" and hit the ENTER key to exit dselect.

---

### Post by ubuntios on 2008-06-25
> **bodhi.zazen said:**
> OUCH !!!

First, what problems are you having ? It *may* be easier to fix those problems then re-install.

========

Second, lol, don't play on "production" servers. Try these things on a test box or virtualization first.

If everything is working, ask yourself do I really need to update ? On a production server I advise nothing but security updates.

========

If all else fails we need to backup your data / config and re-install. My advice would actually be to try a fresh install of 8.04 (due to LTS). Just because an upgrade was problematic does not mean a fresh install of 8.04 will be a problem for you ...

OK, lets go through an organized approach.

First what servers are you running ?

The config files are in /etc

You should know the location of the data.

Are you running mysql ?

anything else you editied , installed ?

Last, lets make a list of installed packages to make restoration easier :

#######
First, make the list. Open a terminal and enter these commands:

    ```
 | grep -v deinstall > ubuntu-files
```

Now you have got a list of all of your installed debs in a fairly small file. Transfer "ubuntu-files" to the insstallation you want to update (flash drive, email it to yourself, backup partition, etc).

Install Ubuntu on the new system.

Once Ubuntu is up and running, copy your ubuntu-files back into your home directory and do the following:

    sudo apt-get update

    sudo apt-get dist-upgrade

    dpkg --set-selections < ubuntu-files

These commmands tell the fresh install of Ubuntu what it needs to be installed. To install the packages .

```
sudo dselect
```

This will open up a dselect session. Type "I" and allow dselect to install of the the packages listed in your ubuntu-files document. When finished, type "Q" and hit the ENTER key to exit dselect.


Hoho , we going deep now.

First of all I agree with you about if the update is not good that doesn't mean that the distro is no good.And of course if I need to re-install I will go to 8.04.
Now about the servers it's just for me , nothing fancy.I have them so I can share some files with friends no big deal .You confuse me a little about the other thing you said , if it is working why to update? I don't have to? I don't  miss anything if I don't ? updates are only for those how have problems ? I don't know why I did it I thought it will be better that's all.
I have post some  of my problems if you want to check it out , and of course it will be better to fix them rather reeeeee-install.
  I'm running ProFtp , apache ,ssh ,squed and I thing mysql.The config files are on the etc.
Thats a very nice way to copy the installed package, thanks.  I did the 'dpkg --get-selections' command and I get the list, after the 'grep -v deinstall > ubuntu-file' command and nothing happen, do I have to see anything after that or I have to search for all those files ?

---

### Post by bodhi.zazen on 2008-06-25
Those servers should all be very straight forward to re-install / reconfigure (the second time is easier).

The hard part will be exporting => importing your mysql database.

to answer your questions :

1. Updating packages : Everyone always wants the newest latest greatest, and that is fine. But when you update a package, let alone a distro upgrade, there can be problems, as in your case. If everything is already up, running, and optimized, why upgrade ? Is there some new feature you need?

If you are running a production server you would have procedures and backups in place prior to an upgrade of this nature for exactly the problem you ran into.

2. for "ubuntu-files" you first re-install Ubuntu. You then update 

sudo apt-get update && sudo apt-get upgrade

Then transfer ubuntu-files to the new installation and:

sudo dpkg --set-selections < ubuntu-files #forgot the sudo

Continue with 
[FONT=monospace]
[/FONT]sudo dselect 

...

---

### Post by jimv on 2008-06-25
> **ubuntios said:**
> 
I install 8.04 only because i saw something on the ubuntu site about uninstall option , so I thought I have nothing to lose , but I guess I was wrong  :(

Ahhh!  Another victim of the "You can uninstall Ubuntu" statement on the site.  Unfortunately that only applies if you install from Windows using the Wubi installer.  They really need to mention that.

---

### Post by ubuntios on 2008-06-26
> **jimv said:**
> Ahhh!  Another victim of the "You can uninstall Ubuntu" statement on the site.  Unfortunately that only applies if you install from Windows using the Wubi installer.  They really need to mention that.

Yea , I found it out after, that is possible only from windows.
So if I need to re-install ubuntu should I do it from windows ? because I have already a win box on my laptop.

---

### Post by jimv on 2008-06-26
It's not a bad idea to use the Wubi installer if you want the uninstall option.  I don't think there's a performance hit or anything....though I haven't used it.

---

### Post by ubuntios on 2008-06-26
I'd like to thank everybody here for your help.

I thing I will go for a clean installation of 8.04
And now that I have learned my lesson , I will be very consider before I update a distro.

Regards

---

### Post by bodhi.zazen on 2008-06-26
> **ubuntios said:**
> I'd like to thank everybody here for your help.

I thing I will go for a clean installation of 8.04
And now that I have learned my lesson , I will be very consider before I update a distro.

Regards

It is a hard lesson to learn, but it is true of almost any OS.

The other option is to backup the entire system first with say partimage (or similar). At least then you can restore.

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

On the flip side, as I said, re-installing the second time around is easier.

Also, if you are going to user Ubuntu with any regularity, I suggest you do a traditional install rather they wubi.

---

