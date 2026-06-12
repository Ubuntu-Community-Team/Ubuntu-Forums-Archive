---
title: "Sunbird 0.7"
date: 2007-10-30
forum: General Help
---

### Post by wildkarde on 2007-10-30
Sunbird 0.7 was just released and wanted to share this link with everybody.

[http://linuxmint.com/forum/viewtopic.php?p=40542](http://linuxmint.com/forum/viewtopic.php?p=40542)

[http://www.4shared.com/file/27672963/d88a81b3/sunbird-mint_07_all.html](http://www.4shared.com/file/27672963/d88a81b3/sunbird-mint_07_all.html)

The good folks from Linux Mint made a package.  I tried it and works fine.

Word of advice, remove Sunbird 0.5 before installing since they're not technically the same package.

---

### Post by bonejob on 2007-10-31
User "wildkarde," a self-proclaimed Gutsy Gibbon user, says he runs Sunbird 0.7 with no problem. I downloaded and installed the Debian package from Linux Mint that wildkarde recommends (sunbird-mint_0.7_all.deb) and it won't run. The "busy" icon displays for a few seconds and then goes away - no Sunbird, though.

I have also tried manually installing the GZ package straight from Mozilla and got the same result.

Are there any critical packages or libraries I need to install beforehand that Sunbird needs in order to run? What do I need to do?

Be gentle, please, because I am a Linux noob.

---

### Post by wildkarde on 2007-11-02
Hey there

Do you have sunbird installed?  If you do, remove it first.  This package won't upgrade your current version as they are "technically" 2 different packages.  (sunbird vs sunbird-mint)

If you have removed it, please try this.  Download the file to your desktop.
Open the console and go to the desktop.

```
cd ~/Desktop
```

```
sudo dpkg -i sunbird-mint_0.7_all.deb
```

If this returns any errors, please paste them here.

---

### Post by FredB on 2007-11-02
Sunbird is very alpha in some ways. The best is to build source code. But it is not for "noob" users :(

---

### Post by wildkarde on 2007-11-02
In any case, any newbies might want to try "Lightning", a sunbird addon to Thunderbird.

[https://addons.mozilla.org/en-US/thunderbird/addon/2313](https://addons.mozilla.org/en-US/thunderbird/addon/2313)

---

### Post by bonejob on 2007-11-02
Yes, I DID de-install one version of Sunbird before installing the other; I may be a noob to Linux but I'm not a noob to computers! I don't use the DVD tray as a cup holder!

And Sunbird 0.7 wouldn't work - neither the tarball from Mozilla nor the denebian package from Linux Mint. What's more, Lightning would install, but would not display properly in Thunderbird. (I want my calendaring app to be separate anyway.)

In any case, it's now moot. I GOT SUNBIRD RUNNING!:smile:

I stumbled onto Phorolinux's "Five Tips for Ubuntu 7.10 Gutsy Gibbon" ([http://phorolinux.com/five-tips-for-ubuntu-710-gutsy-gibbon.html#more-38]("http://phorolinux.com/five-tips-for-ubuntu-710-gutsy-gibbon.html#more-38")) and installed the latest version of Java Runtime Environment, as well as Flash plugin, MP3 support and DVD playback support. The command was:

[INDENT][COLOR="Green"]sudo apt-get install ubuntu-restricted-extras[/COLOR][/INDENT]

Now, Sunbird 0.7 runs!

Which brings me to a gripe about Ubuntu - indeed Linux in general - that until addressed will prevent it from making serious inroads as a mainstream desktop OS. It took me DAYS of persistent Googling to find this solution, for a problem that shouldn't have been there in the first place! Nowhere does Mozilla warn that current JRE must be in place for Sunbird to run! Nowhere in Ubuntu's forums is this to be found, either!

As much as I am sick and tired of Windows, one thing just about every Windows app installer does is check to make sure all required libraries are present, and then either install the missing or outdated ones or at least kick up an error message telling you what is missing and must be installed before the application can run. I got not a whiff of a clue. Only my persistence enabled me to solve the issue. The average user is NOT going to put up with this! They will run screaming back to Windows. Or they'll save their pennies and buy a Macintosh. But they won't put up with an OS that requires this much tinkering "under the hood."

---

### Post by jamere on 2007-11-03
I agree with you completely! I've been following the same path that you've apparently been on trying to get SB 0.7 to run. SB 0.7 and 0.8 absolutely will not launch on my machine no matter what I do. I've successfully installed and used SB versions for months if not years and you are right, this is the kind of stuff that will keep new Linux users away in droves.

---

### Post by jamere on 2007-11-03
bonejob, 
 thanks for the info. Finally SB 0.7 is working after several days of trial and error, searching on the ubuntu forums and googling! I downloaded and installed numerous times to no avail. SB  would NOT launch no matter what! There were absolutely NO error indicators of any kind. Kind of ridiculous in my opinion that there were no problem indicators. I'm sure folks thought I was a little looney for not being able to do a siple install! :)

Anyway, your gripe is my gripe also...well stated!

Jim M

---

### Post by merlwiz79 on 2007-11-12
Sorry that was my fault with the dependences not being there.:oops:
I fixed it so now it should install everything  needed to run.
[http://www.4shared.com/file/29029084/4e3b9220/sunbird-mint_07-1_all.html](http://www.4shared.com/file/29029084/4e3b9220/sunbird-mint_07-1_all.html)

I have also added locales and extensions for installation for 0.7.(all tested in Gutsy)
[http://linuxmint.com/forum/viewtopic.php?t=6528](http://linuxmint.com/forum/viewtopic.php?t=6528)

---

