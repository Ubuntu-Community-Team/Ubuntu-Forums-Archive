---
title: "The final strugle to get rid of the &quot;Windows Addiction&quot;"
date: 2007-07-11
forum: General Help
---

### Post by KnightOnline on 2007-07-11
I've been using windows for as long as I can remember (over 10 years) and only changed my pc into a Linux box a couple of weeks ago. I really love the decision I made as I find Ubuntu a excellent operative system full of goodies far superior to Windows. 

However there are still a few things "missing" that are making it hard for me to completely get rid of using windows:

1. Lack of a great ID3 Tag Editor, I used to use Tag & Rename, a tag editor that would retrieve the tags and cover information from Amazon.com and then rename the file using my renaming conventions.

2. No support for my built-in card reader. I'm using a Compaq Presario R4000 laptop, and the 6-in-1 built-in card reader isn't working, I have no idea how make it work (i don't even know its brand).

3. I've noticed that most programs don't act very well when opening files from Samba share folders, some of them simply refuse to open the files at all. Is there a way to overcome this? Is this also the case with network folders formated in a linux native file system? 

4. I think the big red shutdown button in Ubuntu looks really cool. Its a pity that since i enabled XGL, the "shut down" option disappeared, and I have to log out before I can perform a proper shutdown, is there a way to fix this?

I really don't wanna go back to using Windows just because of these things, but they are still annoying, any help in fixing them would be greatly appreciated

---

### Post by luctor on 2007-07-11
I can only inform/help you on the samba share

Have a look [https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)

I followed it (more or less :) ) and now my samba share is mounted on boot up on /media/server.
Now the shared folder on my server is acting like a regular folder on my ubuntu box so all programs can read/write to it

---

### Post by statictonic on 2007-07-11
> **luctor said:**
> I can only inform/help you on the samba share

Have a look [https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)

I followed it (more or less :) ) and now my samba share is mounted on boot up on /media/server.
Now the shared folder on my server is acting like a regular folder on my ubuntu box so all programs can read/write to it

Unfortunately in gnome it doesn't seem to quite behave right when you try to open up files from a samba share unless it's mounted.  That's a good guide on mounting shares.

If you got a share between two linux boxes going on, I'd suggest using NFS instead of samba though.

---

### Post by whitingx on 2007-07-11
> **KnightOnline said:**
> 
1. Lack of a great ID3 Tag Editor, I used to use Tag & Rename, a tag editor that would retrieve the tags and cover information from Amazon.com and then rename the file using my renaming conventions.


Have you had a look at [Easytag]("http://easytag.sourceforge.net/") ?

Hope this helps.

---

### Post by Surkow on 2007-07-11
> **KnightOnline said:**
> 3. I've noticed that most programs don't act very well when opening files from Samba share folders, some of them simply refuse to open the files at all. Is there a way to overcome this? Is this also the case with network folders formated in a linux native file system?
The performance is better when using a Linux native file system.

> 4. I think the big red shutdown button in Ubuntu looks really cool. Its a pity that since i enabled XGL, the "shut down" option disappeared, and I have to log out before I can perform a proper shutdown, is there a way to fix this?

If the big red button has disappeared you can enable it again by right clicking and adding it to the panel. But if only the shutdown button disappeared you can do the following:

[quote="[Ubuntu Feisty Fawn: Missing Shutdown/Restart](http://justevolvin.wordpress.com/2007/04/28/ubuntu-feisty-fawn-missing-shutdownrestart/)"]
   1. From the top menu bar choose System
   2. Select the Administration menu option
   3. Then choose the Login Window menu option
   4. Enter your password when prompted
   5. Select the Local tab
   6. Check the box next to Show Actions Menu
   7. Make sure Include Host Names below it is checked as well[/quote]

---

### Post by KnightOnline on 2007-07-11
> **whitingx said:**
> Have you had a look at [Easytag]("http://easytag.sourceforge.net/") ?

Hope this helps.

Yes I have, not a bad ID3 Tag editor, but it doesn't have the mass tagging features of Tag & Rename and it doesn't download the album art from Amazon.com which where the main features I liked about Tag & Rename.

Still, thanks for the advice as I haven't seen any Tag editor better than this one

---

### Post by KnightOnline on 2007-07-11
> **Surkow said:**
> The performance is better when using a Linux native file system.



If the big red button has disappeared you can enable it again by right clicking and adding it to the panel. But if only the shutdown button disappeared you can do the following:


The shut-down applet is still there, but when i click on it, it only shows me the options to switch to another user, log off, hibernate or standby. This is only like this for XGL sessions, if i start a gnome session the shut-down option is there.

Is there any way to have the shut-down option in XGL sessions too?

---

### Post by Surkow on 2007-07-12
> **KnightOnline said:**
> The shut-down applet is still there, but when i click on it, it only shows me the options to switch to another user, log off, hibernate or standby. This is only like this for XGL sessions, if i start a gnome session the shut-down option is there.

Is there any way to have the shut-down option in XGL sessions too?

[This]("http://ubuntuforums.org/showthread.php?t=244662") topic might solve your problem. It shows lots of people having the same problem (and solutions for it). On the third page people talk about specific XGL problems.

---

