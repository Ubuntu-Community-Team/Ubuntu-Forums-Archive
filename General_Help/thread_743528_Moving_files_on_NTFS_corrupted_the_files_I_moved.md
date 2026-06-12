---
title: "Moving files on NTFS corrupted the files I moved"
date: 2008-04-02
forum: General Help
---

### Post by Ionesco on 2008-04-02
I accidentally moved the "Program files (x86)"-folder (into another folder on the same partition) on my ntfs-partition in Ubuntu (touchpad mistake). I didn't notice what folder I had moved until I restarted in Vista. 

Now before Vista started it ran chkdsk that restarted the computer a couple of times until I got tired of it and skipped chkdsk. When Vista finally started I found out which folder had been moved, found it, and tried to move it back. But it wouldn't let me. So I tried in Ubuntu, it went fine. 

But when I tried to load Vista it just gets on with chkdsk for hours, restarting the computer every 4 minutes. I can't enter the folder because it says it's corrupted.

Does anyone have any idea about what happened? And maybe if it's fixable?

---

### Post by cmay on 2008-04-02
hi 
this is just a guess. i am a bit new to linux and i am no computer expert.
but however i think taht somehow the filepermissions from ubuntu hidden files or something like that has  gone into that folder you moved.
i have an usbpen myselve that i loaded up whit some programs on a suselinux and now i cant get to use it becouse i dont have any permissions in ubuntu for it. 
there is some system files that follow along whit it and i think this could have been something like that you have eksperienced.
however i would ask someone else that knows alot lot more about these things than i do to be sure.

i dont know vista other by name.
but window i do know only knows its own filesystems 
it can not see other filesystems than fat fat32 ntfs  and if so it happens that it get something  like ext3 too close it will probler say it is corrupted. 
i can not help you anymore than just telling you what i think is wrong 
but good luck whit it..

---

### Post by Ionesco on 2008-04-02
Oh. Just discovered that it's no problem opening the directory in Ubuntu, it's only Vista that complains that it's corrupted.

---

### Post by Ionesco on 2008-04-02
OK. Copying the folder to the Ubuntu desktop and back to the Vista ntfs partition made it readable again by Vista :) 

Thankx for the help.

---

### Post by cmay on 2008-04-02
hi again 
i dont think you should worry about a real virus or something like that.
but as you say yourselve it is only vista hat thinks it is corrupted.
and from the way vista see it it is really corrupted becouse there is something that does not belong in windows now. 
it is the files you make and use and move around in ubuntu linix that has some read and write permissions and other things attached to it  and being from a different file system that is surprising windows.
these two operative systems are completly different in the way they handle files.
as i said before i dont know enough about yet to really help you about.

maybe you are in luck and some one whit a solution pops up.

---

