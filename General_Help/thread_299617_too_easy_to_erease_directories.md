---
title: "too easy to erease directories"
date: 2006-11-14
forum: General Help
---

### Post by jmvidalvia on 2006-11-14
It is too easy to erase empty or even full directories with Nautilus (edgy)
Does anybody know how to protect a directory from beeing deleted while adding or deleting single files is allowed?
Thanks a lot...

---

### Post by aysiu on 2006-11-14
Instead of using the "delete" command, use "move to trash."

You can disable the "delete" command in the Nautilus preferences.

---

### Post by jmvidalvia on 2006-11-14
Thank you, but the problem appears when I use the keyboard.
If I use "del" key no message appears, file just goes to trash.
I have moved twice a directory by accident, so I would need to "fix" some of those directories because they are important for a couple of scripts I use.
Thanks again...

---

### Post by aysiu on 2006-11-14
Isn't there a preference in Nautilus to warn you before moving to the trash?

---

### Post by jmvidalvia on 2006-11-14
No, the preference option just warns you when you delete from the trash, never when you delete with the *del* key (althougt you are not really deleting, just sending to trash)
Of course I have it activated, but this is the way it works (¿?)

---

### Post by aysiu on 2006-11-14
> **jmvidalvia said:**
> No, the preference option just warns you when you delete from the trash, never when you delete with the *del* key (althougt you are not really deleting, just sending to trash)
Of course I have it activated, but this is the way it works (¿?)
Sorry, you're right about that. How about not pressing the Delete key? Or maybe using Konqueror or Thunar instead of Nautilus?

---

### Post by dannyboy79 on 2006-11-14
i am learning about python 2.4 currently, isn't this a place for a little python program, say, everytime the del key were pressed it would bring up a dialog box asking you whether you for sure wanted to move it to  the trash or not? sounds like something that would be useful to many users uncluding myself. I have asked around for something that would warn me if I accidentally move a folder but people tell me there is nothing to warn me. like say if I am in nautilus and i accidentally click on a folder and drag it into another folder it does it automagically without asking me if I really wanted to do that. don't ask me how it happens but it has, my wireless mouse goes bonkers every once in awhile, where it's like the button is pressed and it shoots off in a direction, so if it's over a folder, it'll move  the folder. it only happens like twice but luckily I did notice it. soon after I had to replace the batteries so I am guessing it had something to do with the batteries going. anyway, can anyone tell me if what I have suggested could be programmed?

---

### Post by Henry Rayker on 2006-11-14
You could always just pluck the delete key off the keyboard.

I don't know how you could accidentally hit the delete key frequently enough to warrant a feature like that...not to mention the deleted object just goes to the trash...I'd understand if it did something unreversable.

---

### Post by jmvidalvia on 2006-11-14
Thanks, now evetything is clear, but...same happens with thunar!
By the way, how to set tunar as my default files explorer?
Thanks a lot.

---

### Post by jmvidalvia on 2006-11-14
I am just trying to block this posibility because I am giving to my salesmen many laptops with edgy. I am quite happy because they can forget about viruses, etc. as they are no really skilled on computers. The problem appears when I want all of them to have the same directories structure (in /home, obiously) but I can not keep it fixed as it is so easy to move or erase directories or files.
Thanks.

---

### Post by aysiu on 2006-11-14
I know Konqueror definitely has this feature implemented. If you're installing Edgy for people and believe this feature to be essential, you might consider putting Kubuntu on.

---

### Post by jmvidalvia on 2006-11-14
I will try Thunar instead of Nautilus: I prefer it's simplicity for my people. I checked some webs and realised it is not so easy to substitute Nautilus by Thunar as default.
Is that so difficult?
Thanks.

---

### Post by Henry Rayker on 2006-11-14
Can't you just restrict those directories to root? That way they would have to "sudo rm -r directory_name" in a terminal...

Honestly, you can't be too sure what someone's going to do with a directory they didn't make themselves...what if they intentionally delete it (thinking it is something of theirs they no longer need) and just "ok" the question?

---

### Post by jmvidalvia on 2006-11-14
Yes, that is going to be the best idea.
Which # of chmod should I use to allow other users to fill in that root's directory and erease files inside but never be able to touch the directory?
Thanks.

---

### Post by aysiu on 2006-11-14
> **jmvidalvia said:**
> I will try Thunar instead of Nautilus: I prefer it's simplicity for my people. I checked some webs and realised it is not so easy to substitute Nautilus by Thunar as default.
Is that so difficult?
Thanks.
Please read [this link](http://ubuntuforums.org/showthread.php?p=1743164#post1743164). It may be a good start for you replacing Nautilus with Thunar.

There are also files for removable drives, too--not just the home folder.

---

### Post by dannyboy79 on 2006-11-14
so neither of you2 have a comment about creating a python program that would ask before trying to delete something from nautilus? whether it's something that can be done? or even fopr accidentally moving folders?

---

### Post by Henry Rayker on 2006-11-14
I'll have to look into the chmod when I'm at my system. My work computer won't let me chmod anything.

As for the program: I'm sure it can be done. I'm not sure if it can be done via python or not (but I don't see why it couldn't). One of my favorite apps is the syndaemon. It disables the touchpad while I'm typing, then re-enables it a certain amount of time after my last key press. I'm just not too sure how useful this kind of a thing would be.

---

### Post by aysiu on 2006-11-14
> **dannyboy79 said:**
> so neither of you2 have a comment about creating a python program that would ask before trying to delete something from nautilus? whether it's something that can be done? or even fopr accidentally moving folders? I can't speak for anyone else, but I certainly have nothing to comment about it. I don't know Python or any other programming language, for that matter.

---

