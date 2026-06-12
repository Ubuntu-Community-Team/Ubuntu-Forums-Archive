---
title: "[SOLVED] Nautilus folder contents could not be displayed."
date: 2007-10-30
forum: General Help
---

### Post by Scratches on 2007-10-30
Hiya all, another first time poster here (Yeah, my first bean!).  I switched to Ubuntu from WinXP about 2 weeks ago.  My wife and I are both loving it.

We are both having the same problem.  Both of us are running Ubuntu Gutsy on clean formatted drives with no reference to windows except maybe .wma which I'm currently converting to .mpg.

We are networked on the same router but not sharing directories, just using the same router to access the internet.

The problem both of us are having is randomly we are getting error messages when browsing local folders and attempting to open up another folder.

   The folder contents could not be displayed.
   Sorry, couldn't display all the contents of "folder name".

We both are doing a lot of file moving between folders when this error randomly pops up.  When this happens and if we try clicking on a file that is already in an open folder, the file icon turns into a document style icon.

I've browsed and google'd for over a week now and the only thing I can find similar to this problem is accessing shared windows folders over a network.  Not sure if this is related but we aren't networked to windows, nor sharing folders between computers.  In fact, I haven't even figured out how to share folders yet.

I can temporarily fix the problem by closing the Nautilus Process, when it restarts, eventually this error happens again.  I've even tried reformatting my computer and reinstalling fresh to see if something was corrupted, it didn't fix it.

Thanks for your time, any help is appreciated.

Tom

---

### Post by jonobr on 2007-10-30
WOuld it be that you are copying in large files and they are not yet copied?
If you go to the terminal screen, applications--> accessories--> terminal
(this places you in your home directory) when you navigate to your folder and do an ls -l command repeatedly is the file increasing in size?

Does the ls -l show the same as nautilus,

If you need more info  on how to do this ,  let me know,,

---

### Post by paul.matthijsse on 2007-10-30
> **Scratches said:**
> The problem both of us are having is randomly we are getting error messages when browsing local folders and attempting to open up another folder.

   The folder contents could not be displayed.
   Sorry, couldn't display all the contents of "folder name".I guess you are moving files to non-regular-user dirs like /root, or some other system dirs with restricted access. Keep on moving your files, as long as they stay in the /home/<username>/yourdir hierarchy. In other words, keep your personal files in your personal home directory. Hope this helps. 

Cheers, Paul.

---

### Post by Scratches on 2007-10-30
Nope, just reorganizing music folders and such, the most maybe 5 meg files.

We are moving single files, sometimes a CD group of files, but nothing out of the normal.  It errors not on moving the file, but attempting to open a new folder.  If I attempt to open a file in an already open folder, the file icon changes to a document style icon.

This just completely happens at random, yet it continues to happen.  The only fix short of rebooting is ending the nautilus process.

Thanks

Tom

---

### Post by Scratches on 2007-10-30
> **paul.matthijsse said:**
> I guess you are moving files to non-regular-user dirs like /root, or some other system dirs with restricted access. Keep on moving your files, as long as they stay in the /home/<username>/yourdir hierarchy. In other words, keep your personal files in your personal home directory. Hope this helps. 

Cheers, Paul.

Nope, just moving files about in my home directory.  Example, moving files from "Music" to "Music Video" folders and such.

---

### Post by gate on 2007-10-30
I also have this problem, as several other people. It seems limited to music files when browsing and looking at them one at a time.
  Original thread: [http://ubuntuforums.org/showthread.php?t=592626](http://ubuntuforums.org/showthread.php?t=592626)

---

### Post by Scratches on 2007-10-30
> **gate said:**
> I also have this problem, as several other people. It seems limited to music files when browsing and looking at them one at a time.
  Original thread: [http://ubuntuforums.org/showthread.php?t=592626](http://ubuntuforums.org/showthread.php?t=592626)

Thanks, been looking for awhile to find something like this.  At least I know I'm not alone with this.

Thanks

Tom

---

### Post by jonobr on 2007-10-30
misery loves company:-)

Sorry couldnt be of more help, Agreed this seems to be a popular problem

---

### Post by waspbr on 2007-11-03
I have the same problem, I am connected to a to a T1/T3 connection provided by my university, and at the building I live there is a network where we share files. However I have notbeen able to "see" those other computers in the network.  I get the same error message "Nautilus folder contents could not be displayed."

funny thing is at first when i installed guitsy I used to be able to see other computers in my network, however I think I stopped being able to access the network just after i sorted out my internet connection. (PPPOE connection with raging penguins, with 2 DNS address given by my ISP ).

Can anyone help? I really don't know what to do, i tried tweaking samba, by changing the conf file option to browseable yes... but that did nothing. I am really lost.

O yeah, I am still a noob in linux so bear with me 

cheers

---

### Post by gearshifter on 2008-01-26
Can someone explain this.  It says the problem has been solved?  I am still having the issue here...

---

### Post by Thiago Cesar Vieira on 2008-01-27
Hi friends!

I had the same error listed by Scratches. But, here my **processor rate** stays in 100% until I kill Nautilus.

In log files /var/log/[syslog, messages, etc] no Nautilus log entry is found. But, a new file **~/nautilus-debug-log.txt** shows a lot of lines like the second one:
> 
===== BEGIN MILESTONES =====
0x7562e0 2008/01/27 14:18:15.8818 (USER): debug log dumped due to signal 11

I tried to remove **~/.nautilus directory**. But, when I restart my machine, the same error persists!

I have Ubuntu Gutsy 64 bits and my system is "up to date", with all updates instaled.


Mistery...

---

### Post by peddy on 2008-03-31
same here

---

