---
title: "Is it possible to install Wine and Skype in Ubuntu 12.04 LTS 64 bit?"
date: 2014-02-27
forum: General Help
---

### Post by desconocido on 2014-02-27
I've been trying since January 6th without success, so it has been suggested to me that I should ask whether anyone has actually succeeded in installing them in that environment.

Anyone had any luck?

---

### Post by nunecas123 on 2014-02-27
Isn't Skype available on Linux? Or are you telling me that you can't install both?

---

### Post by desconocido on 2014-02-27
> **nunecas123 said:**
> Or are you telling me that you can't install both?

I can't install Wine and I can't keep Skype installed, although both are supposed to be available. See
[http://ubuntuforums.org/showthread.php?t=2203319]("http://ubuntuforums.org/showthread.php?t=2203319") and
[http://ubuntuforums.org/showthread.php?t=2208041]("http://ubuntuforums.org/showthread.php?t=2208041")
if you want the latest details.

I gather you don't have Skype installed?

---

### Post by Bucky Ball on 2014-02-27
Software Centre>Search for and install Skype. You don't need to manually compile or install anything.

If you have been installing Skype via Software Centre, what seems to be the problem? Specifically and with an exact description of what happens.

Always try with Software Centre first.

---

### Post by desconocido on 2014-02-27
> **Bucky Ball said:**
> What seems to be the problem? Specifically and with an exact description of what happens.

Details on this thread:
[http://ubuntuforums.org/showthread.php?t=2203319](http://ubuntuforums.org/showthread.php?t=2203319)

---

### Post by grahammechanical on 2014-02-27
I have installed Skype. I cannot remember what version of Ubuntu I had it on, 12.04 or earlier. I have also installed wine, on 12.04 and on Trusty Tahr. I use the Software Centre.

I also think that it is better to fresh install rather than upgrade. Anyway, I think that things like Skype should be uninstalled before the upgrade is activated. Then they can be re-installed with a version packaged for 12.04 or whatever version we have upgraded to.

The developers cannot take into account the need to upgrade proprietary software like Skype. Ubuntu 12.04 had vastly different libraries to the ones in your previous version of Ubuntu. 14.04 will have different libraries to 12.04. I am not surprised that the upgrade broke Skype.

Applications installed through the Software Centre are packaged for that version of Ubuntu. The installation brings in all the libraries that the application depends on.

Regards.

---

### Post by raja.genupula on 2014-02-28
or...........choose from here 

[http://www.skype.com/en/download-skype/skype-for-linux/](http://www.skype.com/en/download-skype/skype-for-linux/)

---

### Post by desconocido on 2014-02-28
> **grahammechanical said:**
> I have installed Skype. I cannot remember what version of Ubuntu I had it on, 12.04 or earlier. I have also installed wine, on 12.04 and on Trusty Tahr. I use the Software Centre.
Thanks for the info. Do you remember whether it was a 64 bit machine?

> I also think that it is better to fresh install rather than upgrade. Anyway, I think that things like Skype should be uninstalled before the upgrade is activated. Then they can be re-installed with a version packaged for 12.04 or whatever version we have upgraded to.
I think you are right, although in my case this was a first install of Ubuntu on the machine and I tried to install Skype and Wine afterwards.

> The developers cannot take into account the need to upgrade proprietary software like Skype. Ubuntu 12.04 had vastly different libraries to the ones in your previous version of Ubuntu. 14.04 will have different libraries to 12.04. I am not surprised that the upgrade broke Skype.

Applications installed through the Software Centre are packaged for that version of Ubuntu. The installation brings in all the libraries that the application depends on.
With the default repository settings, I couldn't find Skype on the Ubuntu Software Centre (see attachment), so it got it from skype.com (see next reply). 

Ubuntu Software Centre wouldn't install Wine, so I went to try with apt-get. The problem with USC is that you don't get much info about the problems encountered.

Of course, it is possible that if I tried to install Wine as the first thing I did after an install, it might work.

Thanks again.

---

### Post by desconocido on 2014-02-28
> **raja.genupula said:**
> or...........choose from here 

[http://www.skype.com/en/download-skype/skype-for-linux/](http://www.skype.com/en/download-skype/skype-for-linux/)

Yes, I did that. I chose the option "Ubuntu 12.04 (multiarch)".
That gave me a file called "skype-ubuntu-precise_4.2.0.13-1_i386.deb"
I installed that by right-clicking on the file and chosing the option "Open with Ubuntu Software Centre".

Skype worked for a while but then apt-get decided to remove some essential i386 libraries.

Thanks.

---

### Post by desconocido on 2014-03-03
> **desconocido said:**
> 
Of course, it is possible that if I tried to install Wine as the first thing I did after an install, it might work.


Well, I tried a re-install. I tried Wine as the first thing and it installed.

Then I tried Skype. Even with the "Canonical Partners" box ticked, Ubuntu Software Centre couldn't find Skype (see attachment).

I tried to install it by right-clicking on the file "skype-ubuntu-precise_4.2.0.13-1_i386.deb" and chosing the option "Open with Ubuntu Software Centre".
That didn't work (although it has done earlier this year): (see other attachment).

To parody Morecombe and Wise, I have installed all the right packages, just maybe not in the right order.

---

### Post by desconocido on 2014-03-04
> **desconocido said:**
> Anyone had any luck?

Yes, at last. I backed up my home directory, ran the live DVD, deleted all . files/folders in ~ except the ones I needed:
```
.gtk-bookmarks
.mozilla/
.thunderbird/
.themes/
```
and re-installed Ubuntu 12.04 (amd64) using
/dev/sda1 (type efi) as "Device for boot loader installation",
/dev/sda2 (type ext4) mount as / with format option,
/dev/sda4 (type ext4) mount as /home - *NO format option*

This worked fine. The above files/folders were untouched (or at least work just as they used to) and new hidden stuff was put in my home folder.

This had the added advantage that I have finally been able to install Skype and Wine on the computer - maybe there was a lot of cruft from repeated installs that was kept in my home folder? Certainly Ubuntu Software Centre's history knew about everything I did through four installs where / was formatted each time. Now history begins today.

So maybe some of these dependency problems are caused by files stored in the home folder?

---

