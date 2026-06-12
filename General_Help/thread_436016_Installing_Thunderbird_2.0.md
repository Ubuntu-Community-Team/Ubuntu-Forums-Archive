---
title: "Installing Thunderbird 2.0"
date: 2007-05-07
forum: General Help
---

### Post by chscag on 2007-05-07
Hi:

I'm currently using Thunderbird 1.5 as my newsreader client in Fiesty and would like to upgrade it to the latest - version 2.0.

I downloaded version 2.0 for Linux from the Mozilla site and extracted the files.  However, I do not see a way to install it, or more than likely, I don't know how. :(   I could not find a deb file among the extracted files.  Would appreciate any help or direct me to where I can learn how.   Thanks and regards.

---

### Post by angryhomer17 on 2007-05-07
Go to [http://www.getautomatix.com/](http://www.getautomatix.com/) and follow the installation instructions. Thunderbird 2.0 is one of the software packages that automatix provides. Automatix is like synaptic package manager, very easy to use. Just select what packages you want installed and atomatix does the rest.

---

### Post by Meese on 2007-05-07
I am also interested here.  And without having to install automatix.  Given the .tar.gz from mozilla.org, extracted to a folder ~/thunderbird  as example...there seems to be no .bin, ./configure doesnt work etc etc.

Any help?

---

### Post by Wiebelhaus on 2007-05-07
use google and find the .deb or do what homer said

---

### Post by chscag on 2007-05-07
Thanks guys.

I installed Automatrix2 as suggested.  Now my question is - if I install Thunderbird 2.0, will it overwrite and mess up my Thunderbird 1.5?  Hopefully it will just upgrade from version 1.5 to 2.0 and keep all my data intact but I have no idea if it will.  Any suggestions?

Thanks and regards.

---

### Post by angryhomer17 on 2007-05-07
Usually upgrading doesn't mess with your settings, but there is always the chance that it will. Going from 1.5 to 2.0 should just overwrite some of the thunderbird files, but shouldn't mess with any emails or folders or other stuff.

To backup:

```
cp ~/.mozilla-thunderbird ~/.mozilla-thunderbird.bckp 
```

That folder should have all your settings and emails. If something happens after upgrading to 2.0 you can always downgrade and then use your backup to replace the downgraded installation. I might do this myself soon. Gotta see if it's worth it to upgrade to 2.0 first.

---

### Post by chscag on 2007-05-08
Thanks for the advice.  Will backup as you suggested prior to updating.

Regards.

---

### Post by BoNeR on 2007-05-15
Thanks heaps for the heads up on Automatix, Homer :):)

It really does work a treat

Cheers

BoNeR

---

