---
title: "Help needed installing DEB files from Codeblocks"
date: 2008-04-09
forum: General Help
---

### Post by Yellowage on 2008-04-09
Hi,

    I'll need your help on this issue.
    I am trying to install Codeblocks(a cross platform IDE) onto my Ubuntu desktop. After extracting the tz file, I have left with the following DEBs.

codeblocks_8.02-0ubuntu1_i386.deb
codeblocks-contrib_8.02-0ubuntu1_i386.deb
codeblocks-dbg_8.02-0ubuntu1_i386.deb
codeblocks-dev_8.02-0ubuntu1_i386.deb
libcodeblocks0_8.02-0ubuntu1_i386.deb
libwxsmithlib0_8.02-0ubuntu1_i386.deb
libwxsmithlib0-dev_8.02-0ubuntu1_i386.deb

When I try to use the command:

```

sudo dpkg -i "all the deb files one by one"

```
I am repeatedly prompted with the error message:

```

Selecting previously deselected package codeblocks.
(Reading database ... 92148 files and directories currently installed.)
Unpacking codeblocks (from codeblocks_8.02-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of codeblocks:
 codeblocks depends on libcodeblocks0 (= 8.02-0ubuntu1); however:
  Package libcodeblocks0 is not installed.
dpkg: error processing codeblocks (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 codeblocks

``` 

Anyone would like to advice on how can I resolve the dependency problem?

---

### Post by jken146 on 2008-04-09
Start by installing libcodeblocks0_8.02-0ubuntu1_i386.deb then install codeblocks_8.02-0ubuntu1_i386.deb

---

### Post by drdos2006 on 2008-04-10
Here is how I did it.

To install Code::Blocks on Ubuntu 7.10 64bit OS.

Create a temp folder and copy downloaded file to a temp folder.
Unzip the downloaded zipped file and expand Code::Blocks to *.deb files with a mouse double-click.
Install each of the *.deb files, install with a mouse double-click..

Enter terminal mode. Copy all the *.deb files to /var/cache/apt/archives.
	sudo cp /home/MyName/temp/*.deb  /var/cache/apt/archives
Exit terminal mode. 
Using System -> Administraton -> Synaptic Package Manager, search for “codeblocks”.
Highlight “codeblocks”, right mouse click and drop down to “Mark Suggested for installation”.
The libraries for installation will be “libwxgtk2.8-dev” and “wxcommon”. 
Apply the installation. Close the package manager.
Run Code::Blocks.
regards

---

### Post by jocko on 2008-04-10
Wouldn't this install them all?
```
sudo dpkg -i *.deb
```

---

### Post by drdos2006 on 2008-04-10
It would appear not.
The workaround above is because after unzipping and installing from the temp folder, my Synaptics Package Manager could not find "codeblocks" in the list of archives. 
The workaround above works for me, it may help someone else.
regards

---

### Post by pasgui on 2008-04-10
Hi,

You can find how to install CB on Ubuntu for i386/amd64 here: [http://lgp203.free.fr/spip/spip.php?article1](http://lgp203.free.fr/spip/spip.php?article1)

Remember, you have to add also the wxWidgets repository.

Best regards, pasgui

---

