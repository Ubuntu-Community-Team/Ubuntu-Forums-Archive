---
title: "Update Manager fail"
date: 2013-01-16
forum: General Help
---

### Post by bripa on 2013-01-16
Hi 
First of all thanks in advance for any reply.
I'm getting the below error when running the Update Manager, which then cause me OS instability and need to revert back to the previous grub. 
To be said I'm quite a unacknowledged user of Linux. 
Any help?
If necessary to provide additional info, please guide me. Thanks

```

Error:
installArchives() failed: (Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 288108 files and directories currently installed.) 
Preparing to replace python-problem-report 2.0.1-0ubuntu15.1 (using .../python-problem-report_2.0.1-0ubuntu17.1_all.deb) ... 
Unpacking replacement python-problem-report ... 
Preparing to replace python-apport 2.0.1-0ubuntu15.1 (using .../python-apport_2.0.1-0ubuntu17.1_all.deb) ... 
Unpacking replacement python-apport ... 
Preparing to replace apport 2.0.1-0ubuntu15.1 (using .../apport_2.0.1-0ubuntu17.1_all.deb) ... 
apport stop/waiting 
Unpacking replacement apport ... 
Preparing to replace apport-gtk 2.0.1-0ubuntu15.1 (using .../apport-gtk_2.0.1-0ubuntu17.1_all.deb) ... 
Unpacking replacement apport-gtk ... 
Preparing to replace vlc-plugin-pulse 2.0.3-0ubuntu0.12.04.1 (using .../vlc-plugin-pulse_2.0.5-0ubuntu0.12.04.1_i386.deb) ... 
Unpacking replacement vlc-plugin-pulse ... 
Preparing to replace vlc-plugin-notify 2.0.3-0ubuntu0.12.04.1 (using .../vlc-plugin-notify_2.0.5-0ubuntu0.12.04.1_i386.deb) ... 
Unpacking replacement vlc-plugin-notify ... 
Preparing to replace vlc 2.0.3-0ubuntu0.12.04.1 (using .../vlc_2.0.5-0ubuntu0.12.04.1_i386.deb) ... 
Unpacking replacement vlc ... 
Preparing to replace libvlccore5 2.0.3-0ubuntu0.12.04.1 (using .../libvlccore5_2.0.5-0ubuntu0.12.04.1_i386.deb) ... 
Unpacking replacement libvlccore5 ... 
Preparing to replace vlc-data 2.0.3-0ubuntu0.12.04.1 (using .../vlc-data_2.0.5-0ubuntu0.12.04.1_all.deb) ... 
Unpacking replacement vlc-data ... 
Preparing to replace vlc-nox 2.0.3-0ubuntu0.12.04.1 (using .../vlc-nox_2.0.5-0ubuntu0.12.04.1_i386.deb) ... 
Unpacking replacement vlc-nox ... 
Preparing to replace libvlc5 2.0.3-0ubuntu0.12.04.1 (using .../libvlc5_2.0.5-0ubuntu0.12.04.1_i386.deb) ... 
Unpacking replacement libvlc5 ... 
Processing triggers for shared-mime-info ... 
Unknown media type in type 'all/all' 
Unknown media type in type 'all/allfiles' 
Unknown media type in type 'uri/mms' 
Unknown media type in type 'uri/mmst' 
Unknown media type in type 'uri/mmsu' 
Unknown media type in type 'uri/pnm' 
Unknown media type in type 'uri/rtspt' 
Unknown media type in type 'uri/rtspu' 
Processing triggers for man-db ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for ureadahead ... 
ureadahead will be reprofiled on next reboot 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Setting up linux-image-3.2.0-35-generic-pae (3.2.0-35.55) ... 
Running depmod. 
Failed to run depmod 
dpkg: error processing linux-image-3.2.0-35-generic-pae (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of linux-image-generic-pae: 
 linux-image-generic-pae depends on linux-image-3.2.0-35-generic-pae; however: 
  Package linux-image-3.2.0-35-generic-pae is not configured yet. 
dpkg: error processing linux-image-generic-pae (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic-pae: 
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.35.40); however: 
  Package linux-image-generic-pae is not configured yet. 
dpkg: error processing linux-generic-pae (--configure): 
 dependency problems - leaving unconfigured 
Setting up python-problem-report (2.0.1-0ubuntu17.1) ... 
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Setting up python-apport (2.0.1-0ubuntu17.1) ... 
Setting up apport (2.0.1-0ubuntu17.1) ... 
apport start/running 
Setting up apport-gtk (2.0.1-0ubuntu17.1) ... 
Setting up vlc-data (2.0.5-0ubuntu0.12.04.1) ... 
Setting up libvlccore5 (2.0.5-0ubuntu0.12.04.1) ... 
Setting up libvlc5 (2.0.5-0ubuntu0.12.04.1) ... 
Setting up vlc-nox (2.0.5-0ubuntu0.12.04.1) ... 
Setting up vlc-plugin-pulse (2.0.5-0ubuntu0.12.04.1) ... 
Setting up vlc-plugin-notify (2.0.5-0ubuntu0.12.04.1) ... 
Setting up vlc (2.0.5-0ubuntu0.12.04.1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 linux-image-3.2.0-35-generic-pae 
 linux-image-generic-pae 
 linux-generic-pae 
Error in function:  
Setting up linux-image-3.2.0-35-generic-pae (3.2.0-35.55) ... 
Running depmod. 
Failed to run depmod 
dpkg: error processing linux-image-3.2.0-35-generic-pae (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of linux-image-generic-pae: 
 linux-image-generic-pae depends on linux-image-3.2.0-35-generic-pae; however: 
  Package linux-image-3.2.0-35-generic-pae is not configured yet. 
dpkg: error processing linux-image-generic-pae (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic-pae: 
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.35.40); however: 
  Package linux-image-generic-pae is not configured yet. 
dpkg: error processing linux-generic-pae (--configure): 
 dependency problems - leaving unconfigured
```

