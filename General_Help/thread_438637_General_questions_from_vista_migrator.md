---
title: "General questions from vista migrator"
date: 2007-05-09
forum: General Help
---

### Post by darussian12 on 2007-05-09
just from someone that new to Linux on the PC after trying YellowDog on the Mac and hating it a few years back but so far i like what i have been able to get to work but still have some issues with others. Before I am ready to get in too deep with Ubuntu and delete my vista partition i need help/info on a few issues. I have posted my video file questions in the appropriate forum, and my hardware issues in their appropriate thread too. Now my questions are...
1) I am used to iTunes as my mp3 player in iTunes...obviously thats not happening in Ubuntu but found Banshee and like it enough to stick with it as my default player. question is i dont even know how the file system on linux works. As in iTunes crated it own music folder for my song library in my user folder in Windows. With ubuntu when i fired up Banshee it asked me to select the folder and i selected the Itunes folder on the Vista partition so I assume those files arent imported anywhere in my linux partition. How do I do that or can I, or do I need to just create a folder for all my music in some random location on my Linux partition. If I do does it matter where I create a "music" folder on my Linux partition? because i loved using my desktop for everything temporarily in Windows but i wouldnt want this "music" folder on my desktop indefinately in Ubuntu.

2) HOW THE HECK TO I GET READ/WRITE ACCESS TO FOLDERS/FILES? ....
excuse the yelling but this seems to have gotten in the way so much, from creating a folder in the azuerus subfolder to being able to edit the sources.list file i cant seem to be able to edit stuff and only open it as read only. I only have 1 account(mine) set up on Ubuntu and coming from being used to Windows life where you have only one login account it is also the admin account how to I gain write privelages to a folder and/or file?

3)Just a general filesystem question. I backed up a lot of stuff from my PC to a webserver before messing around with my partitions and am used to having say my user folder in windows and in there subfolders for documents, videos, pics, etc....when i download the backups from the server i dont want to keep it in the default swiftfox D/l location of my desktop....do i just create all the video, pic, etc folder in my "usr" folder or my "home" folder under my user name in ubuntu...its just something i obviously have to get used to and common sense says i dont need to be storing my files in the "bin" and what not folders of Ubuntu.

thanks again and as you can see im a total retard with linux so please excuse the simple questions. if any of you can point me to a good starter quide on the web for the current version of Ubuntu that would be great. I have loved finding the Wiki page for it but it just gives you the terminal codes for how to do X ...I really need just a general overview of Linux/Ubuntu

---

### Post by strabes on 2007-05-10
I assume you didn't create a separate partition for sharing data between windows and linux, which is what most people who are dual booting end up doing. So therefore the most logical place for your music is somewhere in your home directory, most likely /home/username/music, or ~/music for short. If you're using gnome, I believe you can go to Places -> Home Folder to get there easily. Just create a new folder in there called "music" and copy in all of your music. As long as it's tagged correctly (which may not be the case considering you were using iTunes) banshee or any other music player you choose should do its magic. If it turns out you need to retag your music, you can check out the program easytag. It's in the repositories.

The files/folders you mentioned are restricted to the root user. You can temoporarily have root privileges using the "sudo" command. For example, you can run "sudo gedit /etc/apt/sources.list" in the [terminal](http://www.psychocats.net/ubuntu/terminal) to open the sources.list file as a root user, and therefore you will be able to edit and save it. For more information see this page: [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

If you don't have a separate partition/HDD for data then you should store your data in your home directory as mentioned in the first paragraph of my post.

Good luck in your linux adventures. I hope it works out for you and hopefully you'll be able to eventually get rid of that other niche OS, "vista" or something.

---

### Post by darussian12 on 2007-05-10
when i did the first go around of installing Ubuntu i had read on a page to make a system partition, a user partition, and a swap partition. the only problem was i couldnt figure out how to get the "user" partition i had created to show up and it was the largest parition i made because of all the music and video I have so Ubuntu was saying i only had the 7 odd gigs I set aside for the OS parition. So i went back and repatitioned only a swap and the OS parition with the OS being big and will be bigger once i get rid of vista. thanks for the link about permissions because that site is correct, Im used to being able to edit anything I wanted without issues. I have no problem getting rid of vista just as soon as the multimedia thread posters can help me why my video players quit each time because when i can create DVDs in linux i wont needs windows anymore.

---

