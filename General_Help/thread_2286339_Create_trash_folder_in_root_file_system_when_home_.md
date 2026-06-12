---
title: "Create trash folder in root file system when home is somewhere else?"
date: 2015-07-11
forum: General Help
---

### Post by halfbeing on 2015-07-11
Hello,

I have a very small encrypted home folder, but nearly all of my larger files I keep unencrypted on the root file system. This means that I need to create a trash folder for these other files manually, but I've forgotten how to do it. I remember something about creating a /.Trash-1000 directory or something of that sort, but I can't find any clearer instructions than that. Could someone be kind enough to remind me? Thanks.

---

### Post by ajgreeny on 2015-07-11
Tell us more, please.

This sounds like a very unusual situation and I would love to know why you want to keep your large files (what files?) in the root filesystem, as I think it is both inadvisable and probably an unsafe way to do this.

Also why do you need to make a trash folder for the root partition? Any files in the root partition that are sent to trash rather than totally deleted will go to root's trash without you needing to do anything manually.

If you want, or need, to keep the small /home partition for some reason, you would be well advised to create a new /data partition using space from the root partition, mount it at boot with an edit of /etc/fstab, and put all those large files into that.

---

### Post by monkeybrain20122 on 2015-07-11
Why do you need a trash folder in the first place? if you delete something I suppose you want it gone. Otherwise you can just create any folder and move things which you are not sure whether you want to delete there and clean it up once in a while, at least it is not hidden so you won't build up while you have forgotten about it. 

It sounds even more strange that (it seems to me from OP) you want to move your deleted files from your small /home to your /root system (for what??)  Sounds ridiculously convoluted.

---

### Post by halfbeing on 2015-07-11
I want a trash folder for the reason they were invented, to allow me to change my mind if I delete something by accident.

In /home I have two directories. One is my home directory, which is encrypted and therefore in its own file system, and one is a directory for the unencrypted files. One of the reasons for this is that I do multi-track audio recordings and I want to take as much load off the CPU as I can, since it is a bit ancient and underpowered.

But could anyone just tell me the answer to my question? I know it's not something very complicated. I've done it before, but I've forgotten what I did.

---

### Post by monkeybrain20122 on 2015-07-11
> **halfbeing said:**
> I want a trash folder for the reason they were invented, to allow me to change my mind if I delete something by accident.
There is a prompt to ask "are you sure" if you delete with the file manager so you can abort. If you may change your mind later just don't delete or move it to a temporary folder that you create. Problem solved. The trash folder was invented for stupid reasons IMO, Windows people pretty much use it for temporary storage or worse they forget about it when they delete something while it is quietly sitting there to take up space.

---

### Post by halfbeing on 2015-07-11
Please can anyone just tell me the answer instead of questioning my motives?

---

### Post by ajgreeny on 2015-07-11
I am sorry but I still do not see why you have to keep your large files in the root partition, and in fact reading your comment > In /home I have two directories. One is my home directory, which is encrypted and therefore in its own file system, and one is a directory for the unencrypted files.I am not sure you are correct saying the files are in root.  Much more detailed explanation is needed before I am prepared to try to answer your question

I am also not prepared to give an answer that could potentially be very unsafe and also pointless.

---

