---
title: "How to back up my system?"
date: 2008-07-09
forum: General Help
---

### Post by breadbin on 2008-07-09
I know how to backup stuff like photos, music etc but what about my system files. I have installed loads of synaptic apps and updates and was wondering can I save it all to a dvd or something like that? and if so how would i get it all back to where it was. does synaptic keep the debs that it downloads?

---

### Post by jamesapnic on 2008-07-09
They will be spread about the file system, but mainly in /usr and maybe some files in /etc depending on the app.  However yes the .deb files should be in:

> /var/cache/apt/archives/

---

### Post by bodhi.zazen on 2008-07-09
Well you have a few options. 

Start here : [uhelp]community/BackupYourSystem[/uhelp]

You can back up individual packages with something like AptOnCD

But IMO not necessary.

Try this :

First, make a list of installed packages. Open a terminal and enter these commands:

    ```
dpkg --get-selections | grep -v deinstall > ubuntu-files
```

Now you have got a list of all of your installed debs in a fairly small file. Transfer "ubuntu-files" to the installation you want to update (flash drive, email it to yourself, backup partition, etc).

Install Ubuntu on the new system.

Once Ubuntu is up and running, copy your ubuntu-files back into your home directory and do the following:

    sudo apt-get update

    sudo apt-get dist-upgrade

    sudo dpkg --set-selections < ubuntu-files

These commands tell the fresh install of Ubuntu what it needs to be installed. To install the packages .

```
sudo dselect
```

This will open up a dselect session. Type "I" and allow dselect to install of the the packages listed in your ubuntu-files document. When finished, type "Q" and hit the ENTER key to exit dselect.

---

### Post by ktrnka on 2008-07-09
If you want to save everything the way it is, including all installed applications, you might be interested in "remastersys"

[http://www.linuxmint.com/wiki/index.php/Remastersys]("http://www.linuxmint.com/wiki/index.php/Remastersys")

It says it's for Linux Mint Edition but it works fine on the other ubuntu versions.

---

