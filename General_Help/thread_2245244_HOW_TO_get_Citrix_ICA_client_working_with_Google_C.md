---
title: "HOW TO get Citrix ICA client working with Google Chrome browser in Linux and LXDE"
date: 2014-09-22
forum: General Help
---

### Post by hgfelger on 2014-09-22
There is a nice thread describing how to get Chrome back working with Citrix Receiver (ica).

This solution will work with Gnome and KDE - as far as I understand it: [URL="http://ubuntuforums.org/showthread.php?t=1645173&page=4"]http://ubuntuforums.org/showthread.php?t=1645173&page=4
[/URL]

Now I wondered, why this did not work with Lubuntu (LXDE). If you have a look into xdg-open (it's a bash script - so its debugable with "bash -x") you will see, that there are different ways for the different desktopenvironmnets (e.g. KDE, Gnome, xfce4...). Where the fater one have there special mime-binaries, for LXDE or others it wil fall back to use the standard tool file.

So we need to enable file to recognice the downloaded ICA file - not like in standard as ASCII-Text - but as application/x-ica.
Then I think it will be enoght, if you also append the mime-type line (see other thread) to the .desktop file.

So I created (I your's exists - then append to it) the file ~/.magic with 2 lines:
```
0	search	=[WFClient]	ICA-File
!:mime	application/x-ica
```

Be sure, that the columnseparators are tabs, not blancs. After that file retuned the right mime-type like in the example blow:
> file -ik ~/Downloads/launch.ica 
/home/hgfelger/Downloads/launch.ica: application/x-ica; charset=us-ascii


If you now try it with 
> xdg-open  ~/Downloads/launch.ica 
it should start wfica.sh and it told me, that some SSL-Error occured, as it is not started within the right browser-vpn-context.

So you are ready to give chrome a try!

Good luck!
  Hartwig
---
Context: Lubuntu
lsb_release -d -> Description:	Ubuntu 14.04.1 LTS
file --version -> file-5.14
XDG_CURRENT_DESKTOP=LXDE

---

