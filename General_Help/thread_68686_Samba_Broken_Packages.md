---
title: "Samba Broken Packages?"
date: 2005-09-23
forum: General Help
---

### Post by katiad on 2005-09-23
I get this error when trying to install samba from either Synaptic or the command line apt-get. 

The following packages have unmet depencies:
samba: Depends: samba-common (= 3.0.10-1ubuntu3) but 3.0.14a-3ubuntu3~5.04ubp1 is to be installed

I have enabled the repositories suggested by ubuntuguide.org - what can do I about this? 

Thanks for your help!

---

### Post by Jonathan2007 on 2005-09-24
I also get this. Someone please come up with a solution. I need this so I can get the file sharing tab in Kcontrol (on Kubuntu) to work so I can share my Linux box for my XP box. I have samba-common installed but it is the newest version and samba wants an older version.

---

### Post by snowjunkie on 2005-09-24
I also get this message.  Has anyone any ideas?

alastair@zest-audio-sun:~$ sudo apt-get install smbfs
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  smbfs: Depends: samba-common (= 3.0.14a-3ubuntu3~5.04ubp1) but 3.0.10-1ubuntu3  is to be installed
E: Broken packages
alastair@zest-audio-sun:~$

---

### Post by katiad on 2005-09-26
Anyone got any ideas??? :(

---

### Post by Jonathan2007 on 2005-09-26
I still got no solution here. Anybody else that can help us? I am thinking one of the Ubuntu devs just has to change the dependency version on the samba package. If one of the devs could enlighten us, I am sure all of us would really appreciate it. :confused:

---

### Post by snowjunkie on 2005-09-27
Hi Guys,
I found the answer on another thread...

Comment out the two backports repositories (last two I think) and then do a ```
sudo apt-get update
```

Now try again to install samba.  This worked for me.

See thread at [http://ubuntuforums.org/showthread.php?t=68749](http://ubuntuforums.org/showthread.php?t=68749)

---

### Post by katiad on 2005-09-28
Unfortunately, commenting out the backports did not work for me. Still getting the following error.

Depends: samba-common (=3.0.10-1ubuntu3) but 3.0.14a-3ubuntu3~5.04ubp1 is to be installed


Anyone have another idea?

---

### Post by katiad on 2005-09-29
No luck yet...

---

### Post by Jonathan2007 on 2005-09-29
Yeah commenting out backports didn't do it for me either. I have reloaded the list in Synaptic several times and even rebooted. Nothing. One of the devs has to have an answer don't they?

---

### Post by msinger1 on 2005-10-10
Anyone find anything new out?  Same deal with me.

---

### Post by Jonathan2007 on 2005-10-11
Well I upgraded to Breezy and I got the samba package installed so it must be a problem with the Hoary repositories but I guess nobody cares since Breezy is gonna go final Thursday.

---

### Post by hornett on 2005-10-14
[QUOTE=Jonathan2007]Well I upgraded to Breezy and I got the samba package installed so it must be a problem with the Hoary repositories but I guess nobody cares since Breezy is gonna go final Thursday.[/QUOTE]

Well I'm still having this problem and upgrading is not an option for me at the moment since I use this machine for work. Does anybody have a solution at all?

Any help much appreciated, Andy.

---

### Post by Jonathan2007 on 2005-10-14
What I was trying to say was that somebody must have screwed up and they could have fixed this when a lot of people were still using Hoary but since almost everybody (besides maybe servers or work computers but I still think everyone should upgrade) has moved to Breezy nothing will get changed in Hoary. So you may just be SOL. I hate to say that but it just may be the truth. Or perhaps some kind soul will put out a fixed deb file for ya. But as for me and the others in this thread that were having problems we have probably all moved on to Breezy.

---

### Post by hornett on 2005-10-14
Thanks for the reply, I've decided to file a bug for this problem. Hope this is the right thing to do...

[https://bugzilla.ubuntu.com/show_bug.cgi?id=17799](https://bugzilla.ubuntu.com/show_bug.cgi?id=17799)

---

### Post by amorangi on 2005-10-15
I'm surprised I figured this as a total noob to linux:

Open the Synaptic Package Manager
Use it to REMOVE the samba-common package
Once that is done install the samba package (which will also reinstall the samba-common package).

Hope this helps.

---

### Post by hornett on 2005-10-15
[QUOTE=amorangi]I'm surprised I figured this as a total noob to linux:

Open the Synaptic Package Manager
Use it to REMOVE the samba-common package
Once that is done install the samba package (which will also reinstall the samba-common package).

Hope this helps.[/QUOTE]

Amazing, thank you! (can't believe I missed that :oops: )

---

### Post by amorangi on 2005-10-15
My problem now is I can't install the smbfs package: 

"Package smbfs has no installation candidate" 

I'm assuming it's because I need to add another repository to my sources list. Does anyone have any ideas???

---

