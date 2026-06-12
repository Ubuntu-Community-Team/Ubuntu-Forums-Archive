---
title: "&quot;Timeshift&quot; changing permissions, won't stop automatic backups, restricting drive."
date: 2018-09-30
forum: General Help
---

### Post by Lloyd_Hayes on 2018-09-30
Timeshift help needed.  Yes, I know that it is not in the normal list of downloads, but it was a program that I used for almost 2 years while running Mint. Now I am running the latest version of Studio.


This is a multi-part question, and I will explain. I went to do a backup to a portable drive formatted as an NTFS drive using Timeshift. The program took the drive over and changed all of the normal owner and permissions to this external drive to “ROOT”. I was also transferring other files to this drive and suddenly was unable to use the drive for more than a couple of minutes at a time. The drive ended up as being locked up and then became corrupted. I had to replaced the partition and reformat this drive. (My Windows computer could not salvage it.) I had to change the owner and permissions of this drive back to me.


I also changed the settings in Timeshift by turning the automatic backups OFF, and changing the backup location to a 2nd internal backup drive.


I then found a new entry in my “Media” directory which has the same name as the external portable drive. This directory is there even when the portable dive is not plugged into the computer. It shows up as a directory with “Root” only ownership and permissions, but does not act like a normal directory. I changed the ownership and permissions on this apparent directory, which seems to be empty. But I still can not change the name of this directory, or delete it.


As I said, I had turned the automatic backs off. But Timeshift is still automatically starting up and showing a “Backup Failed” window daily after automatic backups have been turned off.

And I just noticed that files transferred to this portable drive are not being written to it, and I am not sure where they are going. Drive light is flashing showing error.


The questions are: 
How do I stop Timeshift from automatically starting up? 
How do I get rid of this extra entry in the “Media” directory? Also, do I want to get rid of this new entry in the “Media” directory?

And how do I get my portable drive back?

[FONT=Verdana]Pardon me for edit by posting an image that shows my post here, but I just noticed that I am still getting a notice that I am still waiting for my portable drive to unmount, after about 10 minutes. The drive seems to be locked as mounted. I don't know what is going on.

[/FONT][ATTACH=CONFIG]281220[/ATTACH][FONT=Verdana]
[/FONT]

---

### Post by Lloyd_Hayes on 2018-09-30
I just found out that the files that I transferred to that portable drive, which were not showing on my Ubuntu Studio computer, showed up when I plugged that drive into a Windows computer. I am having Windows check this 4 TV portable drive now, but it will take awhile. Am in the process of un-installing Timeshift now. However, that one extra directory is still in my "Media" folder. As I just said, that drive is hooked into a different computer now.

I got an error message as I was deleting the older files from my 2nd internal drive.
[IMG]https://lloydhayes.smugmug.com/Direct-Link-Images-only/ComputerIissues/Issue-September-30-2018-001/n-mb6J8k/i-nbdJcSH/A[/IMG]

---

### Post by deadflowr on 2018-09-30
> I got an error message as I was deleting the older files from my 2nd internal drive.
[IMG]/home/lloyd/Pictures/Screen_Shots/Screenshot_2018-09-30_11-16-53.png[/IMG]

Upload the image using the attachments feature
(In Reply to Thread or Go Advanced in the toolbar click on the paperclip icon to open the attachments utility.
Click Add file > then choose file and find the image in your Pictures folder (or where ever it is) then click upload and then click Done at the bottom,
the Attachment should automatically be added at the end of the post as an attachment)

---

### Post by Lloyd_Hayes on 2018-09-30
I just tried that. It didn't work.

---

