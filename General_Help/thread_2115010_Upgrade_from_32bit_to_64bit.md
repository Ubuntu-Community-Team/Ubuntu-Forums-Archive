---
title: "Upgrade from 32bit to 64bit?"
date: 2013-02-11
forum: General Help
---

### Post by pretty_whistle on 2013-02-11
I have Ubuntu 12.04 LTS 32bit.  Can I simply upgrade to the 64bit version or does the 64bit installer offer that?

---

### Post by Bufeu on 2013-02-11
No, you must do a clean install.

---

### Post by MoebusNet on 2013-02-11
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by pretty_whistle on 2013-02-11
If it helps I'm adding this:

My current laptop which runs 12.04 LTS 32bit is gonna need replacing but all the computers I've found come in 64bit so I want to know if I can simply upgrade what I have now to the 64bit.

---

### Post by MoebusNet on 2013-02-11
If I understand your question correctly, what you will need to do is:

1) Select and purchase an Ubuntu-compatible notebook

2) Back up all of your data from your old notebook (I prefer an external drive to back up my data)

3) Install *buntu 64-bit (Ubuntu, Kubuntu, Xubuntu, Lubuntu or whatever) to your new notebook.

4) Restore your data to your new notebook

The data files shouldn't care whether you have 32-bit or 64-bit installed.

---

### Post by offgridguy on 2013-02-11
If it helps, you can use 32 bit on a 64 bit computer, I have done it.

---

### Post by pretty_whistle on 2013-02-11
> **MoebusNet said:**
> If I understand your question correctly, what you will need to do is:

1) Select and purchase an Ubuntu-compatible notebook

2) Back up all of your data from your old notebook (I prefer an external drive to back up my data)

3) Install *buntu 64-bit (Ubuntu, Kubuntu, Xubuntu, Lubuntu or whatever) to your new notebook.

4) Restore your data to your new notebook

The data files shouldn't care whether you have 32-bit or 64-bit installed.
If I do this I cant transfer my programs over, can I?

---

### Post by pretty_whistle on 2013-02-11
> **offgridguy said:**
> If it helps, you can use 32 bit on a 64 bit computer, I have done it.
This is probably what I'll have to do.

---

### Post by MoebusNet on 2013-02-11
No, but almost every program available in 32-bit will be available in 64-bit from the same place.

---

### Post by pretty_whistle on 2013-02-11
> **MoebusNet said:**
> No, but almost every program available in 32-bit will be available in 64-bit from the same place.
That's what I thought.

---

### Post by pretty_whistle on 2013-02-11
Ok, this is solved for me.  I'll just use my 32bit on the 64bit new laptop.

:-) Thanks everyone for your input.

---

### Post by oldfred on 2013-02-11
You can make a list of all installed apps and reinstall. This is just a text list. If upgrading to a new version you may want to review and delete any apps that may have changed like several versions ago the standard was OpenOffice and now it is LibreOffice. You would not want to reinstall OpenOffice as you have LibreOffice. It is a long list as it includes all the support programs also.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by Slim Odds on 2013-02-11
> **pretty_whistle said:**
> Ok, this is solved for me.  I'll just use my 32bit on the 64bit new laptop.

:-) Thanks everyone for your input.
Why would you want to install the 32 bit version on a new 64 bit machine?

Don't waste your resources, install the 64 bit version and live it up.

Otherwise you're wasting RAM; wasting CPU... 64 bit rules!

---

### Post by hansdown on 2013-02-12
> **pretty_whistle said:**
> Ok, this is solved for me.  I'll just use my 32bit on the 64bit new laptop.

:-) Thanks everyone for your input.

Hi buddy!

Just a suggestion, (you can choose from the "large volume" of help options), which are supplied, or maximize the benefits of 64bit, by downloading, and installing the 64bit version.

Either way, you will end up the happy, carefree person, that I have come to know, and respect.

---

