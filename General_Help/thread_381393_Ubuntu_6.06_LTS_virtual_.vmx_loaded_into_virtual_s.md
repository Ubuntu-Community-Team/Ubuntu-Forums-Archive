---
title: "Ubuntu 6.06 LTS virtual .vmx loaded into virtual server what next?"
date: 2007-03-10
forum: General Help
---

### Post by 3595lover on 2007-03-10
I've loaded this [http://www.vmware.com/vmtn/appliances/directory/596]("http://www.vmware.com/vmtn/appliances/directory/596") into vmwares vm server

After I log in with user name: ubuntu , pass: ubuntu.  I'm stuck.

What do I typpe to get into kde or gnome?  

Can you folkes give me some links to learn the command line most important stuff?  I'm on a fast track to get started.

I don't have to much trouble inside the graphical part of ubuntu on its live cd.

But this virtual disk installation has got me stumped.

Thanks all.

---

### Post by zvacet on 2007-03-11
You installed server edition witch comes without GUI.If you want to install it type```
sudo aptitude install ubuntu-desktop
```
if you want GNOME or 
```
sudo aptitude install kubuntu-desktop
```
if you prefering KDE
This commands will pull many more packages.Why did´t you download Ubuntu from 
[http://www.ubuntu.com/]("http://www.ubuntu.com/")
Take Ubuntu Desktop alternate Cd,bacause with it you can convert esktop to server and choose between GNOME or KDE.All that is covered in this forum,just go step by step.

---

### Post by 3595lover on 2007-03-11
Thanks.

What do you type to start the kde or gnome enviroment after they are installed?

---

### Post by zvacet on 2007-03-11
For GNOME
```
sudo /etc/init.d/gdm start
```
For KDE
```
sudo /etc/init.d/kdm start
```

---

### Post by 3595lover on 2007-03-11
Hi.  I entered what you said got this:

ubuntu@ubuntu:~$ sudo /etc/init.d/kdm start
sudo: /etc/init.d/kdm:  command not found

I entered the same for gnome.  Why do you have to enter sudo before?

Ohh.  I did d/l ubuntu and have done the live cd thing.  It was not in shell mode however.  Just graphical.

Thanks.

---

### Post by llamakc on 2007-03-11
Have you installed the 'ubuntu-desktop' or 'kubuntu-desktop' package inside of the vm instance of Ubuntu yet?

---

### Post by 3595lover on 2007-03-11
Yes.  I did get some errors but I didn't think they pertained to the installation of kde or gnome.

I got some temporary failure resolving 'us.archive.ubuntu.com' Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main latex-xft-fonts 0.1-5

There were sdeveral of these.

Other than that I thought everything went ok.

Thanks.

---

### Post by llamakc on 2007-03-11
From inside the vm instance, you want to start the login manager, which appears to be kdm from what you typed earlier.

```

sudo /etc/init.d/kdm start

```

---

### Post by 3595lover on 2007-03-11
Still not working.  It does ask for my password but after that it gives the command not found error.

I've added an image of my vm image.

Thanks.

---

### Post by llamakc on 2007-03-11
From the commandline (in your Ubuntu vm) what's the output of:

```
dpkg -l | grep kubuntu-desktop
```

---

### Post by 3595lover on 2007-03-11
Here's what I get.



Thanks.

---

### Post by llamakc on 2007-03-11
You need to cut-n-paste from what I typed, or spell the commands properly.

It is

```
dpkg -l | grep kubuntu-desktop
```not,[B] kuubuntu-desktop

[/B]That's the command "dpkg" the dash - and a lowercase L, "dpkg -l", next that is the pipe character. On my keyboard it is achieved with SHIFT-backslash. 

cut and paste THIS:

```

dpkg -l | grep kubuntu-desktop

```If you get zero results, you did not install it yet.*** Earlier it was suggested you install it. Have you? ***

Maybe you should just do this: 1. Decide if you want Gnome, KDE, or XFCE. Then, install 

For Gnome:

```

sudo apt-get install ubuntu-desktop

```For KDE

```

sudo apt-get install kubuntu-desktop

```For XFCE

```

sudo apt-get install xubuntu-desktop

```

---

### Post by 3595lover on 2007-03-12
Yes, I did install both as you said.

sudo aptitude install ubuntu-desktop

sudo aptitude install kubuntu-desktop

I just did it again to get the results in the attachments.

It loaded a bunch of stuff.  Told me that 870 modules or packages installed.  Then got a bunch of failure to resolve errors.

There may be something wrong with my net connection in vm ware server.  I don't know.  Under settings it is set to nat.  Is this correct?

The vm's hd size is 8gb.  It is set up as SCSI.  I think this was set by default by vm server.

What's the diff. between

sudo aptitude install ubuntu-desktop

sudo aptitude install kubuntu-desktop

and

sudo ap-get install ubuntu-desktop

sudo ap-get install kubuntu-desktop

I'v attached images of the install and some of the errors.

How do you scroll or down up in the vm window?  Copy and paste?

Thank you.

---

### Post by llamakc on 2007-03-12
I never suggested that you install both ubuntu-desktop and kubuntu-desktop. I suggested you CHOOSE one or the other.

I'm unfamiliar with Windows or VMWare on Windows so I can't help you with any of that.  

Here is a great link on the differences between the package management systems in Ubuntu: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

HERE is what I would do if I were you.

From the terminal run:

```
sudo apt-get -f install
```

The above command is going to ensure that any packages that have not installed yet, do so. I can't help you with your network problems with VMWare and Windows. I can tell you that my /etc/apt/sources.list does not have the "us." in the addresses. I always remove them.

If you choose to edit that, you would want to reload the package index with:

```
sudo apt-get update
```

before running the command above:

```
sudo apt-get -f install
```

Then, if you have actually installed any of the *-desktop metapackages, you would be able to fire up a login manager.

I think it is important to figure out what it is you actually want or expect with all of this. If you have not done much configuring, why not just reinstall Ubuntu inside the VMWare, and use the LiveCD (there's an install option on the Desktop after it starts up).

---

### Post by 3595lover on 2007-03-12
I couln't install in vm server because it doiesn't detect my usb cd burner/drive.  How do you have the network setting in vm server on linux?  maybe they are similar in pc.

Thanks.

---

### Post by llamakc on 2007-03-12
The inability of your vmware install being able to see your USB cd drive has nothing to do with the network.

My VMWare network is set as 'bridged'.

---

### Post by 3595lover on 2007-03-13
Yes. I know this, but it was the reason why I could not install ubuntu in vm server or run the live cd.

I had my network setting on NAT.  I set it to bridged & willl restart to see if that works.

Thanks.

---

