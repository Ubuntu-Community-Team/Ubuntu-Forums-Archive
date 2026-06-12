---
title: "Slow boot again and udate problems."
date: 2017-01-23
forum: General Help
---

### Post by aviator1 on 2017-01-23
Hello All:

About 3 weeks ago, my boot up time went from 30 seconds to 120 seconds. I also noticed that my email program, Thunderbird looked different when I opened it. the folders were a light green and the fonts were much smaller. Almost like I had changed screen resolution. 

The issues seemed to resolve themselves.

The I began getting an error during updates.

My internet connection is fine.

 ```
    Error 1 Failed to download repository information

 
 
 Check your internet connection
 
 
 If I click OK, I get a download, but a warning that some software could not be checked for updates.
 
 
 I do get some type of updates, which can be installed.
 
 
 Error 2 Failure to download extra data files

 
 
 The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.
 
 
 ttf-mscorefonts-installer
 
 
 The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection. 
```

I'm a long time user, but not well versed in Ubuntu commands.

Any help would be greatly appreciated.

Regards.

---

### Post by #&amp;thj^% on 2017-01-23
This has been going on for sometime now Update on Dec 10: A better/easier workaround is to download the 3.6 version of ttf-mscorefonts-installer from Debian. Double clicking and installing that package with gnome's software center (and probably also ubuntu's software center) works perfectly. Or, if you would like to run some code, here you go:
```
wget http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb -P ~/Downloads
```
will download the package to your Downloads folder, and
```
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
```
Will install it from that Folder.
Now you can check again with:
```
sudo apt update
sudo apt upgrade
```

---

### Post by aviator1 on 2017-01-23
I followed instructions, and nothing changed.

Still very slow boot. When the desktop does show up, my cursor is a black "X" for about 15 seconds. If I open Thunderbird, it is still odd looking.

I can close Thunderbird and wait about 20 seconds and it is OK.

Running the updater, still gives me the "Failed to download repository Information-check your internet connection"

Any other suggestions about the slow boot or updater issues?

Thanks very much for your help.

---

### Post by #&amp;thj^% on 2017-01-23
> **aviator1 said:**
> I followed instructions, and nothing changed.

Still very slow boot. When the desktop does show up, ,y cursor is a black "X" for about 15 seconds. 

Thanks very much for your help.
My suggestions were for the update error only...sorry i was not clear on that.
> **aviator1 said:**
> 
Still very slow boot. When the desktop does show up, ,y cursor is a black "X" for about 15 seconds.

To find what is hanging up the startup time post back the return of this:
```
systemd-analyze blame
```
> **aviator1 said:**
> If I open Thunderbird, it is still odd looking.

I can close Thunderbird and wit about 20 seconds and it is OK.


I am not able to help here...sorry.(But could be related to Video Driver)
Can you show the whole output of the update error.

---

### Post by aviator1 on 2017-01-23
Here it is.

```
dave@dave-desktop:~$ systemd-analyze blame
      1min 783ms upower.service
          7.244s NetworkManager-wait-online.service
          1.071s dev-sda6.device
           248ms winbind.service
           231ms nmbd.service
           190ms smbd.service
           188ms samba-ad-dc.service
           182ms lightdm.service
           147ms ModemManager.service
           145ms apparmor.service
           143ms accounts-daemon.service
           141ms NetworkManager.service
           135ms grub-common.service
           121ms gpu-manager.service
           118ms networking.service
           107ms apport.service
           106ms console-setup.service
           104ms irqbalance.service
            93ms systemd-udev-trigger.service
            76ms keyboard-setup.service
            75ms systemd-logind.service
            74ms speech-dispatcher.service
            71ms thermald.service
lines 1-23
```

Please clarify "Can you show the whole output of the update error." ?

Thank you.

---

