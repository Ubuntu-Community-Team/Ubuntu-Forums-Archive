---
title: "Xserver restarts when connected with Xming using xdmcp"
date: 2007-01-26
forum: General Help
---

### Post by tepegoz on 2007-01-26
Dear all,
I have installed edgy to my computer, and I want to connect to this box using xdmcp from other computers. When I connect to the computer using Xming, the login screen comes. After giving the username and password, the screen goes to brown and waits forever.
I found this information in daemon.log:

Jan 26 11:17:47 <computer name> gdm[30462]: gdm_slave_xioerror_handler: Fatal X error - Restarting <client ip>:3

I am using ATI drivers.

Anyone has an idea?

Thanks
Murat

---

### Post by Endolith on 2007-02-10
> **tepegoz said:**
> Dear all,
I have installed edgy to my computer, and I want to connect to this box using xdmcp from other computers. When I connect to the computer using Xming, the login screen comes. After giving the username and password, the screen goes to brown and waits forever.

I am trying to do the same thing.  Try failsafe sessions and see what output you get.  I have seen it display the background of my desktop and the grey box in the upper left hand corner changes into an actual error dialog, but it only happened once and I don't know why.  The error dialog said something about Gnome startup scripts?

> 
I found this information in daemon.log:

Jan 26 11:17:47 <computer name> gdm[30462]: gdm_slave_xioerror_handler: Fatal X error - Restarting <client ip>:3


I don't think that message appears in daemon.log until after you log out.  The grey error box in the upper left hand corner of the screen is probably the key here.

---

### Post by Endolith on 2007-02-11
I got it to display the error message again.  So first it shows the login screen, then I log in and it says Are you sure you want to log in?  You're already logged in. and you say yes, then it goes to the blank brown screen with the grey rectangle in the upper left hand corner.

However, if you let it sit like that for long enough, something crashes and then it starts to work again, and the grey square turns into an error dialog and a bug report crash thing appears, too.  The system then starts to kind of work the way I would expect.

The error dialog says:
> There was an error starting the GNOME Settings Daemon

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply.  Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

Is this the same thing you saw?

See attached screenshots.

See also

    * [http://ubuntuforums.org/showthread.php?p=2141149](http://ubuntuforums.org/showthread.php?p=2141149)
    * [http://ubuntuforums.org/showthread.php?p=2141132](http://ubuntuforums.org/showthread.php?p=2141132)

---

### Post by twowheeler on 2007-03-01
Yup, same trouble, and same error messages in daemon.log, but I am in dapper.  I don't get the odd gray rectangle though.

However I found a work around as follows.  Open up System --> Administration --> Login Window.  Select the Remote tab.  Change the Style setting to "Plain with face browser" or "Plain".  Close the window and try the remote login again.

It seems to only screw up when set to "Same as local" on my machine.  If you confirm we should file a bug.

---

### Post by Endolith on 2007-03-03
> **twowheeler said:**
> Yup, same trouble, and same error messages in daemon.log, but I am in dapper.  I don't get the odd gray rectangle though.

However I found a work around as follows.  Open up System --> Administration --> Login Window.  Select the Remote tab.  Change the Style setting to "Plain with face browser" or "Plain".  Close the window and try the remote login again.

It seems to only screw up when set to "Same as local" on my machine.  If you confirm we should file a bug.

When I switch to Plain mode it still does the same thing with the gray box.

---

### Post by dupa on 2007-07-17
i've the same kind of problem. i can do login from Cygwin (or Xming too) from Windows.. but after login.. everything hangs up.. and i can only see a grey rectangle.

I tried to remote login from another ubuntu login and it worked.

Any idea?

---

### Post by bgturk on 2007-08-27
I am experiencing the same problem. I am unable to log into my Ubuntu box from windows via XMDCP. Has anybody solved this problem?

---

### Post by youdicieux on 2007-09-24
is there still no solution for this problem?
i changed  the remote login Window to Plain, opened the windowsfirewall, disabled Xmings clipboard.
but i still have the grey box, wich turns into an [errormassage]("http://ubuntuforums.org/attachment.php?attachmentid=25069&d=1171232780") after some minutes before the Xserver restarts.

---

