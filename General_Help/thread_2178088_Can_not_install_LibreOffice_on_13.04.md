---
title: "Can not install LibreOffice on 13.04"
date: 2013-10-01
forum: General Help
---

### Post by fbugnon on 2013-10-01
I was having some problems with the original LibreOffice from Ubuntu 13.04 crashing very frequently, so I decided to install **version 4.1** by adding a the [libreoffice/PPA]("https://launchpad.net/~libreoffice/+archive/libreoffice-4-1") from **Lauchpad**.

But I had event worst problems with that, so I excluded the PPA from my software sources, removed LibreOffice, deleted [FONT=Courier New].config/libreoffice[/FONT], made an apt-get [FONT=Courier New]update[/FONT], [FONT=Courier New]autoclen[/FONT], [FONT=Courier New]autoremove[/FONT] and try to (re)install the original version of 13.04, but I'm getting the dependency error below:

```
$ sudo apt-get install libreoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libreoffice : Depends: libreoffice-base but it is not going to be installed
               Depends: libreoffice-calc but it is not going to be installed
               Depends: libreoffice-core (= 1:4.0.2-0ubuntu1) but 1:4.1.1-0ubuntu1~raring1 is to be installed
               Depends: libreoffice-draw but it is not going to be installed
               Depends: libreoffice-filter-mobiledev but it is not going to be installed
               Depends: libreoffice-impress but it is not going to be installed
               Depends: libreoffice-math but it is not going to be installed
               Depends: libreoffice-report-builder-bin but it is not going to be installed
               Depends: libreoffice-writer but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

I've also try:

```
$ sudo apt-get -f install libreoffice
```

and

```
$ sudo dpkg --configure -a
```

but they didn't help me.


I must say I'm using **Oracle Java** (not OpenJDK), don't know if this is related.

Any help is greatly appreciated.  Many thanks!

(sources.list is attached just in case)

---

### Post by slickymaster on 2013-10-02
To install LibreOffice 4 you will need to remove all previous versions. At a terminal window run the following:```
sudo apt-get remove --purge libreoffice-core libreoffice-common
sudo apt-get autoremove --purge
```

Then install it:```
sudo add-apt-repository ppa:libreoffice/libreoffice-4-1
sudo apt-get update
sudo apt-get dist-upgrade
```

Another way would be to download the LibreOffice deb archive from its website, extract it, and inside the folder where the deb files are extracted there should be a folder called "desktop-integration" with a deb inside - copy this deb into the folder where all the other deb files are located and run the following command from a terminal to install it:```
sudo dpkg -i /path/to/libreoffice/DEBS/*.deb
```
In any cases it's recommend to remove all LibreOffce previous versions.

---

### Post by fbugnon on 2013-10-02
Thanks for your reply and very comprehensive answer, [slickymaster]("http://ubuntuforums.org/member.php?u=1753126").

I'm sorry if my post wasn't very clear, but what I want to do is downgrade from 4.1 to 4.0 or whatever version of LibreOffice came with 13.04.
I already removed libreoffice and the PPA for 4-1, but cannot (re)install LibreOffice due to the dependency error above.

---

### Post by SWGraphics291 on 2013-10-02
[LIST=1]
[*]Install Synaptic Code: sudo apt-get install synaptic 
[*]Uninstall libreoffice Code: sudo apt-get purge libreoffice 
[*]Add the Libreoffice 4.0 ppa Code: sudo add-apt-repository ppa:libreoffice/libreoffice-4 
[*]Refresh the repositories list Code: sudo apt-get update 
[*]Install LO 4.0 Code: sudo apt-get install libreoffice=1:4.0-0ubuntu1~precise1~ppa1 . I never done this but there is information on how to install specific version [here]("http://askubuntu.com/a/92021/27968"). 
[*]Open Synaptic, search for Libreoffice, select the package and from the package menu select **Lock version**. 
[/LIST]

Credit all to To Do on askUbuntu URL: [http://askubuntu.com/questions/299137/how-to-downgrade-from-libreoffice-4-0-to-3-6](http://askubuntu.com/questions/299137/how-to-downgrade-from-libreoffice-4-0-to-3-6)

---

### Post by fbugnon on 2013-10-02
Thanks for your reply, starwars29.

I've try, but...

On **item 3** the correct ppa is ppa:libreoffice/libreoffice-4**-0**
This was easy, on error I checked on [Launchpad's PPA page]("https://launchpad.net/~libreoffice/+archive/ppa").

On **item 5**, I received the error:
```
E: Version '1:4.0-0ubuntu1~precise1~ppa1' for 'libreoffice' was not found
```

So I tried plain simple:
```
$ sudo apt-get install libreoffice
```
since I already had installed the PPA for 4.0, but then I received the same (or similar) dependency error:

```
$ sudo apt-get install libreoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libreoffice : Depends: libreoffice-core (= 1:**4.0.5**~rc2-0ubuntu1~raring1~ppa1) but 1:**4.1.1**-0ubuntu1~raring1 is to be installed
               Depends: libreoffice-filter-mobiledev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

For now, my solution, since I can't stand not having Writer, was to re-add ppa for LO 4.1 and then reinstall it without a problem.  But I still want to downgrade to 4.0... keep trying.

It seems to me (from the code above) that problem really has to do with the libreoffice-core (4.0.5 vs. 4.1.1), because it seems no to follow the downgrade of all other packages of LO...

Thanks anyway.

---

### Post by slickymaster on 2013-10-02
> **fbugnon said:**
> Thanks for your reply and very comprehensive answer, [slickymaster]("http://ubuntuforums.org/member.php?u=1753126").

I'm sorry if my post wasn't very clear, but what I want to do is downgrade from 4.1 to 4.0 or whatever version of LibreOffice came with 13.04.
I already removed libreoffice and the PPA for 4-1, but cannot (re)install LibreOffice due to the dependency error above.

fbugnon, I really thought that you wanted to install 4.1.

Anyway, after some research I found out, at [https://wiki.documentfoundation.org/ReleaseNotes/4.1#Most_Annoying_Bugs](https://wiki.documentfoundation.org/ReleaseNotes/4.1#Most_Annoying_Bugs), that when downgrading LibreOffice from 4.1 to 4.0:> If you have no menus on a Debian/Ubuntu-based system or trouble with the install, you likely didn’t uninstall the distro version of LibreOffice completely. You will need to make sure all the binary packages listedin the [“libreoffice” package in Ubuntu]("https://launchpad.net/ubuntu/+source/libreoffice") are uninstalled.So, you can try the following```
sudo apt-get purge libreoffice*  
sudo apt-get purge openoffice.org-dtd-officedocument1.0 python-uno python3-uno uno-libs3 ure
```If everything works smoothly all you have to do afterwards is to install the 4.0 version by adding the main LibreOffice PPA which will get updates not only with LibreOffice 4.0.x but also with newer versions:```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by SWGraphics291 on 2013-10-03
On **item 5**, I received the error:
 	

 	```
E: Version '1:4.0-0ubuntu1~precise1~ppa1' for 'libreoffice' was not found
```


Use 1:4-0ubuntu1~precise1~ppa1 or 1:4.0.0-0ubuntu1~precise1~ppa1

---

### Post by SWGraphics291 on 2013-10-03
Still figuring out quotes.

---

### Post by fbugnon on 2013-10-03
Thanks for your help, slickymaster.

I follow your advice:

> **slickymaster said:**
> ...So, you can try the following```
sudo apt-get purge libreoffice*  
sudo apt-get purge openoffice.org-dtd-officedocument1.0 python-uno python3-uno uno-libs3 ure
```

And this seems to help me completely purge LO and dependencies and allowed me to re-install previous versions of LO.

After having done this, I added the [PPA for the pre-release]("https://launchpad.net/~libreoffice/+archive/libreoffice-prereleases") (just for testing), but strangely, this resulted in a installation of **4.1.0 rc3** (which was OK, but I expected something fresher than the current stable **4.1.1**).

So I went ahead and purge everything again and this time I added the [PPA for LO 3.6]("https://launchpad.net/~libreoffice/+archive/libreoffice-3-6") (of course, excluding previous PPAs).  And once again I had a strange result, for I got installed LO **4.0.2.2**.

But nonetheless, this solved my issue, for I was finally able to downgrade.

Thanks a lot! 

SOLVED:)

---

