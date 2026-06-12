---
title: "Trash can not emptying!"
date: 2013-05-04
forum: General Help
---

### Post by benhofb on 2013-05-04
Hey everyone. I am having issues with my Peppermint OS 3 installation (for those who don't know, Peppermint OS is a spin of Lubuntu; "3" is based on Lubuntu 12.04). 

I cannot seem to empty my trash can! Whenever I go into Pcmanfm and right click the "empty trash" option, I get a huge error message reading out all the files that *were* in my trash and saying that there is no such file or directory. BUT, it looks as if the files are indeed there whenever I click the "Trash" icon within Pcmanfm. 

I am somewhat of a linux noobie, so I am not so familiar with the different trash bins. I remember reading somewhere that there is a **User** trash bin and then a **Root** trash bin. The Trash icon says that the path is "trash:///", but where exactly does that lead? Is that to the Root or User trash bin? 

I've also noticed that whenever I download and then delete newer files, they don't seem to go anywhere. I downloaded a 4GB file and then deleted it after awhile, but the disk space remained at the size it was after it was downloaded. 

I am comfortable with the command line and am open to suggestion. Thanks in advance for anyone who helps!

---

### Post by romain.astie on 2013-05-05
try emptying it some other way, like through the terminal. there are many tutorials out there, just google it.

---

### Post by plucky on 2013-05-05
User Trash is in ```
cd ~/.local/share/Trash/files
```

There is a possibility that you may have deleted a file on a USB drive and not empty the Trash before disconnecting the drive.

If so,just reconnect the drive and empty the Wastebasket.

Good Luck

---

### Post by benhofb on 2013-05-05
> **romain.astie said:**
> try emptying it some other way, like through the terminal. there are many tutorials out there, just google it.

Hah, I may have said I was a noobie, but that doesn't mean I don't know how to google. I already googled the problem and found a thread I thought would help, but alas, did nothing. 

Back at Plucky, how can I empty the User trash? I navigated to the file and found a BUNCH of stuff there, just taking up space. I mean like stuff from months ago. :confused:

---

### Post by cariboo on 2013-05-05
If [bleachbit ]("http://bleachbit.sourceforge.net/")is available to you, check however you install packagges, and use it to get rid of unwanted files.

---

### Post by plucky on 2013-05-06
>  how can I empty the User trash? 

```
rm ~/.local/share/Trash/files/*
```

Good Luck

---

### Post by benhofb on 2013-05-09
> **plucky said:**
> ```
rm ~/.local/share/Trash/files/*
```

Good Luck

Actually worked like a charm! Thanks!

Cheers.

---

