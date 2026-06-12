---
title: "Trying To Totally Delete Firefox"
date: 2017-10-01
forum: General Help
---

### Post by shane_faulkinbury2 on 2017-10-01
I'm trying to totally delete Firefox so I can do a totally clean reinstall.  I did a search in Computer for anything Firefox and found about thirty files.  I'm using rm -r to delete everything except there are four files I cannot delete. Three of them I think have been deleted which is why they are showing up as white.  The Firefox-55.0.3 (1).tar.bz2 file will not delete using the rm -r command.  I thought rm -r could delete anything?  Yes, I am root so that isn't the problem/  Can you please tell me how to delete these four files so absolutely nothing Firefox is showing?

---

### Post by TheFu on 2017-10-01
**Use the package manager** to remove (purge) anything added by the package manager. Removing them outside that tool leaves the APT database thinking they still exist.

Then remove anything related in your HOME manually.  The mp4 files aren't related to firefox, regardless of the "firefox" in the name.

The image isn't very helpful. It doesn't provide any path information, which is absolutely critical.  I would use either **locate** or **find** to find the full path to the files.

---

### Post by shane_faulkinbury2 on 2017-10-01
I was able to uninstall everything except the three blank files.  They were in   ```
/usr/share/applications
``` and ```
/usr/share/app-install/desktop
```

I know about the mp4s and want to keep those.  I will try the package manager tonight when I get home.

Thanks,

---

### Post by again? on 2017-10-01
You may also want to delete the user config directory firefox creates @ ~/.mozilla.

---

### Post by shane_faulkinbury2 on 2017-10-01
Okay, I'm having two problems now besides getting a total wipe of Firefox.  I have wiped everything Firefox and Mozilla related, but now need to know how to purge Firefox.  It isn't ```
sudo apt-get purge firefox
``` is it?  I think I need to know what version it was, but maybe not since I deleted all the files related to the version.  Also, how do I go about installing device manager?  I've got Synaptic Package Manger, but that's it.

---

### Post by again? on 2017-10-01
From man apt
> Removing a package removes all packaged data, but leaves usually small (modified) user configuration files behind,
 in case the remove was an accident. Just issuing an installation request for the accidentally removed package will restore its function as before in that case. 
On the other hand you can get rid of these leftovers by calling purge even on already removed packages. 
Note that this does not affect any data or configuration stored in your home directory.
```
sudo apt purge firefox
```

---

### Post by shane_faulkinbury2 on 2017-10-01
Okay, the purge worked and now I have to install firefox-56.0.tar.bz2.  Does anyone have any idea how I do that?  I don't see the install file anywhere in the folder.

---

### Post by again? on 2017-10-01
Why not use the Ubuntu Mozilla ppa?
[https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa)

FYI if required.
[HOW TO USE A LAUNCHPAD PPA (ADD, REMOVE, PURGE, DISABLE) IN UBUNTU]("http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html")

---

### Post by shane_faulkinbury2 on 2017-10-01
So is it ```
[COLOR=#000000][FONT=&quot]sudo add-apt-repository ppa:firefox/ppa[/FONT][/COLOR]
```  Sorry, I've never installed a PPA.

---

### Post by again? on 2017-10-01
```
sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa
sudo apt update
sudo apt install firefox
```

If you're happy using that firefox version and don't want to get further updates that may have bugs, disable the ppa.
This command will open the software and updates "Other Software" sources tab where you can disable.  
```
software-properties-gtk --open-tab 1
```

Read about ppa-purge in the link in my previous post.
If you have package conflicts or other problems, use ppa-purge to disable the firefox ppa and downgrade packages to ubuntu default versions.
You must re-enable the firefox ppa and update before using ppa-purge.
The command to disable and purge the ppa would be(will downgrade firefox to Ubuntu default version):
```
sudo ppa-purge ppa:ubuntu-mozilla-security/ppa
```

---

### Post by shane_faulkinbury2 on 2017-10-02
Well, I'm at a loss!  I've wiped everything Firefox and Mozilla related and reintalled using the PPA.   Check out my screen shot showing the first time opening Firefox.  All of my bookmarks and extensions are still there!  Let me tell you the reason I'm doing the total uninstall.  I've been a Lastpass premium user for about two years now.  Last week all of a sudden the Lastpass extension window dropped down after pressing it and it was totally blank.  I've uninstalled it and reinstalled it several times now,  THis last time I thought I did a total uninstall and reinstall, but it's still dropping down totally blank!  How do I get rid of EVERYTHING including extensions and bookmarks?

---

### Post by again? on 2017-10-02
I don't use Firefox or LastPass.
As far as I know user configs and extensions are in ~/.mozilla and deleting this directory will reset firefox to default.
(~/.mozilla is a hidden folder in your home directory)
[ATTACH=CONFIG]276932[/ATTACH]