---

### Post by zvacet on 2013-01-18
Try with 

```
sudo dpkg --configure -a
```

---

### Post by bripa on 2013-01-19
Hi there,
[I was sure having already posted this issue, but can't find the thread]

I have problems in following the automated procedure Update Manager: I got problems and then the Grup is corrupted, which requires me to boot with the previous one. 

From the terminal 
sudo dpkg --configure -a
and got the following error:

Setting up linux-image-3.2.0-35-generic-pae (3.2.0-35.55) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-3.2.0-35-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-35-generic-pae; however:
  Package linux-image-3.2.0-35-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.35.40); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.2.0-35-generic-pae
 linux-image-generic-pae
 linux-generic-pae

Any help?
Thanks in advance for the reply
Paolo

---

### Post by bogustrumper on 2013-01-19
Sounds like dpkg-reconfigure -a is not handling packages in the right order, or having issues trying to do everything at once. I'd recommend trying to run it manually, giving it the packages that seem to be causing the problems instead of the -a flag. Then you can try dpkg-reconfigure -a again after each success; might get lucky that way. 

So start with linux-image-3.2.0-35-generic-pae, and if that works try running -a again. If not, try running dpkg-reconfigure on whatever package raised a flag. Something should at least give you some insight, and then you can drill down a little deeper on a particular package that's giving you problems, or try just removing it entirely.

