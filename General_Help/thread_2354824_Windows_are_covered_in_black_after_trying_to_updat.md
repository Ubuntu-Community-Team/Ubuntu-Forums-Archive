---
title: "Windows are covered in black after trying to update graphics drivers"
date: 2017-03-06
forum: General Help
---

### Post by mic3 on 2017-03-06
I am using Ubuntu 16. I attempted to install my graphics drivers from a PPA

I remember I was trying the suggestions here:

[http://askubuntu.com/questions/501560/how-to-update-opengl-driver-on-ubuntu-14-04-lts](http://askubuntu.com/questions/501560/how-to-update-opengl-driver-on-ubuntu-14-04-lts)
[http://askubuntu.com/questions/691271/upgrading-to-latest-version-of-opengl-on-ubuntu-15-10](http://askubuntu.com/questions/691271/upgrading-to-latest-version-of-opengl-on-ubuntu-15-10)

My computer was running fine until I put it in suspend mode. After I turned it back on, now whenever I click on things, I get this black box surrounding it, such as here:

[http://imgur.com/LlT9Fah](http://imgur.com/LlT9Fah)

I  can't even type things in the terminal because I'll get that black box.  If I restart or shut down and turn it back on, I get the same problem

Looking at my `bash_history` file, I see that the possible commands I ran that could've caused this problem were:

> sudo apt-get install libfontconfig1
sudo apt-get install mesa-common-dev
sudo apt-get install libglu1-mesa-dev -y
sudo update-mime-database /usr/share/mime


after switching to a text terminal, I typed

> 
    sudo apt-get install ppa-purge
    sudo ppa-purge ppa:oibaf/graphics-drivers

but got 

    > W: The repository 'http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu xenial Release' does not have a Release file.
    E: Failed to stat /var/lib/apt/lists/partial/cran.rstudio.com_bin_linux_ubuntu_xenial_InRelease - pkgAcqTransactionItem::TransactionState-stat (2: no such file or directory)
    apt-get update failed for some reason`

 when I go to Software and Updates, I can't uncheck the PPA because the window turns black

And when I type `gksu gedit /etc/apt/sources.list`, I get
> 
     Gtk-WARNING **: cannot open display


It looks like this bug has affected others and still hasn't resolved! : [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1292830](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1292830)

Can anyone help?

---

### Post by QIII on 2017-03-06
Hello!

It does not look like you have told us the manufacturer and model of your GPU.  That would be helpful.

---

### Post by mic3 on 2017-03-07
lspci | grep VGA

returns

VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)

---

### Post by mic3 on 2017-03-07
Bump

---