When you delete this directory you will get the "import settings and data dialog" on next firefox launch
and you shouldn't see any old bookmarks or extensions.
[ATTACH=CONFIG]276933[/ATTACH]

Seems to be problems with the extension in latest Firefox versions.
[https://addons.mozilla.org/en-US/firefox/addon/lastpass-password-manager/reviews/](https://addons.mozilla.org/en-US/firefox/addon/lastpass-password-manager/reviews/)
[https://forums.lastpass.com/viewtopic.php?f=12&t=267525](https://forums.lastpass.com/viewtopic.php?f=12&t=267525)

Perhaps search for a LastPass alternative as many are unhappy with it's acquisition by Logmein anyway.
[https://www.theregister.co.uk/2015/12/02/password_manager_get_out_options/](https://www.theregister.co.uk/2015/12/02/password_manager_get_out_options/)

---

### Post by TheFu on 2017-10-02
Just create a new userid and use that going forward.  All personal settings are stored somewhere under your HOME.  A new userid would have a new HOME, effectively removing all prior configs.  Or you could find those configs and delete them - as suggested in posts above.

Lastpass fails my "smell test" for security, BTW.  The last place I want to put all my passwords is online, in some cloud company's hands.  It is bad enough to have personal emails stored on some cloud computer, but passwords?  Really?  That just smells bad.

BTW, if you don't show your work (the exact commands entered), it is impossible for us to be much help.  I get that you've moved onto something else ... we only know what is written in these threads. There is _something_ you are missing, right?  We've all been there. Please "show your work" by posting that stuff back here.

---

### Post by shane_faulkinbury2 on 2017-10-02
Look, guys, what I'm trying to do is a TOTAL uninstall of Firefox which includes bookmarks and extensions, purge didn't work.  I do not want to discuss LastPass since I've been a premium user for three years and it was recommended by a nine-year CCIE Security recipient.

---

### Post by again? on 2017-10-03
> **shane_faulkinbury2 said:**
> Look, guys, what I'm trying to do is a TOTAL uninstall of Firefox which includes bookmarks and extensions, purge didn't work.  I do not want to discuss LastPass since I've been a premium user for three years and it was recommended by a nine-year CCIE Security recipient.
As said before, purging doesn't remove local user settings in ~/.mozilla which is where user bookmarks and extensions are stored.
Run
```
ls ~/.mozilla
```
There should be "No such file or directory".
If there is, remove it.

If you do a search you may find the last pass extension needs to be updated to work with recent firefox builds anyway. :p

---

### Post by shane_faulkinbury2 on 2017-10-03
Thanks for the reply, but where do I find them?  I've already opened Firefox/add-ons/extensions and removed and reinstalled, but that does nothing!

---

### Post by speartip on 2017-10-03
guber2 answered your Qu. in the last post.
After you've done:
```
sudo apt remove --purge firefox*
``` in a terminal.
Go into your home folder, view your hidden files. Then delete the .mozilla folder.
Thats it, Firefox totally gone.

---

### Post by &amp;KyT$0P# on 2017-10-03
Or, if you prefer terminal commands -
```
rm -vR ~/.mozilla ~/.cache/mozilla
```

---

### Post by again? on 2017-10-03
> **shane_faulkinbury2 said:**
> Thanks for the reply, but where do I find them?  I've already opened Firefox/add-ons/extensions and removed and reinstalled, but that does nothing!
You are aware that when you delete the ~/.mozilla directory, it will be recreated afresh when you restart firefox?

---

### Post by shane_faulkinbury2 on 2017-10-04
Thank you for all the info.  I did a Mozilla search and a Firefox search and then deleted everything I found.  The only problem now is deleting those three Firefox folders, but I'm assuming they're nothing important?  It's 1:05 am here so I'll check back in tomorrow before I re-install.  Let me know if I have to do anything else besides deleting everything in those two folders!

---

### Post by again? on 2017-10-04
If you feel you need to delete everything with firefox in the name... so be it.
Not something I would do, both because it's not necessary and manual deletion of system files may have repercussions.

Seems you've been this route before, only last time it was with google-chrome where you were using "sudo su" to remove your user files.
Have a refresher and make sure you're not making the same mistake.
[https://ubuntuforums.org/showthread.php?t=2366884](https://ubuntuforums.org/showthread.php?t=2366884)

---

### Post by vasa1 on 2017-10-04
> **guber2 said:**
> ... you were using "sudo su" to remove your user files.
Have a refresher and make sure you're not making the same mistake.
[https://ubuntuforums.org/showthread.php?t=2366884](https://ubuntuforums.org/showthread.php?t=2366884)

> **shane_faulkinbury2 said:**
> ... Yes, I am root so that isn't the problem ...from the first post :(

---

