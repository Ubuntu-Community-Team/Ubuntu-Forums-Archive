---
title: "Having problems finding hard drive with Ubuntu live cd"
date: 2016-05-14
forum: General Help
---

### Post by Joseph_Inselmann on 2016-05-14
Long story short, my computers hard drive is screwed up and the computer won't start. 

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

According to this link I am able to get access to the hard drive and save my important data, but I'm having a few issues. I get to the step where it says to click on computer and my Windows drive should show up, but the problem is when I click on computer there are over 20 folders. I don't understand what each one means and so im pretty much stuck. I ran this command...

 Sudo gparted 

...and am now faced with this screen.

[http://imageshack.com/a/img921/2914/ZsP9ji.jpg](http://imageshack.com/a/img921/2914/ZsP9ji.jpg)

I am no computer expert(and actually surprised I made it this far), so I need some advice on what to do next. I notice that the 3rd partition(the Windows one) is not working properly, so I feel that is the problem.

I really just want to know if I'm going to be able to get my important stuff off my computer or not and what steps to take?

---

### Post by oldfred on 2016-05-15
The Linux driver normally does not open NTFS partitions that are hibernated or need chkdsk to prevent damage.

But Windows 8 or later uses a fast start up to make you think it boots faster, but it really is hibernation.

 Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html) 

With gparted the error (red icon) on the unformatted system reserved is normal. But error on sda4 is from the fast start up/hibernation.

You probably just need to run Windows repairs, but should ask for detailed help in a Windows forum.

You may be able to mount in read only (ro) mode, so then it does not cause damage, but need to use terminal in Ubuntu.

      
 mkdir /media/win
sudo ntfs-3g -o ro /dev/sda4 /media/win

---

### Post by grahammechanical on 2016-05-15
In Windows where did you put your stuff? I do not use Windows but does it not have specific folders for documents, Music, Pictures  and such? Did you use those folders to store your documents or did you create specific folders for your own needs. 

And again it all may depend on the version of Windows. 

[http://windows.microsoft.com/en-gb/windows7/where-are-my-files-and-folders-after-upgrading-from-windows-xp-or-windows-vista](http://windows.microsoft.com/en-gb/windows7/where-are-my-files-and-folders-after-upgrading-from-windows-xp-or-windows-vista)

Regards.

---

### Post by Joseph_Inselmann on 2016-05-15
I kept most of my stuff either on the desktop or in documents. The folders that show up arent like that though. They seem to be folders that I should never really see, because when I open them they lead to hundreds of other folders :/

---

### Post by Joseph_Inselmann on 2016-05-15
And I tried to turn off the fast startup, but the command in the link does not seem to work. I'll fiddle around with it a bit more and see if I can find anything.

---

### Post by Mark Phelps on 2016-05-15
HOW do you know the command does not work?

Did you walk through the screenshots in the Win10 forums thread?  That will show you if FastStartup is still enabled.

Good Luck

---

### Post by Impavidus on 2016-05-15
> **Joseph_Inselmann said:**
> Long story short, my computers hard drive is screwed up and the computer won't start. 

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

According to this link I am able to get access to the hard drive and save my important data, but I'm having a few issues. I get to the step where it says to click on computer and my Windows drive should show up, but the problem is when I click on computer there are over 20 folders. I don't understand what each one means and so im pretty much stuck. I ran this command...That tutorial is quite old. It assumes that you run Win XP or Vista and the screenshots come from Ubuntu 8.10 (8 years old). Most of it is still correct though, but the user interface of Ubuntu has changed a lot. You now see many folders (directories), which are the directories in the home directory of the user (in this case the default stuff of the user of the live session). On the left there should be a list of devices, where you can find the Windows partitions. Or maybe you are already in the Windows file system, but are now seeing all Windows system files that Windows normally hides from view. That's difficult to say from here. Just browse until you see something familiar.

> Sudo gparted 

...and am now faced with this screen.

[http://imageshack.com/a/img921/2914/ZsP9ji.jpg](http://imageshack.com/a/img921/2914/ZsP9ji.jpg)

I am no computer expert(and actually surprised I made it this far), so I need some advice on what to do next. I notice that the 3rd partition(the Windows one) is not working properly, so I feel that is the problem.

I really just want to know if I'm going to be able to get my important stuff off my computer or not and what steps to take?
Judging from the sizes of those partitions, the fourth one (/dev/sda4) is the one with all your documents.

---

### Post by Joseph_Inselmann on 2016-05-15
I'm putting the command in the Ubuntu terminal and it says REG is not a found command.

---

### Post by Joseph_Inselmann on 2016-05-15
Ok, I think I found something. I found my Windows drive and when I click on it shows this...

[http://imageshack.com/a/img924/8813/briC7K.jpg](http://imageshack.com/a/img924/8813/briC7K.jpg)

I see that it says to turn off hibernation and fast restarting.

---

### Post by oldfred on 2016-05-15
You cannot run Windows command from Linux.

You should be able to directly boot Windows from UEFI boot menu or one time boot key like f10 or f12. You may need to use f8 to get into Windows own repair console or safe mode.
Then you can turn off fast start up.

---

### Post by Joseph_Inselmann on 2016-05-15
I had a feeling that was the problem. Ok, I'll try that and get back to you guys.

---

