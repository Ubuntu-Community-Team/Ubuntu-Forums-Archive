---
title: "How do I restore GRUB2?"
date: 2021-04-24
forum: General Help
---

### Post by sofasurfer on 2021-04-24
I recently lost mt GRUB menu while doing a dual installation (I think that was my problem) and after searching for a while I found how to restore (or update it?). I can not remember the process but it was so easy  I want to recored it in my files. This is what I remember...
There were two commands. One was <repair-grub> or <restore-grub> or <rescue-grub> and the second commands purpose was to "copy the files". I do not remember if a live dvd was involved other than to get access to a terminal maybe. All I know is there were only two commands and it was way simpler than what I am now finding by doing a search. Can anyone refresh my memory?
Thanks.

---

### Post by Xian on 2021-04-24
I've used this method from a LiveCD terminal to restore Grub2:

[https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal](https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal)

---

### Post by sofasurfer on 2021-04-25
Thanks for that

---

### Post by grahammechanical on 2021-04-25
I do not know if this is relevant but here are two commands that are very useful if we are dual booting with more than one distribution of Linux.

```
sudo grub-install /dev/sd?
sudo update-grub
```

Replace the question mark ( ? ) with the drive letter. sda; sdb; sdc. The commands can be reversed. We use these commands when we want to keep one particular OS in charge of the Grub boot menu. They will be needed when an update to another distribution upgrades Grub. The the Grub on that distribution takes over command of the Grub menu.

Regards

---

### Post by sofasurfer on 2021-04-25
That *may* be what I was looking for but I will have to wait and see. 
I have finally learned my lesson about recording information after years and years of learning linux and forgetting more than I have learned. I now have a folder (backed up) that has a pdf file where I copy all commands and procedures that I find useful. I also save tutorials in pdf format and toss them into the folder.

---

### Post by oldfred on 2021-04-25
I saved originally to text files. With different text files for different categories.

Then found Zim. A desktop Wiki. Its in repository & one of the first things I install.
[https://zim-wiki.org/manual/FAQ.html](https://zim-wiki.org/manual/FAQ.html)
Web Links to info are clickable. A find works on one file, but a search is across all the files.
Its now like my own Linux manual, and I regularly update it.

---

### Post by sofasurfer on 2021-04-25
> **oldfred said:**
> 

Then found Zim. A desktop Wiki. Its in repository & one of the first things I install.
[https://zim-wiki.org/manual/FAQ.html](https://zim-wiki.org/manual/FAQ.html)


This is very interesting. Going to read about it right now.

---

### Post by sofasurfer on 2021-05-02
> **oldfred said:**
>  Zim. A desktop Wiki. Its in repository & one of the first things I install.
[https://zim-wiki.org/manual/FAQ.html](https://zim-wiki.org/manual/FAQ.html)


I got it. I am very impressed with its simplicity and powerful solution to information storage and retrieval. Its not every day you come across something that works better than you expected, especially when its so good that everyone should be talking about it.

---

### Post by oldfred on 2021-05-02
Glad you like it.

I originally just imported my text files.
And like that they are just text files, so easy to backup.

---

