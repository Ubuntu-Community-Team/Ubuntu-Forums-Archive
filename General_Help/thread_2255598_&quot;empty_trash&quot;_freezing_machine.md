---
title: "&quot;empty trash&quot; freezing machine"
date: 2014-12-06
forum: General Help
---

### Post by ghostofzuul on 2014-12-06
Did a fresh install of 14.04 and when i go to empty the trash the computer freezes. 

I get the box that says "file operations" and it's stuck on "preparing." 

I can see/hear the hard drive spinning... but nothing happens. I can't do anything else on the desktop and I have to turn off the machine via the switch on the front. 

I know there's a command line to empty the trash but I'm wondering if anyone knows what this problem is and how to fix it. 

Thanks!

---

### Post by vasa1 on 2014-12-06
> **ghostofzuul said:**
> Did a fresh install of 14.04 and when i go to empty the trash the computer freezes. 

... I'm wondering if anyone knows what this problem is and how to fix it. 
...
My experience is that emptying the trash, all the files at one go, can be quite resource-demanding if there are many files in there. Did you have a lot of files in trash?

---

### Post by ghostofzuul on 2014-12-06
> **vasa1 said:**
> My experience is that emptying the trash, all the files at one go, can be quite resource-demanding if there are many files in there. Did you have a lot of files in trash?

no. there are only 2 files in the trash. 

i tried this:

 rm -rf ~/.local/share/Trash/*

didn't work.

there is a file that i'm not sure of it's origin. it's "fal0lj_Xq3"

it won't let me delete the other file in the trash either... which is a simple mp4 file.

it seems any attempt to move or delete these files results in my computer freezing. 

any ideas? i googled the file and it came up with nothing. this is quite vexing. 

thanks.

---

### Post by ghostofzuul on 2014-12-06
so i just tried this:

cd ~/.local/share/Trash/

sudo -s

sudo rm -fr *

still get the same results. terminal freezes. restart machine. items still in the trash. 

fully vexed now.

---

### Post by ghostofzuul on 2014-12-13
still having this problem. 

tried a few more things still can't empty the trash or restore items in trash. 

anyone have an idea? 

thanks!

---