### Post by Lloyd_Hayes on 2018-09-30
Here is a link to my photo page.
[https://lloydhayes.smugmug.com/Direct-Link-Images-only/ComputerIissues/Issue-September-30-2018-001/n-mb6J8k/i-nbdJcSH/A](https://lloydhayes.smugmug.com/Direct-Link-Images-only/ComputerIissues/Issue-September-30-2018-001/n-mb6J8k/i-nbdJcSH/A)

---

### Post by Lloyd_Hayes on 2018-09-30
Here is a link to my photo page. It shows something in my media directory, but there are no drives mounted right now.

[https://lloydhayes.smugmug.com/Direct-Link-Images-only/ComputerIissues/Issue-September-30-2018-001/n-mb6J8k/i-DmtNc33/A](https://lloydhayes.smugmug.com/Direct-Link-Images-only/ComputerIissues/Issue-September-30-2018-001/n-mb6J8k/i-DmtNc33/A)

Here is another screenshot showing permissions. But I can not do anything with whatever this is.

[https://lloydhayes.smugmug.com/Direct-Link-Images-only/ComputerIissues/Issue-September-30-2018-001/n-mb6J8k/i-wVGGWk8/A](https://lloydhayes.smugmug.com/Direct-Link-Images-only/ComputerIissues/Issue-September-30-2018-001/n-mb6J8k/i-wVGGWk8/A)

---

### Post by Lloyd_Hayes on 2018-09-30
And still another screenshot:

[https://lloydhayes.smugmug.com/Direct-Link-Images-only/ComputerIissues/Issue-September-30-2018-001/n-mb6J8k/i-ZfwwvV8/A](https://lloydhayes.smugmug.com/Direct-Link-Images-only/ComputerIissues/Issue-September-30-2018-001/n-mb6J8k/i-ZfwwvV8/A)

---

### Post by Lloyd_Hayes on 2018-09-30
I should explain. I don't get an error message from the computer desktop. It simply shows the drive and folders without any files. I seem to only be able to see the files from my Windows computer.


The error message comes from the drive light flashing. The drive does not flash as files are read or written to it. The drive only flashes when there is an error. I connect it through a USB 3.0 port.


Right now Windows is checking the drive. It can take up to 24 hours for Windows to check and try to repair one of these 4 TB drives. (Windows is slowwwww.....)

---

### Post by Lloyd_Hayes on 2018-09-30
Just had a total computer crash after I hit cancel on this one. I was locked out of my 2nd internal hard drive so I rebooted. After rebooting, I tried to open this same 2nd internal drive and was still locked out. But I also got this message about Timeshift wanting to start another backup. I have not yet uninstalled it since I am trying to figure out what is going on. But I have deleted the backup files on this 2nd drive using the Timeshift program. I took a screenshot and cancelled the start screen. The computer did a total crash right after this.

I ended up rebooting 3 times before things got back to normal. I had features and Internet browsers not working correctly until after the 3rd reboot.

Note: Timeshift uses 'Deja Dup' for the backups.

Here is a link to the startup screen:

[https://lloydhayes.smugmug.com/Direct-Link-Images-only/ComputerIissues/Issue-September-30-2018-001/n-mb6J8k/i-cM8p8Mt/A](https://lloydhayes.smugmug.com/Direct-Link-Images-only/ComputerIissues/Issue-September-30-2018-001/n-mb6J8k/i-cM8p8Mt/A)

---

### Post by Lloyd_Hayes on 2018-09-30
My attempt at having Windows check the portable hard drive failed. I gave up on it and than deleted the partition, along with installing a new one. I have windows wiping the drive right now, with the drive being formatted afterwards. I may assign it a new serial number to help things.

As I said before, Windows is slowwwww.................

---

### Post by Lloyd_Hayes on 2018-10-01
I have identified one part of the problem. The automatic backups were not being initiated by the &#8220;Timeshift&#8221; Program. Instead, they were initiated by  a Ubuntu program that is simply called &#8220;Backup.&#8221; I am not sure how the automatic backups got turned on in this program. But the screen about starting a backup is now explained.            
                        
The folder in the &#8216;Media&#8217; directory is still not explained. I still can not delete it.            
                        
As for the portable drive, a day later and my Windows computer is still working on it....            
            When Windows is done, I will give it another try on my Linux computer.

---

### Post by Lloyd_Hayes on 2018-10-01
I may have this solved. Without a doubt, the backup program "Timeshift" does something with permissions. It startled me when I inserted a memory stick into the computer and I didn't have permission to do anything with it. But after adjusting some of those permissions with 'chmod', everything is starting to look like it is back on track again. I suspect that the problem was created because of interaction between two backup programs running automatically with Cron. I won't swear to it, but that is what I think right now.

Timeshift makes an image of your operating system similar to Windows "Backup", and can include all of your data files, but does not include your home directory by default. Nor does it include the ROOT directory by default.

---

### Post by Lloyd_Hayes on 2018-10-03
This seems to be solved.

1st. The program '**Timeshift**' changes many of the permissions on the computer to "**ROOT**" only. The home computer is not usable under these permissions. I had also run into the problem of the Ubuntu Software not being able to update or install new software after **Timeshift** was installed. By going through and adjusting the required permissions, especially on the **Media** and **Root** directories, I got my computer back. It appears that '**Others**' require permissions to the "**Root**" directory in order to add new software, unless ownership of this directory is changed to the user ('lloyd', in my case). And I am not up to speed on what happens when the owner of the "**Root**" directory is changed to the user.

2nd. I made a mistake above where I said that '**Timeshift**' uses the '**Deja Dup**' backup program. It does not. But I do have '**Deja Dup**' on my computer, and it was set for automatic backup. This has been corrected, with the automatic backups disabled.

Note: **Timeshift** is designed to backup system files. The **home** directory can be added to the backup, but the '**Home**' directory is not part of the **default settings**. In fact, the '**Home**' and '**Root**' directories are the only directories which are not part of the **default** backup. I have included my '**Home**' directory in the backup settings. And I have also removed the '**Media**' directory from the backup settings since I am using a 2nd internal drive for my backups. **Timeshift** will try to backup it's previous backups so you want to exclude that location in the **Filters** when using this program.

As for the portable backup drive, I lost everything that I had copied onto it. The good news is that everything on it had been copied from my main drive on the computer. All data on that portable drive can be replaced. I will have to do another backup to it, but this time I will **not** be using either **Timeshift** or **Deja Dup** with the portable drive.

It seems that this problem is solved.

---

### Post by Lloyd_Hayes on 2018-10-04
OK, I forget. How do you mark problems as solved?

---

