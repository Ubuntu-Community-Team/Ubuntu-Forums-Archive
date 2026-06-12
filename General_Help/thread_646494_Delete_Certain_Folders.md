---
title: "Delete Certain Folders"
date: 2007-12-21
forum: General Help
---

### Post by Laffeman on 2007-12-21
I've got a question.
I know this could've been done easily by myself if I botherd, but as im clearing out my 'Server' computer, I realised a command for it would be faster.

Im not new to Linux, but I only know basis stuff, therefor I wanted to ask if there was a command to delete every folder under a certain size. Like, delete every folder >1MB.

Didnt find anything like that when I looked through the rm commands, so thought Id go here and ask.

Thanks in advice,

Laffeman.

---

### Post by Trinexx on 2007-12-21
I don't claim to be a guru or anything similar, but wouldn't that delete a ton of device files?

---

### Post by dannyboy79 on 2007-12-21
that would be the find command with an expression at the end of it. BUT I would use the find command first to see what it finds before adding the rm command to it. You have to use sudo because some of the folders are root viewable only. So, it would be:

sudo find / -type d -size -1M

that will find all directories which are UNDER 1MB. You put in your post > (greater) than 1MB which I am not sure you meant or not. If you do really want it to find all folders OVER 1MB, than use a plus (+) symbol.

sudo find / -type d -size +1M

Then after you see what it finds, then you can add an expression on the end like this.

sudo find / -type d -size +1M | xargs /bin/rm -rf

rm -rf, is FORCE and RECURSIVE remove. Be careful! I would think it would be easier to just reformat the disk after you save off everything that you want?

PS
I found this on gogle. Gogle is awesome. Also, I checked out the man pages for find. man find

---

### Post by Laffeman on 2007-12-21
Thanks for the replies.

I intended to use this command to delete empty folders on my storeage HDD (no sys files/folders) to clean it up abit for my FTP.

But im getting and error when I try to use the xargs code at the end:
'Input/output error'

I removed the '/' from the command line, as I only intended to use it on a specific folder, maybe that had something to do with it?

Thanks again,

Laffeman

---

### Post by dannyboy79 on 2007-12-21
are you using sudo with this command

FYI, I just messed up on my syntax and removed every folder recurisively that was under 5M from my /home/daniel/ directory. I am such an idiot. I was trying out the command to see if it worked right to see if I would get the same errors as you. Well, I didn't get any errors but the one that said it couldn't remove /home/daniel/. Oh well! I am damn sure glad that I never kept anything in my /home/daniel/ folder. THere was a bunch of folders with a period (.) in front of them and I am guessing that all my preferences are gone. Luckily I still have my mythtv recordings and all my movies, music and porn! 

What I had done was this. I created 3 folders, test1, test2, test3. I then created a file within each of them with a few letters. THen I tried the command and nothing was being found. I realized that the folders themselves were 4096kb which is obviously not lower than 1M. So then I issues the followed command

sudo find /home/daniel -type d -size 5M | grep test

and of course this showed my 3 folders. Then I issued the same command with the xargs rm -rf and it wiped everything from my home directory. I forgot that I had issued a pipe and "grep test" which means only show me the results that have test in them. I was just moving too fast. THAT'S WHAT I MEANT about being careful when using rm -rf!!!!!!!

I am not sure why you're getting an input/output error. That normally means it's having problems accessing that location on the disk. What does dmesg show or syslog? Let me know if you need anything else BUT be careful!

---

