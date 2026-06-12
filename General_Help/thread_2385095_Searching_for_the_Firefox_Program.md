---
title: "Searching for the Firefox Program"
date: 2018-02-16
forum: General Help
---

### Post by thomlignator on 2018-02-16
I just received a new Dell XPS 13 (9370) Developer Edition that has come preloaded with Ubuntu 16.4. The Internet browser that is setup on this laptop is called Chrome. I do not want to use Chrome; I would rather use Firefox. I spent considerable time trying to find a Firefox package within the Ubuntu 16.4 S/O that might have come with the computer.  Is there a program for Firefox within Ubuntu 16.4 that I can install? It appears that if I have to upload Firefox from the Mozilla that I will require some sort of a program manager.

---

### Post by Impavidus on 2018-02-16
Normally Ubuntu comes with Firefox installed by default (and without chrome), but on a computer with Ubuntu preinstalled that may be different. Firefox can be installed from the software centre or whatever its name is or any other interface to the package manager. To try it via the terminal, use```
sudo apt-get update
sudo apt-get install firefox
```

---

### Post by thomlignator on 2018-02-16
Thanks Impavidus. I think this problem will take a little longer for me to figure out. I am not to familiar with using the Terminal so this will be a learning experience. After entering "sudo apt-get update", I get a list of 15 Internet sites, the bottom one number 15 reads " Hit:15 [http://dell.archive.canonical.com/updates](http://dell.archive.canonical.com/updates) xenial-dell-release " 
I do not know what this means, perhaps there is a folder full of programs ready to install somewhere in my computer.  I have not tried entering "sudo apt-get install firefox" .  I will try put a screen shot into this reply:

file:///home/bental/Desktop/Screenshot%20from%20Dell%20Terminal.jpg

---

### Post by thomlignator on 2018-02-16
I will try put a screen shot into this reply: [IMG]/home/bental/Desktop/Screenshot from Dell Terminal.jpg[/IMG]

---

### Post by QIII on 2018-02-16
To add an image, please use the attachment functionality provided by the "paperclip" icon above the text entry box.  IMG tags with a path on your machine are ineffective.

---

### Post by oldos2er on 2018-02-16
> **thomlignator said:**
> Thanks Impavidus.......... I think this problem will take a little longer for me to figure out. I am not to familiar with using the Terminal so this will be a learning experience..... After entering "sudo apt-get updat"e, I get a list of 15 Internet sites, the bottom one number 15 reads " Hit:15 [http://dell.archive.canonical.com/updates](http://dell.archive.canonical.com/updates) xenial-dell-release " ............
I do not know what this means, 

dell.archive.canonical.com is a repository. Some help here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by thomlignator on 2018-02-16
Oh, I was confused by the Image Icon. Lets see here. When I click the paper clip, I get the "Manage Attachments" window, I drag the image into Manage Attachment window, I do not see were the attached image is. All that I can do is post it and see if the image appears. In the preview nothing shows up.

---

### Post by thomlignator on 2018-02-17
Thanks for the help everybody, I am going to investigate the links provided above and glean other sources to find a way to put Firefox on the Dell XPS 13 (9370). I do not have the time to deal this problem right now, however I want come to this forum with a solution, so I can state the problem is Solved, this might help others with the same problem. For the time being I will just use my old slug of a computer.

---

### Post by Impavidus on 2018-02-17
You can't put an image that's on your own computer in a post here (unless your computer is a web server, but even then you need a full url), but as others have written, you can attach one to a post. But in case of terminal output, don't make a screenshot. Just copy the text and paste it in your post. Use [noparse]```
code tags
```[/noparse] for improved readability.

Anyway, all that the sudo apt-get update command did was refreshing the list of available packages, just to make sure the package manager is aware of the latest version of Firefox present in the repositories.

---

