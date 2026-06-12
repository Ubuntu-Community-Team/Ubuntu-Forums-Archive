---
title: "Need to restore my system to its state before crazy  uninstall."
date: 2012-10-24
forum: General Help
---

### Post by Randy Schilling on 2012-10-24
I used synaptic to remove libjpeg-turbo8 and libjpeg-turbo8-dev packages and
my system is collapsing before my eyes as I write this.

This is unbelievable.  Weeks of work is gone.

Is there an easy way to undo this, like take my system back to a previous state?

Rlease help - Randy

---

### Post by Randy Schilling on 2012-10-24
I used synaptic to remove libjpeg-turbo8 and libjpeg-turbo8-dev packages and
my system is collapsing before my eyes as I write this.

This is unbelievable.  Weeks of work is gone.

Is there an easy way to undo this, like take my system back to a previous state?

Please help - Randy

---

### Post by dniMretsaM on 2012-10-24
You have to tell us what went wrong before we can tell you how to fix it. What happened?

---

### Post by cariboo on 2012-10-24
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by stinkeye on 2012-10-24
> **Randy Schilling said:**
> I used synaptic to remove libjpeg-turbo8 and libjpeg-turbo8-dev packages and
my system is collapsing before my eyes as I write this.

This is unbelievable.  Weeks of work is gone.

Is there an easy way to undo this, like take my system back to a previous state?

Rlease help - Randy
Try
```
sudo apt-get install ubuntu-desktop
```
which depends on all of the packages in the Ubuntu desktop system.

---

### Post by crushkittykitty on 2012-10-24
Ok this is what I do grab a live cd and a usb and pull all your stuff off then do a fresh reinstall. That is if I cant figure out what went wrong. The main thing is to save your work. Got an extra hard drive you could just make a folder on that hard drive and move all your stuff then reinstall.

---

### Post by Randy Schilling on 2012-10-24
dniMretsaM,
Thank you for looking into my problem.
I won't be able to explain what happened with as much detail
as I would like
because I'm no longer able to login to my Ubuntu system.
 
I have 2 systems, Ubuntu and Windows, controlled by Grub2. 
When I choose the Ubuntu system, startup stalls at a black screen and the statement: *Checking battery state.
 
I am a novice LAMP user. I had just successfully completed LAMP intallation 
and configuration and I was trying to setup a family web page using 
Coppermine Photo Gallery. 
Coppermine reported the follwoing error involving jpeg,
 
Fatal error: Call to undefined function imagecreatefromjpeg() 
in /usr/local/apache2/htdocs/rjs357/cpg/install.php on line 2145
 
My previous post, "Want jpeg support in gd image library and php?"
contains more details of this problem.
 
I found a reference that said I should recompile php with certain options
and that my libjpeg files needed to be in my /usr/lib/ directory.
I found these files in /usr/lib/i386-linux-gnu/ instead,l and so, right or wrong,
I decided to remove libjpeg programs, planning to reinstall them in /usr/lib/.
 
I entered Synaptic and set two packages,
libjpeg-turbo8 and libjpeg-turbo8-dev 
(I might be slightly off with these names) for complete removal. 
I should have read more carefully what Synaptic said it was
going to remove because it started removing possibly hundreds of programs.
I watched as many of my most important programs fell from my Unity launcher. After Synaptic was done, I could no longer log into Ubuntu,
as I said previously. I don't know any other details to tell you.
 
I know that Windows has a system restore command.
If Linux has such a command, I would ask that you explain to
me how to return my Ubuntu to its state at 7:30 CST on 10/24/2012.
If so, please keep in mind that I can no longer access my Ubuntu
desktop and I have no experience with Ubuntu's recovery systems.
Please provide as much detail as you can.
 
If this is not possible and I have to reinstall all my work, I wonder
if Synaptic creates a log of what it removed? This log would help a lot.
How would I access such a log?
 
Are there other options? Several people have responded to this thread
but none of them contain enough detail for me. Please, more detail,
especially on how to preserve my work,  all of which is in /home/rjs/.
 
Thanks again. Randy

---

### Post by jonnyboysmithy on 2012-10-24
So you uninstalled a lot of programs leaving your ubuntu desktop unusable.
I'm guessing somehow the package ubuntu-desktop got uninstalled.
In that case your configuration files are probably gone (customized settings like wallpaper keyboard shortcuts).
Folders like Pictures Music, Documents should still be there all intact.

The way I see it there are two ways of going about it:
1. Use a liveusb/livecd to boot up and then copy your data and afterwards do a reinstall.
or 
2. Reinstall the programs that got uninstalled.
Let your computer boot up. Don't log in at the regular login screen instead press ctrl+alt+f1 and login (you won't see your password as you type it).
Then run the command ```
sudo apt-get install ubuntu-desktop
```That should install all the programs necessary for you to log in.
After you are done you can run ```
sudo reboot
``` to restart the machine and see if that worked.
If  you cant get it to boot far enough to do that you may want to do  number1 as above or you can tell us what is happening and take it from  there. :)

---

### Post by oldfred on 2012-10-24
Try looking in /var/log/apt for history files.

I purged some old kernels a few days ago and this is what it saved.

```
Start-Date: 2012-10-23  10:45:49
Commandline: /usr/sbin/synaptic
Purge: linux-headers-3.2.0-23:amd64 (3.2.0-23.36), linux-headers-3.2.0-24:amd64 (3.2.0-24.39), linux-headers-3.2.0-25:amd64 (3.2.0-25.40), linux-headers-3.2.0-26:amd64 (3.2.0-26.41), linux-headers-3.2.0-27:amd64 (3.2.0-27.43), linux-headers-3.2.0-29:amd64 (3.2.0-29.46)
End-Date: 2012-10-23  10:46:59

```

---

### Post by Randy Schilling on 2012-10-25
Johnnyboysmithy,
 
I will probably have to go with your first approach but I would like
to consider the second anyway.
 
I don't follow the second approach.  
How do I let my computer bootup? When do I press ctrl+alt_f1? At the Grub2 screen?  Will this take me to a bash shell?
 
Thanks

---

### Post by jonnyboysmithy on 2012-10-25
Yea, the idea is to access a terminal and run ```
sudo apt-get install ubuntu-desktop
``` so you'd let it start up as usual and then do ctrl+alt+f1 before you click your username and type in your password.

Like Oldfred said: Could you post back the contents of the log: /var/log/apt/history.log or attach it as a file.
Then we can see what happened last.

You could just forget all of the above and use a livecd to copy of all your data and reinstall. Actually it wouldn't be a bad idea to make a backup of important data at this stage whether you reinstall or not.

---

### Post by Randy Schilling on 2012-10-26
reinstalling ubuntu from scratch.

---

