---
title: "[SOLVED] Lots of bad boot problems, oh crap"
date: 2007-12-11
forum: General Help
---

### Post by Lokine on 2007-12-11
I am having some horrible boot problems. I know I caused them but I'm not entirely sure what I did to cause them (though I have an idea). Anyway...

I was trying to get Ubuntu to recognize my on-board card reader and got the solution "mount /dev/sda1 /media/flash1" which ended up mounting / to an empty directory. Well. No problems as of yet, except now no programs will open. I did the stupid thing and restarted. Begin long succession of problems. It boots to the login screen fine but when I go to log in, it says "Your session lasted less than 10 seconds" and something like that... I didn't write down that error message.

So, after mucking around in the failsafe terminal (being the only session I can load) I try again. Same message. I was able to delete the /media/flash1 which I thought caused the problem, and my root is still mounted to / as it should be; but I still can't log in. So I restart, try to muck around from the root terminal at restart (using the restore restart from the boot menu). No dice.

Finally, after about an hour of trying to fix some things, I'm able to log in as myself from the root terminal and start x-server as root. You'd think I could solve my problem from there but no--I can't access much. My USB drives aren't recognized, I'd call that the biggest problem as it makes backing up my important files very difficult, if not impossible. (Also, when I do start up the root x-server, it gives me the error message "failed to initialize HAL!")

Well, I tried deleting the utmp file and some other tmp files (probably a bad idea). Upon trying to log in from the actual log in screen (after yet another restart) I get the following error message:
"Failed to create file '/tmp/gconf-test-locking-file-MJCO2T': permission denied."
No idea what that means. Another error (gotten somewhere in this mess) said that it couldn't access my authorization file or write to something in my home folder.

Well, I'm sure by now many of you are shaking your heads or even laughing at my idiocy. I'm here to ask--what can I possibly do to fix this? Am I screwed?

---

### Post by kevinatkins on 2007-12-11
Oh dear.

Looks like you've been having lots of fun... I think the situation should be recoverable, but it might take a few attempts as we try things..

Anyway, I think your .Xauthority file has ended up with incorrect permissions somehow (I've had this happen to me before), so the first thing you need to do is sort that.

Boot into recovery mode, then when you get to the prompt, go into your home directory. Now, I don't know what your login username is, but what you need to do is change ownership of the .Xauthority file back to yourself - do this:

chown <your username>:<your username> .Xauthority

NOTE - the filename is preceded by a dot - ie, 'dot' then Xauthority

Post back how you get on

---

### Post by Lokine on 2007-12-11
Alright, I've just changed the ownership of .Xauthority. Attempting to log in...

First error message:
User's $HOME/.drmc file is being ignored. ... Files should be owned by user and have 644 permissions. ...

And then it tells me I still can't write to my auth file. I'll go back in and chmod my .drmc, see if that does anything.

EDIT: Okay, that got rid of the .drmc message, but it still can't write to my auth file or log in. Any other suggestions?

---

### Post by kevinatkins on 2007-12-11
Hi,

OK, switch to another TTY (<Ctrl>-<alt>-<F1>), login as yourself, then issue:

```
 ls -l -a | grep .Xauthority.
```

Could you post back the result?

Cheers.

---

### Post by Lokine on 2007-12-11
-rwxr-xr-x  1 austin austin    107 2007-12-11 17:45 .Xauthority

Should it be writable by any user other than me?

---

### Post by kevinatkins on 2007-12-11
Hi,

OK the file should not have read / write permissions for any user other than yourself.

To fix this:

```
chmod 600 .Xauthority
```

But I'm not sure whether this will fix the problem.... Give it a try, then could you post back exactly what error message (if any) you receive when you try to log in.

Nb, it might be worth restarting the Gnome Display manager after you have done the above, just to be sure:

```
sudo /etc/init.d/gdm restart
```

---

### Post by Lokine on 2007-12-11
Alright, that solves the auth file problem, haha!

Here's the next error message (this is the 10 second session error message I got early on):
"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. ..."

And details from .xsession-errors:
"... This process is currently running setuid or setgid. This is not a supported use of GTK+. You must create a helper program instead. ... Refusing to initialize GTK+."

---

### Post by kevinatkins on 2007-12-11
Hi,

OK, at the GDM login screen, try clicking 'Options' -> Select Session and selecting Gnome, then try again.

If that doesn't work, does 'Failsafe Gnome' work?

---

### Post by Lokine on 2007-12-11
GNOME gives the same error message. Failsafe GNOME gives this error message:

"Could not open or create the file "(null)"...there may be a problem with your configuration, as many programs need to create files in your home directory. The error was 'Failed to create file '/tmp/gconf-test-locking-file-S1ZO2T': Permission denied"

---

### Post by kevinatkins on 2007-12-11
Hmm, I'm wondering whether this is a problem with permissions on your /tmp directory.

Could you go back to your TTY (Ctrl-Alt-F1), cd to the filesystem root (cd /) and try:
```

ls -l | grep tmp
```

and post back the results...

---

### Post by Lokine on 2007-12-11
It's 755 with root ownership. (Easier to type this than copy character-for-character).

---

### Post by kevinatkins on 2007-12-11
Hi,

OK, that's wrong!

Should be -rwxrwxrwt (ie, with sticky bit set)

You'll need to do:

```
sudo chmod -R a+rwx /tmp
```

Then:

```
sudo chmod -R o+t /tmp
```

That *should* work - check the permissions again after... Hopefully then login should work.. Post back with results..

---

### Post by Lokine on 2007-12-11
Ah! That did the trick! Well, I can't check anything else from where I am but at least I am able to log in now. Thank you very much!

---

### Post by kevinatkins on 2007-12-11
Excellent - glad to help. But it does look like a few things have gone seriously astray on your system - now might be the time to do a backup of all your personal files, just in case there are other problems! Hopefully not though..

Cheers,

Kevin.

---