### Post by Derevko on 2007-05-16
You can find a feisty backport in my repository [http://ubuntu.iuculano.it/](http://ubuntu.iuculano.it/)

[http://ubuntu.iuculano.it/dists/feisty/thunderbird/](http://ubuntu.iuculano.it/dists/feisty/thunderbird/)

---

### Post by cmp1988 on 2007-07-31
Derevko, you just made life much easier without having to go through Automatix.  Thanks.

---

### Post by Industrial PhD on 2007-08-01
How can we do it without using automatix? I downloaded the tar and tried to run it and all I get is 
```

industrialphd@industrialphd:~/Desktop/thunderbird$ ./thunderbird
./thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
industrialphd@industrialphd:~/Desktop/thunderbird$ ./thunderbird-bin
./thunderbird-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory
industrialphd@industrialphd:~/Desktop/thunderbird$      
```

I'd like to know non-distro specific way to install this and make it work.

---

### Post by eeried on 2007-08-01
To install from a bimary tar.gz file, do the following -- most simple: 
- launch an xterm
- copy your tar.gz file to /opt (you need to type sudo before the command
```
sudo cp name-of-the-file.tar.gz /op
```
- then go to /opt (no sudo):
```
cd /opt
```
- Then untar the file which will create a dir called thunderbird:
```
sudo tar -xzvf name-of-the-file.tar.gz
```

That's it!
To launch Thunderbird, you can type:
```
/opt/thunderbird/thunderbird
```

To make things swifter, make a launcher in the taskbar: right click on an empty space > add an item > add a launcher
> fill in the fields:
name Thunderbird2
description: mail
icon: browse to /opt/thunderbird/ icons (or /opt/thunderbird//chrome/default/icons, and choose your icon
path: /opt/thunderbird/thunderbird

Now clicking on the icon should launch Thunderbird

Note: if the name of the dir is mozilla-thunderbird, adapt the above  accordingly. The executable file may also be mozilla-thunderbird.

Note2: if you install thunderbird this way it won't update with the rest of the system. The next Thunderbird version will have to be installed manually after your deleting the /opt/thunderbird dir (this deletes the program from your system).

The wiki or the help doc has an howto install Firefox as if it had been installed through apt.

Good luck :guitar:

I too am going to install thunderbird 2.

cheers

---

### Post by Industrial PhD on 2007-08-01
I've done the above exactly except i'm attempting to launch it from within it's own directory, so i'm doing ./thunderbird instead of /home/desktop/thunderbird/thunderbird

any ideas on my errors above?

---

### Post by Industrial PhD on 2007-08-01
i should also state that when installing from apt it installs 1.5, and i'd like the newest version.

---

### Post by stchman on 2007-08-01
> **Industrial PhD said:**
> I've done the above exactly except i'm attempting to launch it from within it's own directory, so i'm doing ./thunderbird instead of /home/desktop/thunderbird/thunderbird

any ideas on my errors above?

I have a script to install Thunderbird 2.

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

Look at the bottom for Thunderbird 2 script.

Hope this helps.

---

### Post by eeried on 2007-08-02
Why don't you put your Thunderbird dir into /opt if you've got access to sudo?

As for the script, better look at the doc which gives you the link to a script maintained by Ubuntuzilla that's been tested and offers a guide to the manual step-by-step approach: [https://help.ubuntu.com/community/ThunderbirdNewVersion?highlight=%28thunderbird%29](https://help.ubuntu.com/community/ThunderbirdNewVersion?highlight=%28thunderbird%29)

Firefox:
[https://help.ubuntu.com/community/FirefoxNewVersion?highlight=%28firefox%29](https://help.ubuntu.com/community/FirefoxNewVersion?highlight=%28firefox%29)

---

### Post by nanotube on 2007-08-23
i can also recommend the ubuntuzilla project as an easy way to install the latest thunderbird:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by imbjr on 2007-08-23
I had to revert to 1.5 after discovering that Thunderbird 2 under Ubuntu does not do e-mail filtering well, if at all.

---

### Post by nanotube on 2007-08-23
> **imbjr said:**
> I had to revert to 1.5 after discovering that Thunderbird 2 under Ubuntu does not do e-mail filtering well, if at all.

hm, mail filtering in 2.0 is about the same as in 1.5... what exactly didn't work for you? and which method did you use to install tb 2?

---

### Post by imbjr on 2007-08-24
> **nanotube said:**
> hm, mail filtering in 2.0 is about the same as in 1.5... what exactly didn't work for you? and which method did you use to install tb 2?
If I recall correctly it was an update through synaptic. For some reason, the email filters just would not work.

I think I shall try again ...

Correction: I can't have done it by the package manager as v2 is not listed. Mmm, must have been directly from Mozilla.

---

### Post by nanotube on 2007-08-26
> **imbjr said:**
> If I recall correctly it was an update through synaptic. For some reason, the email filters just would not work.

I think I shall try again ...

Correction: I can't have done it by the package manager as v2 is not listed. Mmm, must have been directly from Mozilla.

you could try using ubuntuzilla to install the latest tbird...
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by rambeaut69 on 2007-08-28
Thanks for the link to your repository Derevko. I didn't want to go the Automatix route. I really need to eventually learn the manual way, but this will suffice for now.

---

### Post by voidmain on 2007-08-29
> **Derevko said:**
> You can find a feisty backport in my repository [http://ubuntu.iuculano.it/](http://ubuntu.iuculano.it/)

[http://ubuntu.iuculano.it/dists/feisty/thunderbird/](http://ubuntu.iuculano.it/dists/feisty/thunderbird/)

For folks that use encryption quite a bit, this package doesn't come with any built-in certificates. If you want to use all of the built-ins, I would suggest installing the tarball from mozilla.org.

---

