---
title: "Can not read/write files to walkman"
date: 2013-05-23
forum: General Help
---

### Post by Chelidze on 2013-05-23
So today I connected walkamn to my ubuntu pc knowing that it used to work at least on every other versions of ubuntu I have tried, latest 12.10
So I connected it and it showed files and folders as it used to but when I try to play something, it did not work, vlc even showed an error massage

```
[COLOR=#FF0000]File reading failed:[/COLOR][COLOR=#000000]VLC could not open the file "/run/user/levan/gvfs/mtp:host=%5Busb%3A001%2C006%5D/65537/7/6268". (Operation not supported)[/COLOR]
[COLOR=#ff0000]Your input can't be opened:[/COLOR]
[COLOR=#000000]VLC is unable to open the MRL 'file:///run/user/levan/gvfs/mtp%3Ahost%3D%255Busb%253A001%252C006%255D/65537/7/6268'. Check the log for details.[/COLOR]
```

and I do not remember if it used to show the location of walkman as 

```
mtp://[usb:001,006]/65537
```

on other ubuntu this thing used to work even better than on windows ??

what is wrong with ubuntu 13.04 first it did not installed the printer drivers correctly and now this

does any one knows how to fix it

THank you in advanced

---

### Post by Chelidze on 2013-08-13
This is the way I fixed it 

I just installed gvfs MTP

```
[FONT=arial][B]sudo add-apt-repository ppa:langdalepl/gvfs-mtp
sudo apt-get update
sudo apt-get upgrade[/B][/FONT]
```

[https://launchpad.net/~langdalepl/+archive/gvfs-mtp](https://launchpad.net/~langdalepl/+archive/gvfs-mtp)

---

