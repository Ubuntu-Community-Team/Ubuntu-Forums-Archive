---
title: "Aborted VMWare install now angry"
date: 2007-03-20
forum: General Help
---

### Post by Lor Boo on 2007-03-20
[COLOR="Green"]
Ahh re- reading - subject should have read "aborted vmware install - now vmware is angry with me"
sorry about that.[/COLOR]



I was following this guide:
[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

I'm still very new to Linux / Ubuntu.  
I am uncertain yet about file structure and manageing my partition spaces - as in - how much I have / have left / will need for this install...

Currently I have 3 partitions - system - swap - and a second hard drive mounted to ~/Desktop/media.
I wanted vmware to install the app part of it's self into the regular folders - where ever it wants to go..bin to bin... logs to logs .. where ever.
But I want to put the VMWare box it's self with whatever OS's in put in to that box to be placed onto the second hard drive

So as per below I goofed and tried to start over again:

```

**drinky@drinky:~/Desktop/media/vmware/vmware-server-distrib$ sudo ./vmware-install.pl**
[COLOR="Navy"]Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files?
[COLOR="DarkRed"][/usr/bin] /home/drinky/Desktop/media/vmware[/COLOR] *[COLOR="Green"]This is where I went wrong[/COLOR]*

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

Ignoring attempt to kill the installer with Control-C, because the uninstaller
has not been installed yet. Please use the Control-Z / fg combination instead.


[1]+  Stopped                 sudo ./vmware-install.pl
[/color]**drinky@drinky:~/Desktop/media/vmware/vmware-server-distrib$ sudo ./vmware-install.pl**
[COLOR="Navy"]A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Uninstalling the tar installation of VMware Server.

Unable to find the answer INITSCRIPTSDIR in the installer database
(/etc/vmware/locations). You may want to re-install VMware Server.

Execution aborted.
Failure
Execution aborted.
[/COLOR]
```

How do I reset this to start over?
And - when I do start over - does anyone know the wording of the question that determines where the actally 2'nd party OS will be stored?
For example - if putting in Win2k - I want all those win2k files on the second Hard Drive... but I 
don't know if it would be an obvious question... or one not so obvious as sometimes happens
- When I installed Wine, it didn't make that clear at all, and now it's home folder is on my primary 40 gig HD instead of the 160 gig drive i'd prefered to have had it on.

Thank you much.

---

### Post by zvacet on 2007-03-20
Maybe this gives you trouble
> A previous installation of VMware software has been detected.
If that is the case you need to uninstall all vmware installations you have.When you are clean try with this
[http://www.howtoforge.com/ubuntu_vmware_server]("http://www.howtoforge.com/ubuntu_vmware_server")

---

### Post by Lor Boo on 2007-03-20
I hear what you say.
It's the cleaning up the locked up attempted install part that has me stuck.

Any idea's on how to clear this out so I can try again?

---

### Post by kpkeerthi on 2007-03-20
delete /etc/vmware and try again

---

### Post by haricharan on 2007-03-20
try moving the /etc/vmware folder to another folder maybe ur home folder
and try removing the package..it wud remove some files and then it wud say /etc/vmware missing..at that point u put the folder back and try removing the package again....i faced a similar problem and i did this..it worked for me..

---

### Post by Lor Boo on 2007-03-21
Thanks - 
sudo mv /etc/vmware /etc/vmware.failed
worked just fine.

The system is now asking me
```

In which directory do you want to keep your virtual machine files?
[/var/lib/vmware/Virtual Machines]

```

Is this where the vm'ed OS would be placed?
or is that further on?

---

### Post by Lor Boo on 2007-03-21
Never mind
I guessed that it wasn't... and now it appears that it was..

No matter, it's installed now and tonight I'll try loading up an OS.

Thank you each for your help when I was stuck.
I didn't find anything online to help but now... i'm a little wiser.
Thanks

---

