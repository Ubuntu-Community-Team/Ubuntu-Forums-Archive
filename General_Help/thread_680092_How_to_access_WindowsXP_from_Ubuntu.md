---
title: "How to access WindowsXP from Ubuntu"
date: 2008-01-27
forum: General Help
---

### Post by maxhoward on 2008-01-27
I am running a dual boot PC with WindowsXP and Ubuntu.  I would like to run a couple of Windows applications (MS Access and Quicken) from Ubuntu.  Is this possible?  If so, how?
Is there a tutorial on this?

---

### Post by omi291 on 2008-01-27
> **maxhoward said:**
> I am running a dual boot PC with WindowsXP and Ubuntu.  I would like to run a couple of Windows applications (MS Access and Quicken) from Ubuntu.  Is this possible?  If so, how?
Is there a tutorial on this?

You can run windows applications using wine([http://www.winehq.org/](http://www.winehq.org/)). if you do install it, here's the FAQ:
[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)

---

### Post by maxhoward on 2008-01-30
OK, after reading and rereading the Wine information found on that site, I concluded that I have to Install the windows apps I want into Linux as opposed to accessing these apps that are already installed in Windows. Is this correct?   There is mention in the Wine info of using the "installer" but I never could found out where that is or how to access or run it.  I haven't tried installing the app from its CD while operating in the Ubuntu desktop. Should I do that?  The Wine info doesn't seem too clear for a newbie like me.

Thanks for any help.

---

### Post by philidox on 2008-01-30
Aside from wine you can run virtual machines thru a program like virtual box or vmware server.  I HIGHLY recommand virtual box its completely free and I believe its open source.  You can get the one outta the repository but I recommend going to the website and download the .deb file and install it on your machine.  Running a virtual machine can suck up a lot of your computers processing power because your running two or more operating systems at once.  However the biggest advantage is that you don't have to reboot just to load your other os and you'll probably eliminate the need for a dual boot system. You just load your other os when you need it.  Ever since I've had my virtual machine I have not had the need for my dual boot function, trust me its nice!!!

Here is the url for innotek virtual box:
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Here is the installation guide:
[http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/](http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/)

If your usb ports on virtual machine arent working here is the url:
[http://www.blog.arun-prabha.com/2007/10/26/usb-not-working-with-virtualbox-in-ubuntu-7-10-gutsy-gibbon/](http://www.blog.arun-prabha.com/2007/10/26/usb-not-working-with-virtualbox-in-ubuntu-7-10-gutsy-gibbon/)

---

### Post by zvacet on 2008-01-30
I personaly never tryed it but maybe [this](http://ubuntuforums.org/showthread.php?t=380699&highlight=vmplayer) will be helpfull to you.

---