### Post by #&amp;thj^% on 2017-01-23
Humm? I don't see anything there...I also should have told you to use the page down and page up options to show more... but i think this will tell us a little more.
```
systemd-analyze critical-chain
```
Mine Looks like this:
```
$ systemd-analyze critical-chain
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @22.925s
&#9492;&#9472;multi-user.target @22.925s
  &#9492;&#9472;pacman-init.service @6.833s +16.091s
    &#9492;&#9472;haveged.service @6.147s
      &#9492;&#9472;basic.target @6.125s
        &#9492;&#9472;sockets.target @6.125s
          &#9492;&#9472;dbus.socket @6.125s
            &#9492;&#9472;sysinit.target @6.115s
              &#9492;&#9472;systemd-update-utmp.service @5.937s +177ms
                &#9492;&#9472;systemd-tmpfiles-setup.service @4.840s +1.085s
                  &#9492;&#9472;systemd-journal-flush.service @4.597s +227ms
                    &#9492;&#9472;systemd-journald.service @1.414s +3.167s
                      &#9492;&#9472;systemd-journald.socket @1.345s
                        &#9492;&#9472;-.slice @1.003s

```

Paste that back here along with the results of this please.
```
sudo apt update
```

---

### Post by aviator1 on 2017-01-23
Here is the first part.
```
   dave@dave-desktop:~$ systemd-analyze critical-chain
 The time after the unit is active or started is printed after the "@" character.
 The time the unit takes to start is printed after the "+" character.
 
 
 graphical.target @9.163s
 &#9492;&#9472;multi-user.target @9.163s
   &#9492;&#9472;[COLOR=#ff3333]smbd.service @8.972s +190ms[/COLOR]
 [COLOR=#ff3333]    &#9492;&#9472;nmbd.service @8.725s +231ms[/COLOR]
       &#9492;&#9472;network-online.target @8.710s
         &#9492;&#9472;[COLOR=#ff3333]NetworkManager-wait-online.service @1.466s +7.244s[/COLOR]
 [COLOR=#ff3333]          &#9492;&#9472;NetworkManager.service @1.315s +141ms[/COLOR]
             &#9492;&#9472;dbus.service @1.288s
               &#9492;&#9472;basic.target @1.276s
                 &#9492;&#9472;sockets.target @1.276s
                   &#9492;&#9472;[COLOR=#ff3333]snapd.socket @1.267s +5ms[/COLOR]
                     &#9492;&#9472;sysinit.target @1.267s
                       &#9492;&#9472;swap.target @1.267s
                         &#9492;[COLOR=#ff3333]&#9472;dev-disk-by\x2duuid-80d61814\x2dfc43\x2d4c38\x2db772\x[/COLOR]
                           &#9492;&#9472;dev-disk-by\x2duuid-80d61814\x2dfc43\x2d4c38\x2db772
 lines 1-18/18 (END)
```

And the results of the update.
```
dave@dave-desktop:~$ sudo apt update
[sudo] password for dave: 
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease                     
Hit:3 http://dl.google.com/linux/chrome/deb stable Release                     
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Ign:5 http://www.openprinting.org/download/printdriver/debian lsb3.2 InRelease 
Get:6 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Ign:7 http://archive.canonical.com/ubuntu precise InRelease                    
Hit:8 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial InRelease    
Hit:9 http://www.openprinting.org/download/printdriver/debian lsb3.2 Release   
Hit:11 http://archive.canonical.com xenial InRelease                           
Ign:12 http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu xenial InRelease
Hit:13 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease          
Hit:15 http://archive.canonical.com/ubuntu precise Release                     
Err:16 http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu xenial Release
  404  Not Found
Get:18 http://security.ubuntu.com/ubuntu xenial-security/main Sources [55.8 kB]
Get:19 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [202 kB]
Get:20 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages [196 kB]
Get:21 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [84.9 kB]
Get:22 http://security.ubuntu.com/ubuntu xenial-security/universe Translation-en [38.9 kB]
Reading package lists... Done                                       
W: http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/Release.gpg: Signature by key F8897B6F00075648E248B7EC24CBF5474CFD1E2F uses weak digest algorithm (SHA1)
E: The repository 'http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: http://archive.canonical.com/ubuntu/dists/precise/Release.gpg: Signature by key 630239CC130E1A7FD81A27B140976EAF437D05B5 uses weak digest algorithm (SHA1)
dave@dave-desktop:~$ 


```

Anything you see amiss?

Thanks.

---

