---
title: "Want to change folder icon system wide - 16.04 LTS"
date: 2017-09-09
forum: General Help
---

### Post by blahboybaz on 2017-09-09
Hi,

I've seen some information about doing different aspects of this, but I'm having a problem still. The solutions I've found are sparse and hard to understand. From looking at several articles I have been able to deduce that a solution that works for me would have to cover at least 3 major areas:

[B]1) Change the existing icons to the icon I want it to be (all of them - preferable all at once)
2) Set the default icon to the icon I want it to be (so that when a new folder is created it will use the new icon, no matter what path or command is used to create it.
3) Possible a need to address icons on the desktop as a special case? (I don't know if this needs be addressed).[/B]

Basically I want the system to function the same way it always has with regard to file management - same functionality - just replace the icon used for folders system wide and have it cover all the file management functionality where it might arise (not just some).

Thanks in advance for your any help. Please try not to use any special terminology very much. I don't know what most of it means and don't want to get more confused.

( I've been running ubuntu 7 yrs starting with 10.10 - I can get around on the command line a little but but might get confused at things I haven't seen before).

Here is the best article I've seen but I'm not sure it addresses all the issues, is using a different release of ubuntu than I'm running, and one of the commands looks different than I've ever seen so I don't know how to use it - [https://askubuntu.com/questions/671589/restoring-ubuntu-default-icons-folder](https://askubuntu.com/questions/671589/restoring-ubuntu-default-icons-folder)

I'm hoping to get a soln that's complete, comprehensive, and that is aimed at the release I'm running (16.04)..

Thanks so much. Hope to hear back soon.

Peace.

---

### Post by mc4man on 2017-09-09
Likely I can't help you but - 
> Here is the best article I've seen but I'm not sure it addresses all the issues, is using a different release of ubuntu than I'm running, and one of the commands looks different than I've ever seen so I don't know how to use it.
You may want to actually put that link in your post..

(- here I've changed all the main folder icons in 16.04 but a decidedly low tech approach. I use light-themes/ambiance with the default ubuntu-mono icons.
So I just went in to /usr/share/icons/ubuntu-mono-dark & put all my folder icons in there (places

---

### Post by blahboybaz on 2017-09-09
> **mc4man said:**
> 
You may want to actually put that link in your post..
s

Thanks for pointing out the mistake. I've edited the op and included the link to that article. 

While very hackish that's a pretty clever soln. I think I would rather try to do this proper though. Thx.

---

### Post by wildmanne39 on 2017-09-09
Please do not post duplicates posts, just edited your previous post.

Thanks

---

### Post by blahboybaz on 2017-09-09
sorrry


Update:

> **mc4man said:**
> 
(- here I've changed all the main folder icons in 16.04 but a decidedly low tech approach. I use light-themes/ambiance with the default ubuntu-mono icons.
So I just went in to /usr/share/icons/ubuntu-mono-dark & put all my folder icons in there (places

Based on the information I thought I found a soln but wasn't quite able to make it work. After making a backup, I edited the file /usr/share/icons/default/index.theme to point to a newly created dir <my_custom_dir_name>. Then In went in and copied the entire contents of an existing them (in this case DMZ-Black) into <my_custom_dir_name>. I thought that, after all this, I could locate the icon in that theme that is being used for directory icon and replace it with the svg image I downloaded and want to use.

I wasn't able to locate any such directory icon (who knows what it's called or if there's even anything like that in there). Also; I consider that, like the index.theme files being used, there may be some configuration file I would need to edit as well - even if were possible to replace the directory icon in an existing theme's content.


I've since put everything back as it was. (Deleted contend of <my_custom_dir_name> and replaced the edited index.theme with the original.
It didn't work.

Sill seeking a soln.

---

### Post by wildmanne39 on 2017-09-09
No worries, that is how we learn.:)

---

### Post by blahboybaz on 2017-09-09
Look,

Please ...

This isn't flor entertainment.

I screwed up my folder icons really, really bad and it a REAL mess.

I've ben suffering with it and I need to fix it.

I tried using tweak took to "Restore Defaults" but it had no effect.

A couple mos ago I had tone through multiple folder's properties and changed the icon manually for EACH folder (and not all the same icon either).

I can't work like this - it's KILLING ME.

Please, I am begginjg - I know, with absolute certainty, that this is basic stuff (the sort of thing that half the community should easily be able to solve - but I can't).

I think what's going on here is people look at the headline of this post and thing it isn't important because it's a cosmetic issue - but I'm really suffereing bc of this problem.

The mess is catastrophic - there is no way to deal with organizing dat on my system with it like this.

PLEASE

---

### Post by blahboybaz on 2017-09-09
It's like someone asking how to start the computer isn't it? Simple to almost everyone on the planet but impossible for eh asker (or he wouldn't be asking)

---

