---
title: "Unable to install anything manually"
date: 2015-11-06
forum: General Help
---

### Post by cdl-w on 2015-11-06
I am fairly new to Ubuntu and to Linux as well for that matter.  I have been trying to modify my themes and icons etc to make it more interesting and I am having major issues.  I am doing everything that the tutorials on the sites tell me (including mods that are on the ubuntu site so I know they are accurate).  I use the sudo add-apt-repository ppa: command to retrieve the information then use the sudo apt-get update to update and then when I do the sudo apt-get install command to install the packages it gives me the error "E: Unable to locate package ...".  It doesnt seem to matter what i am trying to install. It could be a simple icon or font package or a game or other application, I cannot get it to install anything at all.:mad:

---

### Post by deadflowr on 2015-11-06
Posting the output of the all commands you ran helps.
 (use code tags, please)

---

### Post by buzzingrobot on 2015-11-06
Also, if a PPA does not have a package available for your version of Ubuntu, then you will likely see that "unable to locate..." .

Every PPA has a page on launchpad.net.  If you search on the PPA's name, you'll find the right link. You can set a filter there to see which packages offered by that PPA are available for your release of Ubuntu.  Look for the dropdown menu under "Overview of published packages".

If you happen to be using 15.10, many themes, etc., aren't available for it yet.

---

### Post by matt_symes on 2015-11-06
Hi

Lots more information is needed to help you here.

The advice you've been given to install software from a PPA is correct and the two previous replies detail what you need to do to get help and why those commands may be failing to locate packages.

So to start with, please tell us which version of Ubuntu you are using.

```
cat /etc/lsb-release
```

and the desktop you are using.

```
echo $DESKTOP_SESSION
```

and please give us an example of a theme you are trying to install and from which repository you are trying to install it from.

My money's on buzzingrobot though. 

I suspect you have 15.10 installed and the PPAs you have installed have not been updated to 15.10 yet as it's only just been released.

Kind regards

---

### Post by cdl-w on 2015-11-08
Thank you I am using Ubuntu version 15.10. I think that that may be my issue.  It seems with further research that 15.04 is the most recent widely compatible release of Ubuntu.  Would you recommend me downgrading to a lower version for a while until 15 has been out fora while? It seems that Ubuntu is growing very quickly I am already seeing chatter online about Ubuntu 16.  Is this going to cause a big problem in compatibility for people?

Edit: I just went to where I was attempting to get the theme and noticed that it is indeed a theme for 15.10. Below is the link to the website and the instructions.

