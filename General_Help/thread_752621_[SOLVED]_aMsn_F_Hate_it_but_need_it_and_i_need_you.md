---
title: "[SOLVED] aMsn F*** Hate it but need it and i need your help"
date: 2008-04-11
forum: General Help
---

### Post by scraghty604 on 2008-04-11
Hi so have been all over the map trying to get this to work, and im goign nuts.

1-installed from synaptic---Ok worked but when i tryed to do skins or plugins said i need the latest version
2-Went to the website and dl the lastest version for tk8.5
3-Got an error [IMG]http://img152.imageshack.us/img152/3691/amsnwe0.jpg[/IMG]
4-Did as posted on other page


 Re: Amsn + gutsy + tkcximage = ????
try this:
Code:

sudo mv /usr/bin/wish /usr/bin/wish-backup
sudo ln -s /usr/bin/wish8.4 /usr/bin/wish

Also, install tlc-dev with this:

Code:

sudo apt-get install tcl8.4-dev

5-Now it shows as starting in the taskbar but then goes away
6-I uninstalled amsn from synaptic and thrid party

7-And if i try and reinstall i get a tk GUI toolkit failed when doing the autoinstall

and am now lost

---

### Post by scraghty604 on 2008-04-11
On restart get same Error

---

### Post by ibuclaw on 2008-04-11
First, I'd remove tcl8.5 with make from the source folder.
```
 sudo make uninstall 
```

And I'd re-install from synaptic aMSN and it's dependencies.
```

sudo apt-get purge amsn tcl8.4 tk8.4
apt-get install amsn tcl8.4 tk8.4

```

And then get the new version of aMSN [here.]("http://downloads.sourceforge.net/amsn/amsn-0.97.tar.bz2?modtime=1198526059&big_mirror=0")
Now, that is the source tarball. But you should have issues with installing it.
```

bzip2 -d amsn*.bz2
tar xf amsn*.tar
cd amsn*
./configure
make all
sudo make install

```

Also, what plugin are you trying to use?
As you should have no trouble.

Though, if things get desperate for you, I'd advice that you'd switch to Hardy now. Not that you should take that advice wisely. But being around a fortnight away from it's official release, it is already in a pristine stable condition. It has the spanking new version of aMSN, as well as tcl8.5 and tk8.5 in the repositories at your disposal.

And why not? I been using Hardy since the alpha was released, and aMSN has worked fine throughout. Though I've kept it pretty much at it's default, as my needs aren't as high as other peoples.

Though as I said, choose to switch wisely, and make backups of important data before-so.

Regards
Iain

---

### Post by scraghty604 on 2008-04-11
i cant seem to get that to work, guess i might as well update to the newest verison of ubuntu since this is a fresh install, i se it says april is gonna be the finalla release...it is halfway thru april any ideas on when it will be offical

---

### Post by fragos on 2008-04-11
Consider checking pidgen, aka gaim. It works with MSN. To my surprise MSN let me sign up with a gmail address.

---

### Post by scraghty604 on 2008-04-11
I need webcam capable, so aMsn  is my only option

---

### Post by davgard on 2008-04-12
there is the KDE equivalent, Kopete this is what i use and it works very well in ubuntu

---

### Post by Claus7 on 2008-04-13
Hello - &#967;&#945;&#943;&#961;&#949;&#964;&#945;&#953;!

First of all why do you hate it? Ok it takes some time to work and it is not so eye candy in the beginning, yet for me at least it works nicely. If it hadn't been for the voice conversation, it would have been very nice indeed. 

Every now and then I see people getting offline and all of them using the msn from windows. In order for this to happen to me, I have to push it a lot! And apart from that is a work based on reverse engineering, which is not trivial.

Anyway, I had checked that hardy will have tk and tcl libraries version 8.5 in the repositories, so the eye candy thing should not be a problem for this version (at least this is what I think). So my advice would be to wait two weeks or so and do a fresh install of amsn from there. In case you do not want to wait, then do the following:
[http://ubuntuforums.org/showthread.php?p=4555010#post4555010](http://ubuntuforums.org/showthread.php?p=4555010#post4555010)
I would propose you do to mine, because that way I will see if it is working on someone else and doing so you will have control over the entire installation! Of cource I'm kidding. Judge on your own!

EDIT: I see that you made a soft link to 8.4 version of amsn (wish8.4), yet you say that you installed the latest 8.5 version of tk... Or I didn't understand well the steps you did.
> **scraghty604 said:**
> 2-Went to the website and dl the lastest version for tk8.5> **scraghty604 said:**
> sudo ln -s /usr/bin/wish8.4 /usr/bin/wish
Regards -&#935;&#945;&#953;&#961;&#949;&#964;&#953;&#963;&#956;&#959;&#973;&#962;!

---

### Post by scraghty604 on 2008-04-14
thanxs for the input...im done screwing with it so i will wait till the hardy final relase on the 24th and work with it form there..., hopefully should have no problems ..again thanxs tho to all helped

---

