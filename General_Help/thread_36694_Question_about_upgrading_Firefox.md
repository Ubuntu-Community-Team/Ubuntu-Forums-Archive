---
title: "Question about upgrading Firefox"
date: 2005-05-24
forum: General Help
---

### Post by mwdowns on 2005-05-24
Hello all. :)  This is kind of a mish-mash of questions revolving around my updating of Firefox.

I am trying to update Firefox.  Ubuntu came with version 1.0.2.  I was able to update to 1.0.4 using apt-get.  However, when I click on the "get more extensions" link in the extensions menu, I am redirected to a Mozilla page instructing me to update my Firefox.  I don't want to download the tarball they offer cause I can't seem to get those to work right.  i'd much rather use apt-get or an RPM (by the way, this is another question I have...Ubuntu is based on Debian, and I've seen these files with a .deb extension.  Is that the equivilant of an RPM file?  Meaning, all I have to do is click on the .deb file and it'll install?)

Using apt-get again, I get the following message:> mozilla-firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) hoary-backports/multiverse Packages (/var/lib/apt/lists/public.planetmirror.com_pub_ubuntu-backports_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problem
Firefox is not up to date (re the Mozilla extensions page).  And what's that last message about?

 I editted my /etc/apt/sources.list file to include the planet mirror repo.  My addition to the sources.list file looked like this: ```
deb http://public.planetmirror.com/pub/ubuntu-backports hoary-backports main universe multiverse restricted
deb http://public.planetmirror.com/pub/ubuntu-backports hoary-extras main universe multiverse restricted
``` Is that the correct way to do that?

Thanks for your help.

---

### Post by jasmuz on 2005-05-24
[QUOTE=mwdowns]Hello all. :)  This is kind of a mish-mash of questions revolving around my updating of Firefox.

I am trying to update Firefox.  Ubuntu came with version 1.0.2.  I was able to update to 1.0.4 using apt-get.  However, when I click on the "get more extensions" link in the extensions menu, I am redirected to a Mozilla page instructing me to update my Firefox.  I don't want to download the tarball they offer cause I can't seem to get those to work right.  i'd much rather use apt-get or an RPM (by the way, this is another question I have...Ubuntu is based on Debian, and I've seen these files with a .deb extension.  Is that the equivilant of an RPM file?  Meaning, all I have to do is click on the .deb file and it'll install?)

Using apt-get again, I get the following message:
Firefox is not up to date (re the Mozilla extensions page).  And what's that last message about?

 I editted my /etc/apt/sources.list file to include the planet mirror repo.  My addition to the sources.list file looked like this: ```
deb http://public.planetmirror.com/pub/ubuntu-backports hoary-backports main universe multiverse restricted
deb http://public.planetmirror.com/pub/ubuntu-backports hoary-extras main universe multiverse restricted
``` Is that the correct way to do that?

Thanks for your help.[/QUOTE]


Look what i did:
I added the Ubuntu backports to my /etc/apt/sources.list like this.

deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-extras main universe multiverse
restricted

Once i added those...i went to synaptic and got the Firefox upgrade.
To stop seeing the warning from the Firefox page i went to the tab and typed about:config, 
i looked for
general.useragent.vendorComment and changed it to the latest 1.0.4 and that's it!

---

### Post by wulf on 2005-05-24
I believe that the Ubuntu version of Firefox, while labelled 1.02, is up to date with the security fixes in release 1.04 of the mainstream version. Therefore, if you're only concerned about the security aspects, you don't need to do anything other than keep your system up to date with the Ubuntu repositories (rather than getting into the mess of mixing and matching different sources).

Wulf

---

### Post by d-n-r on 2005-05-24
hi,

i upgraded my firefox using the following repository:

deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-backports main universe multiverse restricted

when you have upgraded your firefox you have to change its config:

type "about:config" into the adressbar of firefox and search for "general.useragent.vendorSub" and change it to 1.0.4. then you will be able to install extensions.

for further information: [http://www.ubuntuforums.org/showthread.php?t=35961](http://www.ubuntuforums.org/showthread.php?t=35961) 

good luck

EDIT: sorry for posting the same solution. i think everyone posted at the same time :)

---

### Post by mwdowns on 2005-05-24
Thanks, everyone, for the input.

One thing about the repos...I noticed when I first got to this forum that there was a message from one of the admins to use mirror repos instead of the backports.ubuntuforums.org repos in order to keep traffic for that address low (something about package testing).  That's why I have a different repo vendor.  However, if it is better to use the repos you suggested (and there's no problem any more with traffic), then please tell me.

As for Firefox.  All is well now.  Thanks.

Lastly, I had a minor question in the OP, that I'd still like answered...do .deb packages work the same way as .rpm packages (i.e. self extracting installers)?  And with a debian setup, like Ubuntu, can I use .rpms?

---

### Post by reformedgeek on 2005-05-24
yes you can, but you need to use 'alien' to convert them to '.deb'
at least that's what i use.
also not 100% reliable.

try 'sudo apt-get install alien' if you havent already got it installed..

cheers

si \\:D/

---

### Post by Alex_K on 2005-05-25
[QUOTE=wulf]I believe that the Ubuntu version of Firefox, while labelled 1.02, is up to date with the security fixes in release 1.04 of the mainstream version.[/QUOTE]

there are still security problems in 1.02 which should be fixed in 1.04:

take a look on [this site](http://www.heise.de/security/dienste/browsercheck/demos/nc/mozdemo3.shtml) and click the "Test ausführen" link. 
it will create (and run) a file browsercheck.sh in you home directory.

---

### Post by lorap on 2005-05-25
hi friend!
i'll tell what you MUST do.
first of all download the firefox update file to your  Desktop.
remember, don't open it still with the archiver, just save it to the hard disk.
after you've it saved on your Desktop place a mouse over it then click the right button and choose "extract here" option.
the directory'll be created so you don't need anymore the archive file.
delete it.
now open the new directory by double clicking on it.
you'll see the only directory in it.
place a mouse over that directory then press the right button and choose "cut" option. after what place the mouse over the Destop, press the right button of the mouse and choose "paste" option. so the previous directory contains nothing anymore. so delete the old directory too :-)
now open the terminal window but don't maximize it so you'd be able see the directory on the Desktop.
now that you've the terminal window open write the next:

sudo sh

now double click on the directory you've pasted on the desktop so it'd open.
look in it and you'll see a file called "install-script" or "install-mozilla".
place a mouse over it and just grab it to the terminal window.
remember, there should be a distance between the script name and "sh"!!!!!
"sh" is like a command!
after what press enter.
what the installation process asks you to choose the installation directory choose "Custom" option and type this:

/usr/lib/mozilla-firefox

you'll be asked if the system should to delete the old directory, choose "Ok".
that's all :-)
have a nice day.
pavel

---