You could also try something like this:
[CODE]
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade
[/CODE[

...but I'm assuming that you've already struggled with that approach and found it useless. If not, could be worth a try.

If all else fails, you could always go nuclear and reinstall. There's another way, for sure... but if you've been stringing this installation along from version to version, or installing lots of things that aren't being maintained anymore, then sometimes it can be nice to start fresh.

---

### Post by Elfy on 2013-01-19
>  [I was sure having already posted this issue, but can't find the thread]I've now merged them - in future you can find your posts/threads in your user cp - statistics, or at the top of any page - Search - Your Posts or Threads.

---

### Post by bripa on 2013-01-20
Thanks for the help!

I've tried your suggested script with blind eyes (I'm a BIG dummy). 

After that I got the following error:
Errors were encountered while processing:
 linux-image-3.2.0-35-generic-pae
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

What could be?

Paolo

---

### Post by COMECON on 2013-01-20
> **bripa said:**
> Hi there,
[I was sure having already posted this issue, but can't find the thread]

I have problems in following the automated procedure Update Manager: I got problems and then the Grup is corrupted, which requires me to boot with the previous one. 

From the terminal 
sudo dpkg --configure -a
and got the following error:

Setting up linux-image-3.2.0-35-generic-pae (3.2.0-35.55) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-3.2.0-35-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-35-generic-pae; however:
  Package linux-image-3.2.0-35-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.35.40); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.2.0-35-generic-pae
 linux-image-generic-pae
 linux-generic-pae

Any help?
Thanks in advance for the reply
Paolo

Please, wrap the output between the **CODE** tags.

> **bogustrumper said:**
> Sounds like dpkg-reconfigure -a is not handling packages in the right order, or having issues trying to do everything at once. I'd recommend trying to run it manually, giving it the packages that seem to be causing the problems instead of the -a flag. Then you can try dpkg-reconfigure -a again after each success; might get lucky that way. 

So start with linux-image-3.2.0-35-generic-pae, and if that works try running -a again. If not, try running dpkg-reconfigure on whatever package raised a flag. Something should at least give you some insight, and then you can drill down a little deeper on a particular package that's giving you problems, or try just removing it entirely.

You could also try something like this:
[CODE]
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade
[/CODE[

...but I'm assuming that you've already struggled with that approach and found it useless. If not, could be worth a try.

If all else fails, you could always go nuclear and reinstall. There's another way, for sure... but if you've been stringing this installation along from version to version, or installing lots of things that aren't being maintained anymore, then sometimes it can be nice to start fresh.

Please, correct the *[/CODE[* tag on the post.

I also agree, if running those commands don't work, I don't know what could you do. :(

esy

---

### Post by bripa on 2013-01-22
Thanks both to try help me.

I'm very sorry but it is not clear for me what you mean with "Please, wrap the output between the **CODE** tags".

Thanks for clarifying. Maybe I'm just incorrectly using your suggestion.

Paolo

---

### Post by grahammechanical on 2013-01-22
Hi bripa

First, when we click on the quick reply icon we get a box to type our reply in. Above that box are some icons that make formatting our reply easier.

Move the mouse pointer over the last icon on the right. You should see this.

"Wrap >  tags around selected text."

Select the text click the icon that looks like a speech bubble with words in it.

Now as to your problem. This will just be a guess. Am I correct in thinking that at the Grub menu you can select an earlier kernel to boot? It that what you mean when you say

[QUOTE] need to revert back to the previous grub

If you can get to a desktop based upon a kernel earlier than linux-image-3.2.0-35-generic-pae (that means with a number lower than 35) then boot into that kernel.

If you are using 12.04 you may have Synaptic Package Manager installed. Use it to reinstall or remove Linux kernel linux-image-3.2.0-35-generic-pae and related 3.2.0-35 stuff that is installed.

Search Synaptic for Linux kernels and scroll down the results looking for 3.2.0-35. Select what you find and right click and select Mark for Reinstallation. If that does not work try Mark for Complete Removal and then reboot and try to use synaptic to reinstall the 3.2.0-35 kernel.

If you can boot using an earlier kernel then do so. I am using the development branch of 13.04 and few weeks ago it got Linux kernel 3.7.0.0 This worked fine but I could not get to a desktop with kernel 3.7.0.1 or 0.2; 0.3 or 0.4. It was not until the kernel was updated to 3.7.0.5 that I could boot into these later kernels. Until then I had to keep booting into 3.7.0.0. It was no big deal.

Regards.

---

### Post by Cheesehead on 2013-01-22
3.2.0-35.55 is not the current 12.10 kernel.
3.2.0-36.43 is the current kernel...today.

Look in System Settings --> Software Sources. If you have any PPAs or unoffical repositories, disable (uncheck) them.

Remove the problem packages from your apt cache.
```
sudo rm /var/cache/apt/archive/linux-image-3.2.0-35-generic-pae
sudo rm /var/cache/apt/archive/linux-image-generic-pae 
sudo rm /var/cache/apt/archive/linux-generic-pae
```

Update your package lists.
This will change the upgrade target from 3.2.0-35.55 to the current kernel.
```
sudo apt-get update
```

Try upgrading again
```
sudo apt-get upgrade
```

Let us know what happens.

---

### Post by bripa on 2013-01-26
Thanks for the support
Not very much success indeed. I see now a new PAE .36 appear while the 35 is corrupted
I probably have identifed which application makes problem but when trying to uninstall, it requires the 35 and then fail. 

I wonder if it is better to reinstall all Ubuntu again....

Thanks anyway

---

### Post by bogan on 2013-01-29
Hi!, **Cheesehead,**

You Posted:>  3.2.0-35.55 is not the current [COLOR=Red]12.10 [/COLOR]kernel.
3.2.0-36.43 is the current kernel...today.Sorry, but I have to correct you:
3.2.0-36.43 may be the current [COLOR=Red]12.04 [/COLOR]kernel. Precise
3.5.0-23-#35 is the current latest[COLOR=Blue] 12.10[/COLOR] kernel...today. Quantal Proposed-generic

Chao!, **bogan.**

---

### Post by idcrewdawg on 2013-02-01
I'm using 12.10 and there was an update push today. Because of that update I'm unable to run flash video in my Google Chrome Browser but it does work in my Firefox browser.

I looked through the update history, and found the offending chrome update, but want to revert to the previous driver version before that update was installed.

How do I revert a particular software driver update?

---

