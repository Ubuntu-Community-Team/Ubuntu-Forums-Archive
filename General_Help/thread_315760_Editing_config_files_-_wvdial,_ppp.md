---
title: "Editing config files - wvdial, ppp"
date: 2006-12-09
forum: General Help
---

### Post by stewjack on 2006-12-09
**Introduction**

I am fairly new to Linux, and have just started setting up ubuntu 6.06 in persistent mode.  I am using a 3 GB ext3 hdb partition.

The persistence mode seems to be working just fine.  Imported files such as mp3's and bookmarks persist.  Synaptic seems to maintain everything. I don't really think persistence is the main cause of my problem, but I thought I should mention it, because of the fact that I can't get the graphical front ends of wvdial or ppp to maintain my setup information.  However the kppp dialer does maintain that information but, just can't log on to my ISP because of "authentication problems."

**Background**

I have been able to partially solve the problem of the graphical front ends of wvdial or ppp not being able to maintain my setup information.

I have finally learned that if I configure wvdial, using the terminal, that my information persists!  I have also used the terminal to configured ppp.  Now  I can always boot into Ubuntu and type sudo wvdial or pon and get connected to the Internet.

Next I tried downloading the 20 megs of files required to install kppp.  The information persists with kppp but apparently requires a modification in the file /etc/ppp/peers/kppp-options.  I next discovered that I don't have permission to modify kppp-options, or the config files of the other two dialers.

**Some assumptions**

I think that more than enough background.  My present assumption is that my dialer programs can't access or modify their config files, and I know that I can't modify the kppp-options file.  The term "lock-files" may also be involved.

**Specific questions -**

How can I modify the kppp-option file or, any other file "owned" by root?

If there is a common cause to most of these experiences, please explain it to me.

Jack

---

### Post by lloyd_b on 2006-12-09
Open up a terminal window, and "sudo nano {file}", where {file} is the full file name (including the path).

"nano" is a very simple text editor.

"sudo" will prompt you for a password - just enter the same password you used when you logged in (the default Ubuntu configuration gives the initial user full access to all root commands via the "sudo" command).

As a general rule, any file that's considered to be a "system" file will have it's owner set to root, and permissions set so that only root can modify it (though generally anyone can read it).  You could potentially changed the permissions on the files so that a regular user can modify them (whether or not you *should* do this depends on your environment - having such files writeable by ordinary users can be a serious security issue).

Lloyd B.

---

### Post by stewjack on 2006-12-09
> **lloyd_b said:**
> Open up a terminal window, and "sudo nano {file}", where {file} is the full file name (including the path).

"nano" is a very simple text editor.
......

Lloyd B.

It's to late here in Florida for me to boot back into Ubuntu, but I will definitely try it tomorrow.

I was close! 
I already tried sudo edit {file}.
If I had tried sudo editor {file}, I would have been closer!;) 

Jack

---

### Post by lloyd_b on 2006-12-10
Well.... If you had typed "sudo editor {file}" you would have had access to the file.  But I *believe* that the default editor is "vim", which is NOT newbie-friendly (that's why I referenced nano instead).:) 

If you're familiar with an of the "vi" variants (vi, vim, elvis, etc), then I'd recommend using "vim" instead of "nano" - it's much more powerful (just has a steeper learning curve).

Lloyd B.

---

### Post by stewjack on 2006-12-11
> **lloyd_b said:**
> Well.... If you had typed "sudo editor {file}" you would have had access to the file. 

Lloyd B.

Actually, I thought I was just kidding.  :p 

Bye the way, I followed your instructions and got Kppp working, also for a reason I can't explain, 
I also got the graphical driver Gnome-ppp working.  

Gnome-ppp is now complaining that it can't access the doc,
or maybe it's the script, "pap-secrets"  
(I didn't provide the path because I am in windows now,
 and can't remember what it was, but the file does exist.)

I will try and modify some permissions  

 :-k 
Would [ sudo open {file} ] allow me to modify permissions?

What about [sudo run {file} ]?

Jack

Note: This is my second attempt in 24 hours to reply 
to your last post.  I guess I failed to hit the 
"Submit Reply" button the first time. :oops:

---

### Post by lloyd_b on 2006-12-12
> I will try and modify some permissions


Would [ sudo open {file} ] allow me to modify permissions?

What about [sudo run {file} ]?

There *is* an "open" command, but it starts up a new terminal session on a specified virtual terminal (not what you're looking for).

The correct command for changing permissions is "chmod".

For more info on how to use this (or just about any command line command), type "man {command}" - this will bring up the "man page" (Manual Page) for the command.  Man pages aren't really all that detailed, but they generally provide the basics of how to use a command.

FYI - To find out if a given command exists, type "which {command}" - if this returns something, then try "man {command}" to see what it does.

Lloyd B.

---

### Post by stewjack on 2006-12-14
> **lloyd_b said:**
> 
The correct command for changing permissions is "chmod".

For more info on how to use this (or just about any command line command), type "man {command}" - this will bring up the "man page" (Manual Page) for the command.  Man pages aren't really all that detailed, but they generally provide the basics of how to use a command.

FYI - To find out if a given command exists, type "which {command}" - if this returns something, then try "man {command}" to see what it does.

Lloyd B.

Thanks for your help.  :D  
I have got good 2D graphics, I have sound because I can hear the Ubuntu "chord," and I have a graphical dial-up connection to the Internet.  

Next, I will try playing with the terminal, a bit, using your suggestions.



Jack

---

