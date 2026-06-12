---
title: "Adept problems with &lt;OK&gt; prompt"
date: 2007-01-21
forum: General Help
---

### Post by leupi on 2007-01-21
I have had this issue a few times and I am hoping that someone may know what I am doing wrong. I am using Kubuntu and when I try to install certain applications with Adept Package Installer (such as vmware-player, flashplayer-nonfree, jre) I have to agree to some kind of EULA; however, there is no way to acitivate the <OK> button. I try hitting enter, the tab key, the curser, nothing seems to activate the button and I am stuck. I then have to shutdown Adept and am then stuck with a corrupted package installed that gives me errors whenever I try and use Adept. Right now I am getting this error:
```
Read Only Mode, Database Locked
You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.
```
If I try to uninstall the application I get this:
```
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
tparks@linux4500:/var/lib/dpkg$ Errors were encountered while processing:
 vmware-player

```
I cannot seem to install or uninstall this application. Same this happened with flashplayer-nonfree, I reinstalled the OS but I really do not feel like doing that again...
I have had this issue with applications that require you to accept an EULA and hit the <OK> button, which for the life of me I cannot activate. I have used the button when I am just being asked some kind of config question and it works fine then.

Any ideas? I am really confused about this one.

Thanks,
Todd

---

### Post by leupi on 2007-01-21
I used apt-get with the --force-yes option and that removed vmware from the system and I can use Adept again (YAY!). One thing though is that xserver-xorg-video-vmware is still installed and if I try and use Adept to remove it it wants to remove kubuntu-desktop, xorg, xserver-xorg-video-all also. Somehow I do not think that that will be real good for my system. Any thoughts on how to get that removed without removing all of the rest? If not, I can keep it, so far it does not seem to be breaking anything.

I am still wondering why I cannot choose <OK> during an install...

Thanks,
Todd

---

### Post by _Agrajag_ on 2007-01-23
> **leupi said:**
> I used apt-get with the --force-yes option and that removed vmware from the system and I can use Adept again (YAY!). One thing though is that xserver-xorg-video-vmware is still installed and if I try and use Adept to remove it it wants to remove kubuntu-desktop, xorg, xserver-xorg-video-all also. Somehow I do not think that that will be real good for my system. Any thoughts on how to get that removed without removing all of the rest? If not, I can keep it, so far it does not seem to be breaking anything.

I am still wondering why I cannot choose <OK> during an install...

Thanks,
Todd

I had the same problem today with vmware-player.  I haven't resolved the problem yet, but hopefully I'll figure it out.

---

### Post by leupi on 2007-01-23
I installed vmware on Kubuntu 6.06 with [these]("http://www.howtoforge.com/ubuntu_vmware_server") instructions and when I upgraded the kernel I used [this]("http://www.ubuntuforums.org/archive/index.php/t-25258.html") to repair the install. Hope this helps.

It is nice to see that it was not just me having this problem  :)

Todd

---

