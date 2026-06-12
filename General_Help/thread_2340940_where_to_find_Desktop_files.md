---
title: "where to find Desktop files"
date: 2016-10-23
forum: General Help
---

### Post by William_Labbett on 2016-10-23
[IMG]https://833ad3ab-a-62cb3a1a-s-sites.googlegroups.com/site/willsstore11/home/art/Screenshot%20from%202016-10-22%2014_39_38.png?attachauth=ANoY7crXr1B3ccrbBSM5EhFzByFhC3LJmrXECbCuPYGeiEHwhAJurnN0H_alCqg2gLdxuBg9T-7FJAA9cxxYeqFEyXi-5pmIIC4d-XHewkvmIVgh4XnT0VE3O-GjTaRc6AF2E-P6Ij5684-xQ3jTBQA7nAO1xBSeJ_UgVe8w6Z18FaYq7_iTRINaNavRcflb3OQO2VnHj5wImZWiqD-TsGXBrfweus2ZVsvPStW0l-8Iu0lN1AZTj7P4jCWG_FG6Q435kqOqP_Qd&attredirects=0[/IMG]


This is what my auxiliary drive looks like. It's ubuntu on it. I had to take it out of the machine it was running for some reason and so now I'm accessing it
from another ubuntu machine. I put it in another machine as an auxiliary drive hoping to be able access an important file with all my passwords in.

I'm used to being able to access the files from the ubuntu interface but now I've just got this filesystem to look through to find the file.
I think the file was on the desktop. Can someone tell me where I should look. I've looked in the usr folder but can't find a list of users with all

the usual My Pictures, Downloads et al.

Some advice would be great. It might acually be the wrong harddrive but I had the same issue with the other one as I have two out of work
HD's with ubuntu on.

---

### Post by CantankRus on 2016-10-23
Look in the home folder where you'll find the $USER home directories.

---

### Post by ajgreeny on 2016-10-23
Depending on how the disk is attached you will probably need to look in the left hand pane of your file manager to see the various disks (devices) listed and the partitions of the disks.

Once you click on the shortcuts in the left hand pane, the partitions of the "old" attached disk will probably be mounted in **/media/<username>** and from there is where you will need to search for the folders and files in **/home/<username>**.

You may have some problems copying or opening files from that disk depending on permissions that they have, but if you can't figure out how to get the files you need, come back again and ask.

---

