---
title: "Install VirtualBox with no internet connection"
date: 2007-07-30
forum: General Help
---

### Post by jamieh on 2007-07-30
Can someone tell me how to install VirtualBox or VMware Server? My computer has _NO internet connection._ My OS is Ubuntu 7.04 Feisty Fawn
I _DO_ have access to a Windows/Ubuntu dual-boot PC with an internet connection, and I do have a 1GB flash drive, so I can transfer files to the PC with no internet connection.

---

### Post by FleetAdmiral74 on 2007-07-30
There is a thing called apt-on-CD, might give that a try. Not used it outside Linux, but it *is* used to install programs without internet.

---

### Post by pak33m on 2007-07-30
jamieh,

On the Windows/Ubuntu dual-boot PC perform the following (at Ubuntu terminal):

```
wget http://www.virtualbox.org/download/1.4.0/virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb
```

Then copy virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb to your flash drive and install it on the PC with NO internet access.

On the PC with NO internet access perfor the following (in the terminal):

```
sudo dpkg -i virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb
```

You can follow along here:

[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)
[http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html](http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html)

Hope this helps!

---

### Post by jamieh on 2007-07-31
> **pak33m said:**
> jamieh,

On the Windows/Ubuntu dual-boot PC perform the following (at Ubuntu terminal):

```
wget http://www.virtualbox.org/download/1.4.0/virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb
```

Then copy virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb to your flash drive and install it on the PC with NO internet access.

On the PC with NO internet access perfor the following (in the terminal):

```
sudo dpkg -i virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb
```

You can follow along here:

[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)
[http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html](http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html)

Hope this helps!

I am at the screen where I have to accept the License Aggreement, but how do I say "Yes"? Clicking OK or pressing Enter does nothing.

---

### Post by ader10 on 2007-12-30
If you haven't figured out yet, you have to scroll all the way to the bottom of the license. That's because they want you to read it.

---

