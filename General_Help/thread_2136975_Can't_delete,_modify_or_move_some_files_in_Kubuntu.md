---
title: "Can't delete, modify or move some files in Kubuntu"
date: 2013-04-19
forum: General Help
---

### Post by Breadalbane on 2013-04-19
In the last week or so I have found that I cannot delete, move or modify certain files, pictures and word processing documents in the main, either from the root drive or the other drives in the pc or attached by usb. I cannot find what has caused this or what I was doing programme wise when it has happened.

I cannot see what the files have in common other than they will not delete, rename or wipe(using nauitilus) or be moved to other directories

I cannot change file permissions in when root.
 
Some show 0 bytes others remain their original size. 

The common error message with all of them is "Error removing file: Input/output error" The files with content can still be opened but changes cannot be saved

So far I have tried changing to root, using chow commands, command "gksu nautilus and gksu dolphin and other variants suggested on forums.

As the majority are photos or text I wish to edit and print then any help would be appreciated.

Thanks in anticipation

Keith B

PS although I know my way around some bits of ubuntu I am a novice user.

---

### Post by Impavidus on 2013-04-19
It could be a faulty hard drive. It says "Input/output error", which causes the file system to be remounted read-only to prevent more damage. Backup your files and check the smart-status of your drive.

---

### Post by dabl on 2013-04-19
The zero-bytes files sound like a filesystem issue:  [http://ezinearticles.com/?How-to-Solve-Zero-Length-File-Problem-in-Linuxs-Ext4-File-System?&id=4240780](http://ezinearticles.com/?How-to-Solve-Zero-Length-File-Problem-in-Linuxs-Ext4-File-System?&id=4240780)

---

### Post by Breadalbane on 2013-04-20
Thanks form the quick responses. I will have a go at resolving this and post the result later.

Keith B

---

### Post by Breadalbane on 2013-04-21
[**[COLOR=#000000]Impavidus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1417721")

thank you for your advice. The smart system tells me that the drive is faulty and in need of replacement. I have backups so apart from having to buy a new drive it is not really a problem They don't build drives like they use to. It has only run for 150000 hours over 9 years. (cant complain but I will).



[**[COLOR=#000000]dabl[/COLOR]**]("http://ubuntuforums.org/member.php?u=217451")
[COLOR=#000000][/COLOR]
thanks for your prompt reply. I am afraid that I found the article a little too complex for my simple mind. However I was able to recover the manipulated photos I had saved and could not open by using PhotoRec.

Thank you both for your advice and prompt responses

Keith B
Samsung N145plus, 2 Gb Ram 1.5Mhz Intel , 60 Gb SSD Kubuntu OS Start up time less than 17 seconds on a poor day Yesssss

---

