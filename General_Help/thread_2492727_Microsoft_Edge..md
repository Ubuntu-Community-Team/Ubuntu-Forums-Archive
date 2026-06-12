---
title: "Microsoft Edge."
date: 2023-11-21
forum: General Help
---

### Post by Hewjr100 on 2023-11-21
Running Microsoft Edge on Ubuntu 22.04. The problem I have is this, I run bleachbit as root and regular user, then update system via terminal.  Every time I do this, whne I open Edge I get the following error message.

"We're having trouble syncing data across your signed devices."

So I have to sign out and then in whenever I clean up ubuntu.

Btw when I set up bleachbit, when given the choice to cancel an option I do.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293096&stc=1[/IMG]

Henry

---

### Post by SeijiSensei on 2023-11-21
I have no idea how you are running Edge on Ubuntu. Wine? A virtual machine? VirtualBox or KVM? 

Remember that Edge is basically Chromium with Microsoft branding.

---

### Post by Hewjr100 on 2023-11-21
Microsoft Edge deb install.

[https://www.microsoft.com/en-us/edge/download?form=MA13FJ](https://www.microsoft.com/en-us/edge/download?form=MA13FJ)

Henry

---

### Post by ian-weisser on 2023-11-21
Folks who bring their bleachbit habit from other OS to Ubuntu generally discover that bleachbit is not necessary in Ubuntu.

Ubuntu generally does not need to be "cleaned." Trying to do so tends to cause more problems than it solves.

---

### Post by Hewjr100 on 2023-11-22
ian I did not now that.  I will remove bleachbit.  so will just using "sudo apt autoremove" be all I need to do occasionally.

Henry

---

### Post by VMC on 2023-11-22
> **Hewjr100 said:**
> Running Microsoft Edge on Ubuntu 22.04. The problem I have is this, I run bleachbit as root and regular user, then update system via terminal.  Every time I do this, whne I open Edge I get the following error message.

"We're having trouble syncing data across your signed devices."

So I have to sign out and then in whenever I clean up ubuntu.
 

What do you have checked on your Bleachbit items; both sudo and regular?

---

### Post by Hewjr100 on 2023-11-22
Anything that did not have a cancel option.  No deep scan.  On System I checked cache, clipboard, recent documents, temporary files and trash.

Also checked Apt, bash, evolution, gnome, journald, libreoffice, temporary files, thumbnalis and X11

Henry

---

### Post by TheFu on 2023-11-22
I've never used beachblt or any similar tool.  I do wipe the trash in my pre-backup script. I only use the X11 x-buffer, so no clipboard and I remove all those default directories that I just don't use that get created in the userid setup stub. 
Lastly, I set the journald.conf file to limit total log sizes to about 200MB.  It isn't like I'd ever look over months and months of logs anyway.
For temporary files, I just ensure those get stored in /tmp/ ... which is automatically wiped at boot.
No clue why bash would be in a list. Bash doesn't leave unwanted temp files, unless you don't limit command history. I limit it to 500 commands over 3 characters long. 3 characters or less never get added.
Sort of related, I setup ~/.hushlogin ~/.inputrc and ~/.bash_aliases on all my systems to prevent dumb defaults - mostly that break my workflows and get in the way. I like multi-line paste of commands, for example.  The new "protections" that block that I find nonsensical, especially when I'm not running any GUI.

IMHO, people should be more worried about having excellent, automatic, versioned, backups that they can actually restore more than all this other junk.  [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)  Don't worry about 4Kb files when you have bigger issues.

---

### Post by VMC on 2023-11-22
Henry,
Here's what I have. On the 'Bleachbit' I have everything under Firefox checked except Cookies, Passwords.
On sudo Bleachbit, I have APT everything checked, Deep Scan, nothing, journald checked, System has Cache, Localizations, Recent documents list, Rotated logs, Temp files, Trash

I have not has your issue. Does Microsoft Edge show up on Bleachbit? You didn't say. If it doesn't, delete its config file, both ~/.config/bleachbit  and /root/.config/bleachbit
Then re-run bleachbit and see if it picks up Microsoft Edge.

---

### Post by Hewjr100 on 2023-11-22
Fu, thanks for your well laid out response, I will take your suggestionsand apply it to my system.

Henry

---

