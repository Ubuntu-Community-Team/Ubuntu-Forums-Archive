---
title: "Update manager errors"
date: 2006-11-22
forum: General Help
---

### Post by Sabrage on 2006-11-22
HI, when I click the update manager orange thing it just closes after checking for updates without installing. And if I rightclick and "install all updates" I get this errormessage:> E: The package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

So I can't install the updates.... any ideas?

---

### Post by Sabrage on 2006-11-29
Haven't figured it out yet... Maybe I will have to do a reinstall. Does anyone know if it is possible to reinstall only the update manager, not the whole os?

---

### Post by OttifantSir on 2006-12-06
If you haven't solved it yet, I tried this after seeing your post:

System->Administration->Synaptic
Searched for update and clicked to change the listing to sort in order of status. Found update manager and update notifier as installed and clicked on the box (or right-click the name) and select Mark for reinstall.

It solved it for me.

If synaptic doesn't work for you, terminal commands are needed for doing this, and you will have to ask around some more for them. Just remembered seeing this option in Synaptic, and I am a noob.

---

### Post by mingster on 2006-12-06
i had the same problem earlier with new beryl packages...

update manager failed but apt-get upgrade in the terminal worked.

dunno why update manager wouldnt work

---

### Post by OttifantSir on 2006-12-06
Just got another update notification, this one pertaining to the GnuPG package. Still didn't want to download the packages and perform the update, despite having re-installed it. Then I noticed the taskbar at the bottom saying it was starting an administrative application. This usually means you have to input a password. But I wasn't asked for one. In another thread, someone said that AFTER being asked for a password by update-manager, it stalled. So, I went to use the terminal. Here's what happened:

ottifantsir@otti-laptop:~$ sudo update-manager
Password:
warning: could not initiate dbus
could not send the dbus Inhibit signal: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I thought I was out of luck. Most error messages tend to mean that, right? Not this one. It gave me an error message, but opened update-manager and installed the update.

So, if you don't get queried for your password when running update-manager, run the command I did from Terminal. Then you will ensure that update-manager has root privileges, and do what it should. This is a work-around the problem. Obviously, there's something not quite right somewhere since update-manager don't query me for a password.

But hey, the Terminal is power, so why not learn it. Things like this is what gives us noobs the confidence to try something else another time.

---

