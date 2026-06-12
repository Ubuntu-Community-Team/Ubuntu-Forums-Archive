---
title: "Reload symbolic links?"
date: 2016-05-10
forum: General Help
---

### Post by mario71 on 2016-05-10
Hello to all the users of this forum today i have a question involving symbolic links .

I run Windows and Ubuntu on my computer and on  Windows i downloaded and installed Dropbox hence i have a Dropbox folder on the Windows partition which i can access without problems from Ubuntu,
since i access frequently to this files from either Ubuntu and Windows i decided to create a symbolic link on my Ubuntu Desktop  to access this folder.

It works without problems from the terminal once the partition is mounted but accessing from the graphical is really annoying since i have to logout and log in again .

I'm asking if there is a way to "reload" the symbolic links so the graphical environment knows the partition is already mounted?

 What i figured out is that maybe i can run a script at the start that mounts the Windows partition before the log in screen but i really want to avoid that ,also Im not sure is going to work and sometimes if the NTFS partition is not closed properly from Windows which happens if you have the fast boot enabled on Windows 10 (which i had to disable to mount the partition without having to boot on Windows and restart) the partition wont mount even if you use read only mode so m not sure if that might cause the system to get stuck while booting or something if i do the script solution which again im not sure if is going to work  .

Any suggestions, solutions are welcome .

---

### Post by Bucky Ball on 2016-05-10
When you open a file manager, is the Windows partition not there in the left pane? If you click it, it should mount. Use your Dropbox symlink.

Never a good idea to be accessing files like this from the Windows install partition. If you want to share data, much better idea to have a separate NTFS filesystem partition for the purpose.

---

### Post by deadflowr on 2016-05-10
Why not cut out the fluff and install Dropbox on Ubuntu?

---

### Post by mario71 on 2016-05-10
yes it appears there ,when mounted i can access the folder with the link from the terminal but if i double click the link it says is broken and the icon isnt a folder with an arrow unless i logout and the log in again then tho icon takes the right form and i can double click it and works. So ther is something that happens with this link when i log out and then  log in but i cant figure out what is it.

Also i know its a bad idea to share data directly form the Windows partition and also i have a partition to share data but all my files on Dropbox won fit in there and im running short on space so i can move many files easily ,If i have to reinstall Windows i will definitely make sapce for the Dropbox folder on a separte parition or make room in the already existent parition for the folder but i don have many time right and manipulating the files graphically is easier for me than watching them all form the terminal which i cna acces graphcally form the explorer going to User /mario bala blalba but is also a pain to do.

Running short on space man ,and don't have too much time to wait for my files to Download

---

### Post by mario71 on 2016-07-29
So for anyone who runs into this specific trouble ,i fixed it by mounting the Windows partition and then killing nautilus process and starting it again.

This is now solved .

---