[http://www.noobslab.com/2015/11/macbuntu-1510-transformation-pack-for.html](http://www.noobslab.com/2015/11/macbuntu-1510-transformation-pack-for.html)

---

### Post by matt_symes on 2015-11-08
Hi

> **cdl-w said:**
> Thank you I am using Ubuntu version 15.10. I think that that may be my issue.  It seems with further research that 15.04 is the most recent widely compatible release of Ubuntu.  Would you recommend me downgrading to a lower version for a while until 15 has been out fora while? It seems that Ubuntu is growing very quickly I am already seeing chatter online about Ubuntu 16.  Is this going to cause a big problem in compatibility for people?

It takes a while for PPAs to be updated from version to version - anything from a week to a couple of months. Sometimes they never get upgraded at all. You just have to wait and see.

If you're happy with 15.10 then stay on it for the nine months it's supported and then upgrade.

There is much chatter about 16.04 because it's the next LTS (long term support) release. They come along every couple of years and are supported for 5 years and not 9 months. 

I am still on the last LTS release (14.04) and will be upgrading to 16.04 a couple of months after it's out. I give time for bug fixes to be ironed out as i like my main OS to be stable.

You'll be able to upgrade from 15.10 to 16.04 when it comes out or you can install a new (not upgraded from 15.10) version of 16.04.

> Edit: I just went to where I was attempting to get the theme and noticed that it is indeed a theme for 15.10. Below is the link to the website and the instructions.

[http://www.noobslab.com/2015/11/macbuntu-1510-transformation-pack-for.html](http://www.noobslab.com/2015/11/macbuntu-1510-transformation-pack-for.html)

If you like it then install the theme :)

Kind regards

---

### Post by cdl-w on 2015-11-09
Thank you for the information.  I posted the link to the theme page because that is the theme that i have been trying to install and i am getting the original error that i put in my first post with these packages.  They say it is supposed to be upgraded for 15.10 but none of the packages are loading. I still am getting the "Unable to load package ...." error

---

### Post by matt_symes on 2015-11-09
Hi

> **cdl-w said:**
> Thank you for the information.  I posted the link to the theme page because that is the theme that i have been trying to install and i am getting the original error that i put in my first post with these packages.  They say it is supposed to be upgraded for 15.10 but none of the packages are loading. I still am getting the "Unable to load package ...." error

Interestingly enough, I cannot install the themes either on 14.04.

I've added to repository and updated, but a search for the package is showing zip; along with attempted installation as shown below.

```

matthew-laptop:/home/matthew:2 % sudo apt-get install macbuntu-ithemes-v6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package macbuntu-ithemes-v6
matthew-laptop:/home/matthew:2 
```

I'll see if i can find out why.

Kind regards

---

### Post by matt_symes on 2015-11-09
Hi

Well I've looked at the repository and the packages for both macbuntu-ithemes-v6 and macbuntu-icons-v6 there for Wily (15.10), in the pool section. They are also referenced in the Packages file; the two compressed files and the uncompressed one for both x86 and x64.

So it looks like they should be available to you.

I could not install them because they are only available for Wily (15.10) and Wily only.

So are you sure you are on Wily ? 

I know it's a daft question but can we check please; just to be 110% sure.

Please post the output of this command after copying and pasting it into the terminal.

```
cat /etc/lsb-release && echo $DESKTOP_SESSION
```

Kind regards

---

### Post by matt_symes on 2015-11-09
Hi

I just installed Wily into a VM and installed the theme.

These were my steps.

```

matthew@matthew-Standard-PC-i440FX-PIIX-1996:~$ cat /etc/lsb-release && echo $DESKTOP_SESSION
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.10
DISTRIB_CODENAME=wily
DISTRIB_DESCRIPTION="Ubuntu 15.10"
ubuntu
matthew@matthew-Standard-PC-i440FX-PIIX-1996:~$ sudo add-apt-repository ppa:noobslab/themes
[sudo] password for matthew: 
 themes uploaded on http://www.NoobsLab.com PPA
For exact theme version and support visit on site and see themes page
 More info: https://launchpad.net/~noobslab/+archive/ubuntu/themes
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp_h5j4own/secring.gpg' created
gpg: keyring `/tmp/tmp_h5j4own/pubring.gpg' created
gpg: requesting key F59EAE4D from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp_h5j4own/trustdb.gpg: trustdb created
gpg: key F59EAE4D: public key "Launchpad PPA for NoobsLab" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
matthew@matthew-Standard-PC-i440FX-PIIX-1996:~$ sudo apt-get -qq update
matthew@matthew-Standard-PC-i440FX-PIIX-1996:~$ sudo apt-get -qq install macbuntu-icons-v6 macbuntu-ithemes-v6
Selecting previously unselected package gtk2-engines-pixbuf:amd64.
(Reading database ... 175355 files and directories currently installed.)
Preparing to unpack .../gtk2-engines-pixbuf_2.24.28-1ubuntu1_amd64.deb ...
Unpacking gtk2-engines-pixbuf:amd64 (2.24.28-1ubuntu1) ...
Selecting previously unselected package gtk3-engines-unico:amd64.
Preparing to unpack .../gtk3-engines-unico_1.0.3+14.04.20140109-0ubuntu1_amd64.deb ...
Unpacking gtk3-engines-unico:amd64 (1.0.3+14.04.20140109-0ubuntu1) ...
Selecting previously unselected package macbuntu-icons-v6.
Preparing to unpack .../macbuntu-icons-v6_3.16~wily~NoobsLab.com_all.deb ...
Unpacking macbuntu-icons-v6 (3.16~wily~NoobsLab.com) ...
Selecting previously unselected package macbuntu-ithemes-v6.
Preparing to unpack .../macbuntu-ithemes-v6_3.16~wily~NoobsLab.com_all.deb ...
Unpacking macbuntu-ithemes-v6 (3.16~wily~NoobsLab.com) ...
Setting up gtk2-engines-pixbuf:amd64 (2.24.28-1ubuntu1) ...
Setting up gtk3-engines-unico:amd64 (1.0.3+14.04.20140109-0ubuntu1) ...
Setting up macbuntu-icons-v6 (3.16~wily~NoobsLab.com) ...

keep visit on www.NoobsLab.com

Setting up macbuntu-ithemes-v6 (3.16~wily~NoobsLab.com) ...

keep visit on www.NoobsLab.com

matthew@matthew-Standard-PC-i440FX-PIIX-1996:~$ 
```

It installed correctly although i have not switched to it yet.

```
matthew@matthew-Standard-PC-i440FX-PIIX-1996:~$ dpkg -l macbuntu-icons-v6 macbuntu-ithemes-v6
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version            Architecture       Description
+++-===========================-==================-==================-===========================================================
ii  macbuntu-icons-v6           3.16~wily~NoobsLab all                MacBuntu Icons & cursors uploaded on NoobsLab.com PPA
ii  macbuntu-ithemes-v6         3.16~wily~NoobsLab all                MacBuntu Themes available on NoobsLab.com PPA
matthew@matthew-Standard-PC-i440FX-PIIX-1996:~$
```

Kind regards

---

### Post by cdl-w on 2015-12-03
I want to thank everyone for their help.  I went back to the link a couple weeks later and about 4 15.10 software updates later (Dont know if that made a difference to my problem) and everything installed smoothly.  I really did appreciate everyone’s due diligence and thank you again. 

Now if someone can tell me why my media streaming keeps randomly disconnecting from my PS4 all is fixed on my end hahahaha:guitar:

---

