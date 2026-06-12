---
title: "btrfs, strange file, does it merit concern?"
date: 2024-07-09
forum: General Help
---

### Post by whiteoak2 on 2024-07-09
I am using Kubuntu 22.04.3. Two days ago, I used KDE Partition Manager to create a single fresh btrfs partition on my 14 TB HDD, using the entire drive for backups. Then I used Unison to sync a folder with about 1 TB of data to it. Today, when I started my computer and launched Unison, it indicated a new file in that folder on the 14 TB HDD. This caught my attention because the file was named `kubuntu-24.04-desktop-amd64.iso`. Upon further investigation, I discovered it was created 6 minutes ago and was only 2.7 GB in size. I had downloaded `kubuntu-24.04-desktop-amd64.iso` 5 days ago, but I found the original file on a different drive; it is 3.8 GB and matches the hash on kubuntu.org. My question is, is this something to be concerned about?

Backstory, about a week ago, I used 4pane to copy a folder with many files (>300k) and folders. I intended to copy it into a folder (a) that contained files and folders, but I started the copy into one of (a)'s sub-folders. On the menu there was an option to cancel the copy which I selected. There was also an option to undo the copy, which I selected, but it failed with an error message that was consistent with the fact that the disk was now in read-only mode. That fact took me a little time to figure out. I then thought that a reboot would solve the read-only disk problem, but it failed to mount, which put me in emergency mode. I then booted into my old 20.04 installation, and modified the fstab for 22.04, commenting the line for the 14 TB drive. That enabled me to use my 22.04 system without the 14 TB mounted while I looked for solutions. The only solution that I could find was to delete that partition and put a new one on it, and that starts my story above.

---

### Post by currentshaft on 2024-07-09
> **whiteoak2 said:**
> I am using Kubuntu 22.04.3. Two days ago, I used KDE Partition Manager to create a single fresh btrfs partition on my 14 TB HDD, using the entire drive for backups. Then I used Unison to sync a folder with about 1 TB of data to it. Today, when I started my computer and launched Unison, it indicated a new file in that folder on the 14 TB HDD. This caught my attention because the file was named `kubuntu-24.04-desktop-amd64.iso`. Upon further investigation, I discovered it was created 6 minutes ago and was only 2.7 GB in size. I had downloaded `kubuntu-24.04-desktop-amd64.iso` 5 days ago, but I found the original file on a different drive; it is 3.8 GB and matches the hash on kubuntu.org. My question is, is this something to be concerned about?

Concerned in what regard? What sort of answers are you expecting to such a vague question?

> **whiteoak2 said:**
> Backstory, about a week ago, I used 4pane to copy a folder with many files (>300k) and folders. I intended to copy it into a folder (a) that contained files and folders, but I started the copy into one of (a)'s sub-folders. On the menu there was an option to cancel the copy which I selected. There was also an option to undo the copy, which I selected, but it failed with an error message that was consistent with the fact that the disk was now in read-only mode. That fact took me a little time to figure out. I then thought that a reboot would solve the read-only disk problem, but it failed to mount, which put me in emergency mode. I then booted into my old 20.04 installation, and modified the fstab for 22.04, commenting the line for the 14 TB drive. That enabled me to use my 22.04 system without the 14 TB mounted while I looked for solutions. The only solution that I could find was to delete that partition and put a new one on it, and that starts my story above.

This only adds to the confusion. Perhaps start by providing the output of relevant commands instead of a puzzling first-hand anecdote about your personal computer misfortunes?

---

### Post by whiteoak2 on 2024-07-11
> **currentshaft said:**
> Concerned in what regard? What sort of answers are you expecting to such a vague question?
I am sorry, it did not cross my mind that anyone would find it vague. Do these questions help remove the ambiguity? 

[LIST]
[*]Is it indicative of an underlying problem? 
[*]What are the chances of something similar happening in the future? 
[*]Is it a bug? 
[/LIST]
In my 35+ years of computing, I have never heard of anything like this. How do I prevent it from happening again?
If you don't mind my asking, what did my question mean to you?
> This only adds to the confusion. Perhaps start by providing the output of relevant commands instead of a puzzling first-hand anecdote about your personal computer misfortunes?
When I am trying to diagnose a problem, I want to know the history. What commands would you find relevant?

---

