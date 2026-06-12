---
title: "Terminal directories stupid question: &quot;~&quot; vs. &quot;/&quot; --- root v home?"
date: 2017-10-30
forum: General Help
---

### Post by spencer2 on 2017-10-30
** if this is in the wrong place: I'm sorry, I'll move it to where it should be if someone will tell me where that would be. I'm posting it here since this is "general help" **

I'm a long time Ubuntu user but not really a "coder": I sort of learn what I have to as I go but sometimes I sort of overlook or don't know that I need to clarify things as I'm going. I'm trying to learn how to do all my file/directory organizing through the terminal & expand my general knowledge & such, but I think I'm doing an overlook thing. Some help would be greatly appreciated. 

I don't really know the exact syntax for my commands so there is some trial & error & I think I'm doing something wrong & I'm hoping someone can answer a couple, what are probably stupid, basic questions (but that I think I'm doing wrong none the less). 

The first thing  is the difference between the "~" & the "/" syntax. 

Under the "~": 

```
spencerownside@spencerownside-Aspire-F5-571T:~$ cd ~
spencerownside@spencerownside-Aspire-F5-571T:~$ pwd
/home/spencerownside
spencerownside@spencerownside-Aspire-F5-571T:~$ ls
adobe-linux-x86_64.repo  Green Job FollowUp.odt  Pictures
Court Cases              green something.odt     Public
Desktop                  l;asjf;las.odt          Second Editor Letter.odt
Documents                Links                   snap
Downloads                list.txt                Templates
etc                      minitube64.deb          TFRJ Statement.odt
examples.desktop         Music                   Videos
FCC                      Part 2 scratch.odt
GPMarchAgenda.docx       pia.sh
```

And under "/", I have: 

```
spencerownside@spencerownside-Aspire-F5-571T:~$ cd /
spencerownside@spencerownside-Aspire-F5-571T:/$ pwd
/
spencerownside@spencerownside-Aspire-F5-571T:/$ ls
bin    core     Done  home            lib         media  Pictures  run   srv  usr      vmlinuz.old
boot   Desktop  etc   initrd.img      lib64       mnt    proc      sbin  sys  var
cdrom  dev      Good  initrd.img.old  lost+found  opt    root      snap  tmp  vmlinuz
```

So, I have some different things in the different locations & I think that as I've been going along with my trial & error efforts, I'm pretty sure I've been inconsistent with moving/copying various files & such. I assume that the "/" directory should be the 'bin', 'boot', 'opt', 'lib'. etc... & that my "Desktop", "Done", "Good", pictures, etc. should be in the folder:

```
/home/spencerownside
```

If this is correct, how do i do the syntax to correctly move both files & directories to the correct place? Specifically, I'd like to move the "Done" directory to /home/spencerownside. Also, what is my syntax for moving both directories & files to directories under the spencerownside? I'm pretty nervous about doing this correctly because while its annoying to move stuff to the wrong place, I'm worried about syntax especially when deleting stuff. I have a folder called "Desktop" on both the the "/" & the "~" (under /home/etc.. ) & the folder under "home" is my actual desktop with all the folders & such on it --- I'd be really sad if I deleted the wrong "Desktop". Please help & thank you very much.

* to clarify a little: I {assume}, that I want normal use files (videos, music, word docs, etc) under the "/home/spencerownside" -- hence the moving of non system directories out of the "/" & to the "~"

please & thank you again

---

### Post by gsahli on 2017-10-30
If I were you, I wouldn't save, move or mess with files or folders in the root "/" directory. Your personal files are supposed to be in your home folder - "~" If you want to be a linux (& unix) user, you need to understand file system hierarchy:
[https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by spencer2 on 2017-10-30
ok: so to be clear, the "/" is root? I agree, I don't want to mess with the root stuff. I think what I've been doing is when I move things ("mv" command, be it file or directory) [& intended to be kept on the 'home' side]; I don't do my target syntax correctly & am instead moving stuff into the 'root'. I would like to get things into the home you're talking about; so what is the syntax that I need?
For example: under my home, there is a directory called "Done" --- under the root there is also a folder called "Done" --- I think that when I tried moving "Done" within my home, I think the target syntax was wrong & went to root: what is the syntax to move the root "Done" to "/home/spencerownside/Video/Untitled" please? Do I have to type out the entire target directory? Or, what is the syntax for merging the 2 "Done" directories (I want the 'done' in root to merge into the 'done' in home). I'm sorry these are stupid questions & I do appreciate your help. I do get the difference between the root & home; its the syntax that I'm having trouble with. 
The best example I can think of is with a new math equation or logic proof: I'm looking at the equation & I can plug through it some, but I'm doing something wrong & I need a couple of examples to check my work against to see what I'm doing wrong. I hope that helps & again, thank you for your help. Just your specificity about the 2 cleared up what I thought (but was not certain) might be the case - and thank you very much for that.

---

### Post by vasa1 on 2017-10-30
You couldn't move things to root unless you've been operating as root (which sadly is very common for people coming from MS Windows) or you've been been using elevated privileges (sudo).

I hope you back-up all your valuable data! If not, please do so at once.

---

### Post by spencer2 on 2017-10-30
I think that what I was doing before was using sudo to move directories/files into root from home because i was doing the syntax on my target wrong. I've figured out some of it & have moved out of root the folders I accidentally put there. What is the syntax for moving a folder that has files in it? I'm specifically trying to merge my "Done" folders (they are both on the home side now).

---

### Post by spencer2 on 2017-10-31
nm: i figured it out. thank you.

---

