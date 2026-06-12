---
title: "Asked For Password Twice At Boot, Why? 13.10"
date: 2014-03-18
forum: General Help
---

### Post by Smallwheels on 2014-03-18
I'm using 13.10. I start the machine and type the password to get it working. Then It opens a new box asking for my password to allow access to be an administrator or something. I didn't have this in 13.04. What is this? I can cancel this box and operate the machine. When I do that I get this message: "User must be part of 'lp' group. Manually add 'lp' group to 'My computer name' user." 

I found this old thread where post number two says it is just asking for the keychain password to allow access to other things. Is this true? The window asking for the password does have a keys icon on it. [http://ubuntuforums.org/showthread.php?t=1541936&highlight=13.10+asks+for+password+twice](http://ubuntuforums.org/showthread.php?t=1541936&highlight=13.10+asks+for+password+twice)

It says to go to Applications>Accessories>Passwords to change it so that the password I use to sign in is the same as the one on the keychain. I haven't even setup a separate keychain. I didn't do it in 13.04 or any of them all the way back to 10.04. Even if these instructions were correct for that older version I don't know how to get to Applications>Accessories>Passwords using Unity. 

I don't want to type in my password again until I know that this isn't a flaw that somebody else is exploiting in Ubuntu. First of all is it safe for me to type my same password into this second box? Secondly how can I just get rid of this second box? 

Thank you for your help.

---

### Post by grahammechanical on 2014-03-18
When you are asked to enter the password the first time is it at the login screen? Do you have an encrypted drive? And what exactly are you being asked to authenticate when you are asked to enter the password a second time. The expression "or something" does not help us to identify whether it is a genuine system request or a request from malicious code.

In Ubuntu 13.10 with Unity we go to System Settings in the power/cog menu. There you will find User Accounts. Are you set up for automatic login?

Regards.

---

### Post by Dave_L on 2014-03-18
> I don't know how to get to Applications>Accessories>Passwords using Unity.

Use the command:
```
seahorse
```

---

### Post by Smallwheels on 2014-03-19
Since loading 13.10 last week my machine has frozen twice. I'm not happy about this. Today it did it again so when logging in I wrote down what each dialog box said.

Upon pressing the button to turn on the power again the regular log in screen opened. In time the desktop appeared. It is then that this second box opens. It has a keys icon on it. The border of the box says, "Enter your password to perform administrative tasks" Within the box it says "The application '/usr/sbin/usermod-G lp-a michael' lets you modify essential parts of your system." Below that is a box to enter my password. 

Is this enough information? 

As I said in the earlier post I click the cancel button without entering my password. Then a new box opens with this: "User must be part of 'lp' group. Manually add 'lp' group to 'My computer name' user." 

So what is going on with this?

---

### Post by Smallwheels on 2014-03-19
> **grahammechanical said:**
> When you are asked to enter the password the first time is it at the login screen? [COLOR=#ff0000]Yes.[/COLOR]

Do you have an encrypted drive? [COLOR=#ff0000][/COLOR][COLOR=#ff0000]No.[/COLOR]

And what exactly are you being asked to authenticate when you are asked to enter the password a second time. [COLOR=#ff0000][/COLOR][COLOR=#ff0000]See my last post.[/COLOR]

In Ubuntu 13.10 with Unity we go to System Settings in the power/cog menu. There you will find User Accounts. Are you set up for automatic login? [COLOR=#ff0000][/COLOR][COLOR=#ff0000]No.[/COLOR]

Regards.

Thanks for the help.

---

### Post by buzzingrobot on 2014-03-19
The "lp group" suggests something connected with printing. ('lp' is ancient Unix jargon derived from 'line printer').

Executing '/usr/sbin/usermod-G lp-a michael...' would add the user 'michael' to the group of users authorized to administer printers. Your password is required to ensure you have sufficient authority to add 'michael' to that group.

'"User must be part of 'lp' group"' is telling you that a task that has apparently been queued up cannot be executed because the user, i.e., you, are not in the lp group.

I have no idea why this is happening. There is insufficent information to even begin.  But, this kind of behavior is certainly not expected in a clean, fresh, Ubuntu installation.  It suggests, possibly, an attempt to do something with printing, that required root authority, and was left unfinished or broken.

[You might provide your password when asked for it, and see what happens. Adding yourself to the 'lp' group is certainly not a security issue.]

---

### Post by daxumaming on 2014-03-23
Yeah, this happened to my kids' desktop as well. I only got to do-release-upgrade a few days ago. And I noticed that I/they have to login twice. The first screen is with their user wallpaper and all. And the 2nd login prompt is with the default gnome(not sure) login with the clock and all. Had to check /var/log/auth.log and tracked down the culprit.

```

Mar 23 18:39:02 minero CRON[17373]: pam_unix(cron:session): session closed for user root
Mar 23 18:54:32 minero gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Mar 23 18:54:37 minero cinnamon-screensaver-dialog: gkr-pam: unlocked login keyring
Mar 23 18:56:38 minero gnome-keyring-daemon[8179]: couldn't allocate secure memory to keep passwords and or keys from being written to the disk
Mar 23 18:58:54 minero gnome-screensaver-dialog: gkr-pam: unlocked login keyring

```

I only need to uninstall cinnamon-screensaver and everything seemed fine now.

---

