---
title: "Xubuntu program for internet cafe"
date: 2014-10-27
forum: General Help
---

### Post by neilajarn on 2014-10-27
Am looking for some software to use on Xubuntu machines in an internet cafe.

Ideally would like to be able to lock the screen, set a timer, record where users go online and delete any downloaded files/temporary internet files over night.

Is there such a program available ?

---

### Post by TheFu on 2014-10-27
So - I googled "internet cafe management linux" and 5 solid leads came back. These among other:
* Mkahawa
* Zencafe
* [https://sites.google.com/site/mikhoward/cybercafemanagementprograms](https://sites.google.com/site/mikhoward/cybercafemanagementprograms) is an article about someone looking too
* [http://serverfault.com/questions/244112/internet-cafe-software-for-linux](http://serverfault.com/questions/244112/internet-cafe-software-for-linux)
Never run one of these myself - interesting problem. What have you looked at already?

I'd probably do something with PXE boot and Ansible if those didn't work.  The built-in guest login account that Ubuntu has might be useful too.

I have run pfSense which has hotel modules. That could be part of the entire solution, but Idunno. I've been on the guest-side of the pfSense deployment and it was not trivial for some reason at that hotel. OTOH, where I setup pfsense everything "just worked", so perhaps the install team at that hotel wasn't so good?

---

### Post by slickymaster on 2014-10-27
*Moved to the ***General Help*** sub-forum*

---

### Post by neilajarn on 2014-10-27
Thanks, was only looking in the Ubuntu software centre.

---

### Post by TheFu on 2014-10-27
> **neilajarn said:**
> Thanks, was only looking in the Ubuntu software centre.

Often, SC is extremely limited for non-standard things - and sometimes standard stuff too.  Use **Synaptic** or **aptitude** to see many more options in the Ubuntu repos.

Going outside the repositories can be dangerous - definitely not recommended for people new to Linux (new is less than 2 yrs LINUX admin knowledge). Going outside repos will eventually lead to a system that cannot be patched. Sometimes that happens in a few months, sometimes in 1-2 yrs. Stay with LTS, existing repos for as much as possible.  Then only add 1,2 PPAs per install to limit risks.  

Sometimes to get the software we need, we have to install .deb files directly - these are the most dangerous and it means that updates are now manual.  The same applies to installing programs from source or tar.gz files. If installing through non-package manager techniques, do yourself a favor any for the installed software into /usr/local/ ... NOT whatever defaults a packager setup.

---

### Post by neilajarn on 2014-11-20
Am reopening this thread because its still unresolved.

I had a look at the software mentioned above yet was unable to get any of them working.

For now I would just like to have a batch file to delete the contents of the Documents, Pictures, Videos and Downloads folders when the pc is shut down. Since I am not versed in writing batch files, is there an application available that would help me do this ?

---

### Post by sudodus on 2014-11-20
Maybe you can get a ready-make ***linux kiosk operating system***. Search for it via the internet. One example is Webconverger.

---

### Post by TheFu on 2014-11-20
> **neilajarn said:**
> For now I would just like to have a batch file to delete the contents of the Documents, Pictures, Videos and Downloads folders when the pc is shut down. Since I am not versed in writing batch files, is there an application available that would help me do this ?

We don't call these batch files - we call them scripts. There are thousands of examples on your Linux machine and millions of examples on the internet.
The tool most used for creating these things is called an editor - vim, emacs are the historic versions for UNIX/Linux systems. You can use nano, geany, gedit or any of the 50 other editors as you like.

Here's an easy example:

```
#!/bin/bash
HOME="/home/userid"
rm -rf $HOME/Documents/*  $HOME/Pictures/*   $HOME/Videos/* $HOME/Downloads/*

```

Change the "userid" for your needs.

However, perhaps only letting them use the "guest" account would be better?  This account is auto created at login and destroyed at logout, leaving nothing behind. Don't know if Xubuntu supports that mode. Sorry.

---

### Post by neilajarn on 2014-11-21
> **sudodus said:**
> Maybe you can get a ready-make ***linux kiosk operating system***. Search for it via the internet. One example is Webconverger.

Had a look at these but are not really suitable as we need other apps such as Skype, a word processor, a media player and a burner (we're using VLC and K3B). In fact we have also put on a copy of Microsoft Word using Play on Linux as many customers prefer working with it.

The guest account is a good idea with regards to data not being stored but again the preinstalled apps with play on linux such as Microsoft Word do not appear under the guest account in Xubuntu.

---

### Post by TheFu on 2014-11-23
While LibreOffice isn't MS-Office, it does work reasonably well for simple uses.  AbiWord is another option - but many people are using Google-Docs more and more for this stuff.

I've used skype on Linux, but not recently.  I had it setup as replacement for our home phone and it mostly worked for a year or so. VLC is a great media player and K3b is fairly nice - both are good fines.  Google-Talk is another option - probably best used with Chrome.

---

### Post by neilajarn on 2014-11-25
The Libre Office works under the guest login. The only problem is the default save reverts back to ODT format. Under another user account this default save has been set to save in Microsoft Word format - it makes life a lot easier for customers who need to type a document and are not familiar with file formats especially when they email their document to someone with Microsoft Word which cannot open an ODT file.

So the question now is can the guest account be tweaked so that when its logged in the default save option for Libre Office Writer is set to Microsoft format ?

---

### Post by sudodus on 2014-11-25
I have not done this myself, so I only guess that it would be possible with some trial and error:

The settings of the guest account are set according to this link

[https://help.ubuntu.com/community/CustomizeGuestSession](https://help.ubuntu.com/community/CustomizeGuestSession)

(In my computer those settings are in **~/.config/libreoffice**, but it should be possible to do it 'automatically' via a 'Special purpose user'.)
> If the directory /etc/guest-session/skel exists and is not empty, its contents is copied to the home directory of the temporary user account. Otherwise the files in /etc/skel are copied. 
(In my computer only **/etc/skel** exists.)

See the instructions for 'Special purpose user'

Good luck :-)

---

### Post by neilajarn on 2014-11-26
That's working well now thanks. I followed the "Special purpose user" instructions and experimented a bit. Interestingly the guest account would not load with Play on Linux and Microsoft Word installed, so I uninstalled those and it now loads fine with all the desired tweaks. We will use Libre office and if necessary can use the free version of Microsoft word online or Google docs as has been mentioned here. 

Just one small problem in that previously some pcs were set to auto login. There are a couple of threads that suggest using this command to edit out the username but this doesn't work under the admin account for some reason - gksudo gedit /etc/lightdm/lightdm.conf 

The only other thing that remains is to find a way to record the websites each customer visits - its something required by law here. I suppose we could use Open DNS for that but would rather have a free alternative.

---

### Post by neilajarn on 2014-12-01
> **neilajarn said:**
> Just one small problem in that previously some pcs were set to auto login. There are a couple of threads that suggest using this command to edit out the username but this doesn't work under the admin account for some reason - gksudo gedit /etc/lightdm/lightdm.conf.

This would be because I didn't have gedit or leafpad installed :)

---

### Post by sudodus on 2014-12-02
It seems your problem is solved :KS

If you feel it is the case, please click on Thread Tools at the top of the page are mark this thread as SOLVED.

And welcome back with another thread, if/when you have another problem or question :-)

---

### Post by neilajarn on 2014-12-02
Its not quite solved.....

We still need a way to record the websites each guest visits

---

### Post by neilajarn on 2015-07-01
Thought I would just close this thread off even though the recording of websites has still not been done - all that needs doing is setting up on the router which can be done in conjunction with the internet provider.

Aside from that Xubuntu has been working very well at the internet cafe. We have this arrangement setup on 3 computers out of 14 (others are running Windows and an Apple Mac to offer choice to our customers). Its very stable and takes care of most customer needs. That covers basic internet surfing, downloading, documents, printing, scanning, Skype calls, image editing and some browser based online games.
 
Occasionally the connection to the wireless printers drops out - more a wireless issue than anything else - and is easily solved by logging in as administrator, removing the printer and adding it again, then logging back in as guest to solve the problem.

Once a week I will log in as administrator to run the updates.

Customers seem happy with it, especially as the guest account assures them when they log out any data they downloaded, copied or saved onto it will be deleted.

I can thoroughly recommend Xubuntu for use in an internet cafe but would suggest having a couple of Windows computers aswell; sometimes customers insist on using Windows software because they are familiar with it and more complex Microsoft Office files do not convert well to Libre Office. I was unable to get MS Office working with the guest session using Wine - that only seems to work as administrator.

Thanks to all that contributed to this thread and thankyou Xubuntu :).

---

