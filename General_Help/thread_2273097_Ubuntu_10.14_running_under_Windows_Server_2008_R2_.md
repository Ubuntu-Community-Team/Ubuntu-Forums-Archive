---
title: "Ubuntu 10.14 running under Windows Server 2008 R2 Hyper-v error on startup"
date: 2015-04-10
forum: General Help
---

### Post by randyd2 on 2015-04-10
We have a Clonezilla server running Ubuntu Server 10.14 under Hyper-v on a Windows Server 2008 R2 64-bit Standard Edition with 8GB of RAM on an Intel Xeon 3.2 GHz processor. We have been using Clonezilla the other day and it worked fine. I started the Clonezilla VM up yesterday and I get this message that said "The system is running low graphics mode". Your only option is 'OK". So I click "OK" and now I am asked, "What would you like to do?"

I am given these four options:

* Run in low graphics mode for just one session.
* Reconfigure your graphics
* Troubleshoot the error
* Exit to console login

In low graphics mode for just one session, I get the message, "Standby one minute while the display restarts. The screen resets and stays black.

In the "Reconfigure your graphics" option, my choices are "Use default (generic) configuration" and "Use your backed up configuration". Either option just flashes the menu back up.

In the "Troubleshoot the error" screen I got the following 4 options:

* Review the xserver log file
* Review the startup error
* Edit configuration files
* Archive configuration and logs

I can review the xserver log file and I don't really see anything in there that look like a problem, but then I am a newbie. When I review the "startup error", it is blank. The "edit configuration files" option doesn't do anything but flashed the menu back up. The last options just saves the configuration and log files.

And of course the last option on the main menu is "Exit to console login" and when I select that I am returned back to a black screen. 

I have tried all of the options. I even stopped and restarted the VM session and I even rebooted the Windows server. I still get the same error message about the system is running in low graphics mode.

Another thing I noticed is you don't see the Grub Loader. I even press and held the SHIFT key down during boot up to get the Grub Loader to show up. Out of several restarts of the VM I only the Grub loader flash up twice, but I was never able to get into it, as suggested by this link:

[http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)

I wanted to try and fix the low graphics problem by using the above link, but I cannot access the Grub menu.

Has any one experience this problem by running Ubuntu under Hyper-v on Windows Server 2008 R2. We are trying everything possible to fix this so that we don't have to rebuilt it. We don't want to lose all of our images that we have stored.

In advance thanks for any help and comments.

---

### Post by TheFu on 2015-04-10
Copy the images off and rebuild the VM.

I've never touched any virtualization from MSFT.  Under any other VM technology, I'd just move the VM to a different VM host and try it there. If that didn't work, I'd boot a liveCD into the VM and look for issues by checking the log files, running fsck, and definitely having a current backup.

BTW - 10.14 isn't an ubuntu release. 10.04 is about to end support, so if you are on that, you NEED to reinstall something newer anyway.  If you are running 14.10 in production ... I think you have different issues. At any company, only running LTS releases is smart, unless there is a very specific requirement that can only be supported by some other 6 month-support release.

Ubuntu Server doesn't have any graphics, so low-graphics mode probably means 80x25 text - meh - whatever.  Just ssh into the server and do your work that way. There is an ssh server running on the machine, right?

If all this is greek to you ... well ... eh ... er ... I dunno what to say.

---

