---
title: "Can't Run Synaptic and Other Tools"
date: 2004-11-27
forum: General Help
---

### Post by mojorising on 2004-11-27
When I try to run Synaptic and other tools like the login screen setup program -- basically anything requiring root access -- I get an error like, "Failed to run /usr/sbin/synaptic as user root: Child terminated with 1 status.

I have set up the root account and use this instead of sudo, which is where I think the problem stems from but I am not sure what do do about it. 

Does anyone know how to fix this issue? I would greatly appreciate it!

Thanks, 
Mike

---

### Post by WW on 2004-11-30
If you are trying to run Synaptic from the menu Computer->System Configuration, you must still enter **your** password (not root's) when you are prompted.  It doesn't matter that you have set up the root account.  This menu runs Synaptic with **gksudo**, which is the graphical version of sudo.

---

### Post by mojorising on 2004-12-01
I do enter my password. Still does not work. If I did not, surely it would produce a different error. 

I have made some progress on the issue.

Running synaptic or gdmsetup from a console  produced this error: "(synaptic:5077): Gtk-WARNING **: cannot open display:"

So I googled part of that message and figured this out from picemealing advice from others on similar problems..

If I type xhost + at the command line and then su - (enter pw),
Type export DISPLAY=:0.0 as root 
I can then run synaptic and gdmsetup from the console temporarily until I close that console. 

Now all I need is a permanent fix. I am sure there is one but I am not knowledgable enough to know what it is. If anyone could provide the last bit I need, that would be awesome!

Thanks again,
MIke

---

### Post by poptones on 2004-12-01
Check /etc/hosts and see if there in an entry for your machine name. If there isn't one, make one like so:

127.0.0.1 *machine_name_here*

---

### Post by WW on 2004-12-01
> I do enter my password. Still does not work. If I did not, surely it would produce a different error. If I enter the wrong password when running Synaptic from the menu, the message you reported is exactly the error message that I get in an Error window:
> Failed to run /usr/sbin/synaptic as user root:
 Child terminated with 1 statusThat's why I thought you might be entering the wrong password. But it looks like your problem wasn't as simple as that.  Sorry I couldn't be more helpful!

---

### Post by mojorising on 2004-12-01
Ah, thanks for the tip, WW.

I did check my /etc/hosts file and my hostname is there. The first line is:
127.0.0.1       localhost.localdomain   localhost       bm

bm is my hostname and, as you can see, it is there but I still have the problem.


Mike

---

### Post by filattiera on 2004-12-03
I have the same problem.

I think that it can be a permission problem to the usr/sbin or usr/bin folders, because it occured to me after a chown -R root:root usr/sbin done after the lamp installation.

I don't try to resolv this problem in any way...

Ciao.
Luke

---

### Post by jdong on 2004-12-03
[QUOTE=filattiera]I think that it can be a permission problem to the usr/sbin or usr/bin folders, because it occured to me after a chown -R root:root usr/sbin done after the lamp installation.
[/QUOTE]

Golden (err, teflon-coated) rule of distros with a package manager: **don't EVER EVER EVER EVER EVER ... add, remove, or modify stuff in the directory trees!!** That's what the /usr/local tree is for! and /opt!

---

### Post by mojorising on 2004-12-06
I'm not sure what caused it fomr me. It seems like it was like that since I installed it but it could be the result of something I did or installed right after installing the OS. 

Does anyone know how I can fix it? I'm thinking I just need to put xhost +  and export DISPLAY=:0.0 as root  in a script and hten have that run at start-up I'll be set.

MIke

---

### Post by nomaand on 2005-01-09
I also recently had this problem. After I debootstraped a new ubuntu installation onto an evms volume.

This problem was easily fixed by running:
```
visudo
```
and adding 
```
{username}   ALL=(ALL) ALL
```
to the file. Usually this is done by the installer I must have missed something after the bootstrap

nomaand

---

### Post by wallijonn on 2005-01-09
[QUOTE=mojorising]When I try to run Synaptic and other tools like the login screen setup program -- basically anything requiring root access -- I get an error like, "Failed to run /usr/sbin/synaptic as user root: Child terminated with 1 status.

**I have set up the root account and use this instead of sudo**, which is where I think the problem stems from but I am not sure what do do about it. [/QUOTE]

So, what happens when you open up a Root Terminal and "su"? When you open up a User Terminal and "su"? And issue the command [COLOR=Red]/usr/sbin/synaptic[/COLOR]

I would think that if you are using the Launcher you would have to remove "gksudo" from the SPM properties Command.

Basically, now that you have "created" a root user account you must issue all root commands from a root terminal. Which means that you may as well remove SPM from the menu launcher. Nah...

---

### Post by pirast on 2005-03-05
@nomaad: it is already in the file.

@wallijonn 

when i open a root terminal and su and issue the command synaptic, synaptic starts.

gksudo is not installed.

---

### Post by matthieufecteau on 2005-05-03
I think (not sure!) that the root of the problem (synaptic and other apps not starting) is because, for some people, the loopback interface is not started at boot.  This bug prevent cups (the printing system) to function, and also other apps like apache I think.

I posted the solution to this problem in the second post of this thread :
[http://www.ubuntuforums.org/showthread.php?p=157434#post157434](http://www.ubuntuforums.org/showthread.php?p=157434#post157434) 

It's not the ideal solution (technically), but it works for me.  It could use the sysV init scripts (runlevels, etc.) instead, but I don't know how.

---

### Post by pirast on 2005-05-04
Since I am using hoary  it's working well  :) 

Thanks,
Martin

---

### Post by pintong on 2005-06-21
[QUOTE=jdong]Golden (err, teflon-coated) rule of distros with a package manager: **don't EVER EVER EVER EVER EVER ... add, remove, or modify stuff in the directory trees!!** That's what the /usr/local tree is for! and /opt![/QUOTE]
I did the exact same thing, being the newbie I am. I chown'd /usr/bin - what do I need to do to change it back?

---

### Post by darrylm on 2005-09-06
Actually Nomaand was right about editing the sudoers file in /etc via the command visudo.

I had this problem after I deleted the account that was created using the installer.  I created a new account via adduser in a terminal using the root account.  When I rebooted ubuntu (had to because I was doing other things aswell) and went into the wm I tried to use root terminal and synaptics and was getting something "Failed to run blah. Status 1".  This is when I googled the error msg and hit this page.  I followed his instructions and added a new line for user for the newuser that I created to the sudoers file (NOTE: this is inclusive of the root entry, I suspect this is where some of you went wrong before).  When I reran the apps they worked perfectly fine.

So big kudos  to Nomaand :D

ps. Im running Ubuntu 5.04 (hoary).

---

### Post by justadam on 2006-03-02
I agree.  Editing the 'sudoers' worked for me as well.  I am using BB 5.1.  However, know that I installed the software from the download image.  I went through the appropriate steps to create a user during the installation process.  It obviously did not update the 'sudoers' file.  I understand you don't want root launching the GUI desktop for security purposes.  However, nothing works for the added user unless you make Nomaand's recommend change.  You are stuck running all of these commands from the console instead.  Perhaps this is a bug with Breezy?  Or, should I revisit the settings of this file to protect my system? 

 Believe me I have tried this install/reinstall a number of times both with creating a new partition [clean install]  and using an existing [unclean install].  The only solution was to edit the 'sudoers' file.  A>AM

---

