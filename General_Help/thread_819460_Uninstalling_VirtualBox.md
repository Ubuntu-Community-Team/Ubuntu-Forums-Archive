---
title: "Uninstalling VirtualBox"
date: 2008-06-05
forum: General Help
---

### Post by webcoded612 on 2008-06-05
I downloaded VirtualBox and installed it.  It doesn't boot (I imagine I did somethng wrong), so I am asking either for help getting it to run, or removing it.  Here's what I did:

1.  Downloaded the .run file from the VirtualBox site (for Linux i386).

2.  Entered the following code:

```
cd ~/Desktop
sudo chmod +x vbox.run (I renamed the file to make it easier to type)
sudo ./vbox.run

```

Everything installed OK, and it put an entry into the Applications/System Tools menu, but when I click on it...nothing.  I checked the processes, and it's definitely not running.  I even tried Alt+F2, virtualbox and vbox, and it says they're not found.  

No errors with install.  Am I missing something?  Do I need to install it again?  Or is there a way I can remove it?  

Thanks!

---

### Post by pointone on 2008-06-05
You will need to make your user a member of the "vboxusers" group:

```
sudo usermod -G vboxusers -a <username>
```

...log out and back in afterwards and try again.

---

### Post by webcoded612 on 2008-06-05
> **pointone said:**
> You will need to make your user a member of the "vboxusers" group:

```
sudo usermod -G vboxusers -a <username>
```

...log out and back in afterwards and try again.

Forgot to mention that.  I did that.  Went to Users and Groups, unlocked it, clicked Manage, found vboxusers, clicked properties, and checked the box next to my username.  Then I logged out and back in.  Still nada.  

Sorry for leaving that out!

---

### Post by webcoded612 on 2008-06-05
Anybody?  I'd really like to get this working....

---

### Post by webcoded612 on 2008-06-05
Is there some other forum I can go to for help?  Or an article I can read?  

Anything...?

---

### Post by pointone on 2008-06-05
Try running the command "VirtualBox" (capital V and B) from the command line and see if any errors are raised.

---

### Post by NikoC on 2008-06-05
And what if you would type VirtualBox (mind the capital V and B) in the ALT + F2 dialogue box?

Also an other option would be to start it in a terminal window (just open a terminal and type VirtualBox there, if it doesn't work, you might get some feedback in the terminal window to see if something is actually wrong).

Cheers

edit: as usual, as I was typing somebody beat me to it ;)
edit2: @ pointone: great minds think alike ;)

---

### Post by webcoded612 on 2008-06-05
> **pointone said:**
> Try running the command "VirtualBox" (capital V and B) from the command line and see if any errors are raised.

Didn't know about the case sensitivity.  Thanks.  

I got this error when I ran it in terminal:

```
james@ubuntu:~$ VirtualBox
/opt/VirtualBox-1.6.0/VirtualBox: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

```

I would assume I need the libqt-mt library?  How could I get that?

Thanks for the help!

---

### Post by forestpixie on 2008-06-05
Can I just ask why you didn't download the deb file if you got it from an external source? 

It would have been a lot easier.

---

### Post by webcoded612 on 2008-06-05
> **forestpixie said:**
> Can I just ask why you didn't download the deb file if you got it from an external source? 

It would have been a lot easier.

The last time I installed it that's what I did.  Couldn't find the .deb file this time, and I didn't want the OSE in the repositories.  

I know it would have been much easier.  Of course, adding/removing programs shouldn't be this difficult, either.  :P

Any ideas on how to fix this?  Thanks everybody.  :)

---

### Post by forestpixie on 2008-06-05
HAve you tried to install what it wants, other than that no idea I'm afraid. Maybe just get the deb and reinstall it.

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

---

### Post by webcoded612 on 2008-06-05
> **forestpixie said:**
> HAve you tried to install what it wants, other than that no idea I'm afraid. Maybe just get the deb and reinstall it.

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

Did that just now, and it says I have to remove the old installation first.  I see why I couldn't get the .deb, too...I was choosing Linux i386 instead of Ubuntu 8.04.  

I can't believe nobody knows how to do this?  I mean, I'm still a Linux noob, but surely some of the experienced users here know how to uninstall a program?  

I don't mean to whine, but usually this forum is really good, and it's a big let down when it's not.  

Thanks to those who have tried to help already.  Now I just need to figure out how to remove this installation.  I hope it doesn't come to another reformat of the entire drive, but that seems the easiest way to get things done in Linux when you can't find any help.  :(

---

### Post by webcoded612 on 2008-06-05
Can somebody please help me with this?  Or at least point me to a place where I can find help?

---

### Post by NikoC on 2008-06-06
From the manual on the VirtualBox website I understand that the software depends on a package called qt3... I'm currently not on my ubuntu machine, but what if you open synaptic and search for qt3 and install that?

---

### Post by forestpixie on 2008-06-06
From the manual

>   The installer must be executed as root with either install or **uninstall** as the
first parameter.

So reverse what you did to install it, navigate to the file and do this I assume - 

```
sudo ./VirtualBox.run uninstall /opt/VirtualBox
```

> I don't mean to whine, but usually this forum is really good, and it's a big let down when it's not.

If people are not looking at the forum at the time that you're thread is there then it won't be seen, the forum isn't a replacement for searching, all I did was get the manual and search the pdf for uninstall.

Hope that helps.

---

### Post by webcoded612 on 2008-06-06
> **NikoC said:**
> From the manual on the VirtualBox website I understand that the software depends on a package called qt3... I'm currently not on my ubuntu machine, but what if you open synaptic and search for qt3 and install that?

That's what I needed to know.  Thank you very much.  :)

---

### Post by webcoded612 on 2008-06-06
> **forestpixie said:**
> From the manual



So reverse what you did to install it, navigate to the file and do this I assume - 

```
sudo ./VirtualBox.run uninstall /opt/VirtualBox
```



If people are not looking at the forum at the time that you're thread is there then it won't be seen, the forum isn't a replacement for searching, all I did was get the manual and search the pdf for uninstall.

Hope that helps.

You're right, of course.  The problem with searching is there's so much conflicting information on how to do things in Linux, and so much of it is wrong or out of date that it's easier to get fresh answers.  

Thanks for the help.  You can take comfort, I guess, that you're one of two people of all the people on this forum who cared enough to take the time to answer a simple question.  :))

---

### Post by forestpixie on 2008-06-06
> so much conflicting information on how to do things

Tell me about it I have the same problem :)

Still glad you're sorted, although I did point you in that direction yesterday

> HAve you tried to install what it wants,

---

### Post by webcoded612 on 2008-06-06
yah but i didn't know what to look for.  still don't, as a matter of fact.  the uninstall command didn't work, so I guess if I can't get it to work it'll just sit there until I get around to reformatting the hdd.  

thanks for the help.

---

### Post by forestpixie on 2008-06-06
Didn't installing the qt package work then? If the uninstall command doesn't work what error did you get?

Can you run it again and post the error it gives. Let's not give up just yet.

---

### Post by forestpixie on 2008-06-06
Navigate to the file in a terminal and try to run

```
sh vbox.run uninstall
``` - if this isn't the name you gave the file change it to suit

or 

```
sudo ./vbox.run uninstall /opt/VirtualBox
```

---

### Post by webcoded612 on 2008-06-12
Thanks for trying to help.  I decided to just use Windows until 8.10 comes out.  Maybe they'll make it easier to install/uninstall programs and hopefully they'll improve the video support on ATI cards.  :)

Thanks again.

---