### Post by #&amp;thj^% on 2017-01-23
All these Are warnings: (And can safely be ignored for now)
> 
W: [http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/Release.gpg:](http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/Release.gpg:) Signature by key F8897B6F00075648E248B7EC24CBF5474CFD1E2F uses weak digest algorithm (SHA1)
W: [http://archive.canonical.com/ubuntu/dists/precise/Release.gpg:](http://archive.canonical.com/ubuntu/dists/precise/Release.gpg:) Signature by key 630239CC130E1A7FD81A27B140976EAF437D05B5 uses weak digest algorithm (SHA1)
Here is what is happening with update errors:```

E: The repository 'http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
```
This one more than the rest though:
> [http://archive.canonical.com/ubuntu/dists/precise/Release.gpg:](http://archive.canonical.com/ubuntu/dists/precise/Release.gpg:) Signature by key 630239CC130E1A7FD81A27B140976EAF437D05B5 uses weak digest algorithm (SHA1)
N: See apt-secure(8) manpage for repository creation and user configuration details.
What is that PPA for?
When I try to see I get this: The requested URL /ubuntu/dists_**/precise/**_Release.gpg: was not found on this server.

---

### Post by aviator1 on 2017-01-23
I have no idea what the "ppa" is for.

How would I correct the "no release file" issue?

---

### Post by #&amp;thj^% on 2017-01-23
Well lets have a look at them then:
```
gedit /etc/apt/sources.list
```
Paste back here again...Thanks

---

### Post by aviator1 on 2017-01-23
Here it is. I really appreciate your help.

```
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

deb http://archive.canonical.com/ xenial partner
deb-src http://archive.canonical.com/ xenial partner
deb http://www.openprinting.org/download/printdriver/debian/ lsb3.2 contrib # disabled on upgrade to xenial
```

---

### Post by #&amp;thj^% on 2017-01-23
I would comment these two out via:
```
sudo -H gedit /etc/apt/sources.list 
```
So they now look like this:
```
 
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner
```
That has not seen any activity since: 18-Feb-2016 16:50     
And I still wonder about this one "**deb [http://www.openprinting.org/download/printdriver/debian/](http://www.openprinting.org/download/printdriver/debian/) lsb3.2 contrib # disabled on upgrade to xenial**"
I guess we will see if it fly's.
And just to check once more to see if things are in a better state.
```
sudo apt update
```
Now you may still see this "Signature by key xxx xxx 48E248B7EC24CBF5474CFD1E2F uses weak digest algorithm (SHA1)"
Or even another key value that dose not comply with the new algorithm (SHA2)
And again there is nothing you can do on your end to fix this....As this lies in hands of that maintainer of that Repo or PPA.

---

### Post by aviator1 on 2017-01-23
Need a little help.

I ran 
sudo -H gedit /etc/apt/sources.list

Do I simply edit the ones listed below you mentioned in terminal, or do I have to do something else?

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

Thanks.

---

### Post by #&amp;thj^% on 2017-01-23
Yes Sir.. just edit those two as you see them with the "#" in front.
And just to be sure....  save the file after the edit.

---

### Post by aviator1 on 2017-01-23
Here's what I see now. I saved and rebooted. There are no changes. Still slow boot and a delay before programs look right.

Any ideas?

Thanks for your help


```
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

deb http://archive.canonical.com/ xenial partner
deb-src http://archive.canonical.com/ xenial partner
deb http://www.openprinting.org/download/printdriver/debian/ lsb3.2 contrib # disabled on upgrade to xenial
```

---

### Post by #&amp;thj^% on 2017-01-23
Lets try and stay focused on one problem only....Best to post another thread topic on the other problems.
What we are trying to fix here and now...is the update problem....so are there now any errors from:
```
sudo apt update
```
Now not to get off topic here...but the slow boot shows a vague hint with:
```
1min 783ms upower.service
```
That will be the big hill to climb to find the cause of that...could be a update that threw it off...or even a new update coming in that might fix that.
Heaven forbid...it could even be a sign of aging hardware.

---

### Post by aviator1 on 2017-01-23
I agree about solving 1 problem at a time. 

Also, as I mentioned earlier, I had these same issues a few weeks ago, but they cured themselves. I have had updates since then.

Hardware is less than 2 years old, and has been working fine otherwise. I think you had responded to a post I made about RAM not being used very much though.

I ran sudo apt update again.

Do you want me to post the results? There was no change in the boot process after I ran that.

Thanks for your help.

---

### Post by aviator1 on 2017-01-23
Here's the latest.

dave@dave-desktop:~$ sudo apt update
[sudo] password for dave: 
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                     
Hit:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Ign:5 [http://www.openprinting.org/download/printdriver/debian](http://www.openprinting.org/download/printdriver/debian) lsb3.2 InRelease 
Hit:6 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) xenial InRelease    
Hit:7 [http://archive.canonical.com](http://archive.canonical.com) xenial InRelease                            
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Hit:9 [http://www.openprinting.org/download/printdriver/debian](http://www.openprinting.org/download/printdriver/debian) lsb3.2 Release   
Ign:11 [http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu) xenial InRelease
Err:12 [http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu) xenial Release
  404  Not Found
Hit:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease          
Reading package lists... Done                                                  
E: The repository 'http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: [http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/Release.gpg:](http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/Release.gpg:) Signature by key F8897B6F00075648E248B7EC24CBF5474CFD1E2F uses weak digest algorithm (SHA1)
dave@dave-desktop:~$

---

### Post by #&amp;thj^% on 2017-01-23
> **aviator1 said:**
> Here's the latest.

```
dave@dave-desktop:~$ sudo apt update
[sudo] password for dave: 
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                     
Hit:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Ign:5 [http://www.openprinting.org/download/printdriver/debian](http://www.openprinting.org/download/printdriver/debian) lsb3.2 InRelease 
Hit:6 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) xenial InRelease    
Hit:7 [http://archive.canonical.com](http://archive.canonical.com) xenial InRelease                            
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Hit:9 [http://www.openprinting.org/download/printdriver/debian](http://www.openprinting.org/download/printdriver/debian) lsb3.2 Release   
Ign:11 [http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu) xenial InRelease
Err:12 [http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu) xenial Release
  404  Not Found
Hit:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease          
Reading package lists... Done                                                  
E: The repository 'http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: [http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/Release.gpg:](http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/Release.gpg:) Signature by key F8897B6F00075648E248B7EC24CBF5474CFD1E2F uses weak digest algorithm (SHA1)
```
dave@dave-desktop:~$
Well I did not see this one??
```
http://ppa.launchpad.net/libreoffice/libreoffice-4-4
```
Best to comment that out since it also has seen no activity since:"(2015-08-05)"
This you will just have to live with until they comply with Ubuntu's new signing protocol.
```
W: [http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/Release.gpg:](http://www.openprinting.org/download/printdriver/debian/dists/lsb3.2/Release.gpg:) Signature by key F8897B6F00075648E248B7EC24CBF5474CFD1E2F uses weak digest algorithm (SHA1)
```
Now after that you should be in good shape out side of the key warnings.
So if you want to open another thread With systemd slow boot "1min 783ms upower.service" or something of that same line.
I was not much help here but you are welcome and Kind Regards

---

### Post by aviator1 on 2017-01-23
Doesn't it show at: ??

Ign:11 [http://ppa.launchpad.net/libreoffice...ice-4-4/ubuntu]("http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu") xenial InRelease
Err:12 [http://ppa.launchpad.net/libreoffice...ice-4-4/ubuntu]("http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu") xenial Release
  404  Not Found

How do I comment that out?

Thanks

---

### Post by #&amp;thj^% on 2017-01-23
The easiest way here is to use synaptic package manager.
Do you have that installed?
BTW If you must have a PPA for Libre Office you might want to check this one out.
[https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa)

---

### Post by aviator1 on 2017-01-23
Great.

Thanks very much for your help. I shall be starting another thread as you suggested.

Kind Regards.

---

### Post by aviator1 on 2017-01-25
Solved.

See 
[h=3][System slow boot "1min 783ms upower.service]("https://ubuntuforums.org/showthread.php?t=2350362")[/h]

---

