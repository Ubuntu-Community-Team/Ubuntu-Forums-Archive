---
title: "Make executable bash script run with sudo privileges?"
date: 2020-01-12
forum: General Help
---

### Post by bingbong6 on 2020-01-12
EDIT: 

1) First off, yes, I'm aware that this is a bad security practice and I should not make a habit out of doing this, and I realize I should try to limit the scope of these privileges as much as possible. 

2) I've also read the sudoers manpages and visudo manpages, as mentioned in the askubuntu post.

3) If any of you are askubuntu users, I've placed a bounty (my first) on my question there. So feel free to comment there if you have a suggestion to answer my question.



(Original post below)
__________________________________________

Ubuntu 18.04 Gnome de.

I made a simple bash script file that flags my next reboot to choose the windows grub entry. For quick rebooting into windows straight from Linux DE. Here it is:


```

#!/bin/bash
sudo grub-reboot 2
sudo reboot now

```


The problem is I have to use dconf to modify executable files to ask, so I can click run in terminal where it automatically asks for password. Otherwise, just executing the file does nothing, bc it's waiting for a password input.

**Is there a way to run a bash script file like this with inherent sudo privileges so it doesn't need to ask for a password? I want to be able to double click the executable on my desktop or a shortcut to it, and have it execute without need for a password or  prompt for  password**. 

bash script file is named restart2windows and is located on my desktop:

```

/home/myusername/Desktop/restart2windows

```

So would I just need to add this following lime to the /etc/sudoers file via sudo visudo?:

```

myusername     mymachinename = NOPASSWD: /home/myusername/Desktop/restart2windows

```

---

### Post by SeijiSensei on 2020-01-13
You can remove the "sudo" from the commands, then run the whole script with sudo from the command prompt. You'll still need a password though. I haven't played around with sudoers enough to know how to avoid a password entirely.

---

### Post by bingbong6 on 2020-01-13
yeah I know I can do that, but my intent is to just double click that executable and have it reboot to windows. I know I'm being picky, but it would be useful to learn anyway.

---

### Post by TheFu on 2020-01-13
There's a NOPASSWD option.
When modifying the sudoers with nopasswd, be certain you 
*  don't lock yourself out
*  only impact the exact command you want to impact
* restrict the options to only those which are actually desired, not every possible option
* only impact a single userid, not all of them

In general, setting up nopasswd with a script that isn't owned and protected by root is considered poor security. The script needs to be in /root/bin/ , IMHO.

As to how to make it work with a mouse, I wouldn't know.
The sudoers manpage is a work of art, IMHO.
```
...
     PASSWD and NOPASSWD

       By default, sudo requires that a user authenticate him or herself
       before running a command.  This behavior can be modified via the
       NOPASSWD tag.  Like a Runas_Spec, the NOPASSWD tag sets a default for
       the commands that follow it in the Cmnd_Spec_List.  Conversely, the
       PASSWD tag can be used to reverse things.  For example:

       ray     rushmore = NOPASSWD: /bin/kill, /bin/ls, /usr/bin/lprm
....

```

---

### Post by bingbong6 on 2020-01-13
@TheFu  I guess I should have stated that I am indeed aware of the "bad" security practice of doing this. I'm also aware, that if I am going to do this, I should try to limit the scope to the bare minimum of what I need it to do. The guy from the askubuntu thread said the same thing. He also pointed me to the manpages of which I have since read. I will edit my post to reflect this.

That said, I tried to follow the manpages but it still will not work as intended. 

But you don't know the answer to my question?

---

### Post by TheFu on 2020-01-13
> **bingbong6 said:**
> @TheFu  I guess I should have stated that I am indeed aware of the "bad" security practice of doing this. I'm also aware, that if I am going to do this, I should try to limit the scope to the bare minimum of what I need it to do. The guy from the askubuntu thread said the same thing. He also pointed me to the manpages of which I have since read. I will edit my post to reflect this.

That said, I tried to follow the manpages but it still will not work as intended. 

But you don't know the answer to my question?

Was the script fixed by placing it into /root/bin/, chmod 700 the file, ensure the file is owned by root, remove the sudo commands from inside it and use full paths to the 2 commands?

"not working as intended" isn't clear.  What, exactly, does that mean?  Please assume we cannot read minds.  Also, showing the real, exact, line that you put into the sudoers would help - as would using *code tags*.  The `` don't work here.

---

### Post by bingbong6 on 2020-01-13
I want to double click the executable or Shortcut to it and have it execute with no further input. I thought I stated that in the original post but I guess I didn't.

I will have to try that suggestion after work to tomorrow night. Thank you 

I'll edit the line of code I put into the sudoers file, with code tags. I assumed this place used markdown like the rest of the internet....

Edit: from the askubuntu post :

> The path of grub-reboot command. Not the path to a script on your Desktop. To find the path of a command: which *name of command*, for example: which grub-reboot. Will return: /usr/sbin/grub-reboot. That is the PATH to apply in you sudoers file . The path to the command you intend to use in your script   

So with that suggestion, would you still advise moving the script file to the root/bin/ directory?

---

### Post by TheFu on 2020-01-14
I've made recommendations already.  I think you should follow them, but only you can decide that.

I don't use markdown anywhere. I'm a texttile user. Regardless, forums seldom support markdown, IME.  They use something called "bb-code".  Thanks for the code tags. That makes things clearer.

/root/bin/
    is not the same as 
root/bin/

Please ensure you understand the difference or this solution will be impossible to implement.

Yes, you were clear that you wanted to point-n-click to accomplish this.  Should I not attempt to help because I only know 2 of the 3 parts to the solution?  Plus, I think the parts I know about are more difficult than that last part.  All 3 parts are required.

---

### Post by CatKiller on 2020-01-14
> **TheFu said:**
> Yes, you were clear that you wanted to point-n-click to accomplish this.  Should I not attempt to help because I only know 2 of the 3 parts to the solution?  Plus, I think the parts I know about are more difficult than that last part.  All 3 parts are required.

The last part is trivial once there's a command and permissions that work. Launchers to run a command when you click on them are just .desktop files - simple text files.

---

### Post by CatKiller on 2020-01-14
> **bingbong6 said:**
> So with that suggestion, would you still advise moving the script file to the root/bin/ directory?
For clarity, TheFu's (sensible) suggestion is orthogonal to the actual function.

/root is the root user's Home directory, and will be on the same partition as / even if /home is on a different partition, which is useful should things go pear-shaped at any point. This is standard practice going back decades.

The various bin directories are where programs to be executed ("binaries") live. Again, going back decades.

In general, but *especially* when dealing with security, it is very important to keep things organised, so that you don't forget something critical. This script that you want to run is something that you want to run as root, so putting it in root's bin directory is a sensible way to remember what it's for, and to restrict write access to it. You wouldn't want untrusted users, or malicious external parties, to be able to fiddle with it.

For the function of your script, it would be the commands inside it that you would need to be able to run as root with no password. You should also specify within that script the full paths to the commands that you want to run, as TheFu says, so that no one can substitute a different file with the same name instead.

---

### Post by CatKiller on 2020-01-14
> **bingbong6 said:**
> The problem is I have to use dconf to modify executable files to ask, so I can click run in terminal where it automatically asks for password. Otherwise, just executing the file does nothing, bc it's waiting for a password input.

Again, orthogonal to the answers you've had about the permissions side of things, both of these are simple to solve. If you have a launcher that runs your script, which is sensible, running it in a terminal is a simple flag (Terminal=true), but even better would be to use PolicyKit (the replacement for both gksudo and kdesu) instead of sudo by running pkexec <command that you want to run>. That pops up the same password dialogue that you get when, for example, updating software.

---

### Post by bingbong6 on 2020-01-14
@CatKiller Thanks for the clarifications and explanations! Couple questions:

1. regarding TheFu's suggestion to place the script in:
```

/root/bin

```

wouldn't I put it in
```

 /root/sbin 

```

since from my research, sbin is meant for binaries that have root only privileges? 

2. The suggestion of placing the full file path of those commands, in my script; how would I designate which grub entry to boot to? I have edited it to:

```

#!/bin/bash
/usr/sbin/grub-reboot
/sbin/reboot

```

but I need to set it to choose grub option 2 (windows boot entry).

Thanks for explaining the necessity and logic of placing this type of file in the /root/bin (should be /root/sbin ?) that makes complete sense.

---

### Post by TheFu on 2020-01-14
Somewhere under /root/ is what is important.  There's nothing special in a HOME directory, so most userids don't have bin/ and sbin/ subdirs.  Either will pre-exist, so you'll need to mkdir anyways.  If you look at /root permissions, you'll see why it just doesn't matter, assuming a basic understanding of permissions exists.

If you want to talk about /usr/local/bin vs /usr/local/sbin, then you have nailed it. I would definitely place an admin tool that I built by hand, not through a package, in /usr/local/sbin/ if I intended for all admins on the box to have access.  When it comes to scripts that can harm a system, then I want it to be harder to run, hence the /root/bin/ recommendation. Nobody can run it without sudo AND they will need to know the exact filename + path to access it.

Seems you may have missed some prior knowledge that an admin would need to know.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

---

### Post by bingbong6 on 2020-01-14
**EDIT: **I was able to create a symlink to the file and move it to my desktop and execute it by double clicking it. It immediately reboots, but again, not sure how to designate the grub-reboot full path command, to select entry 2....

ORIGINAL POST FOLLOWS:

@TheFu thanks for explaining the different use cases of /root/bin/ vs /usr/local/bin and /usr/local/sbin

Yeah I'm still learning and I've been working through linuxjourney.com but I will also check out that book (linuxcommand.org) as well, thanks.

I'm working through this and almost have it, but I'm just stuck on how to designate the grub-reboot command to choose entry 2, when executing it as it's full file path. I'll explain below:


I went ahead and made the changes to the sudoers file via sudo visudo as follows:


```

#includedir /etc/sudoers.d
myusername     mymachinename = NOPASSWD: /usr/sbin/grub-reboot, /sbin/reboot

```


those command locations were determined by running:


```

which grub-reboot
which reboot

```


THEN I left my script file on my desktop (for testing purposes), and left it to read:


```

#!/bin/bash
grub-reboot 2
reboot now

``` 


and choose to RUN it at the prompt, and it works! It reboots and selects entry 2 (windows).


BUT, I'd still like to do this the right way with the proper security you've mentioned:


I tried changing the commands to:


```

#!/bin/bash
/usr/sbin/grub-reboot
/sbin/reboot

```


Wasn't sure how to tell it to choose entry 2 with the grub-reboot command. Read some [manpages]("https://manpages.ubuntu.com/manpages/bionic/man8/grub-reboot.8.html") about grub-reboot and it mentioned using greater than symbol (>) after the command with no spaces, followed by the grub entry. This did not work, it still chose the default entry 0. Perhaps I was doing it wrong. I tried

```

/usr/sbin/grub-reboot>2

```

and 

```

/usr/sbin/grub-reboot >2

```



and

```

/usr/sbin/grub-reboot> 2

```




No luck. 



But I still then moved it to:


```

/root/bin/

```


and set the file to have permission 700 with:


```

chmod 700 bin

```


Then I wasn't sure what to do or how to run it from there. I want to double click a file or shortcut on my desktop, but I'm not sure how to link that file to my desktop. Perhaps with symlinks as outlined [here]("https://linuxize.com/post/how-to-create-symbolic-links-in-linux-using-the-ln-command/") can't use hardlinks because my /home directory is on it's own partition separate from /

so my outstanding questions now are:

**1) How to point the full path to the grub-reboot command to use grub entry 2, and**

[s]**2) how to execute the executable from an icon/file on my desktop (with symlinks? about to try that)**[/s]

---

### Post by CatKiller on 2020-01-14
> **bingbong6 said:**
> Wasn't sure how to tell it to choose entry 2 with the grub-reboot command. 

You already know how to do that:

> ```

#!/bin/bash
grub-reboot 2
reboot now

``` 


and choose to RUN it at the prompt, and it works! It reboots and selects entry 2 (windows). 

When specifying the full path to grub-reboot rather than having the shell expand it for you the syntax doesn't change. You've apparently already established that the simple *2* is what works for you. 

> I was able to create a symlink to the file and move it to my desktop and execute it by double clicking it.

Eesh, that's horrible. What if you wanted to run it from your panel, or a dock, or a menu? What if you wanted it to look different? Or to have a descriptive name? 

A .desktop file is what you're after rather than a symlink to the file, as I said upthread. You can just drag and drop one of the entries from your menu into a text editor to see the structure, and there are plenty of guides about, as well as the specification of the format.

---

### Post by bingbong6 on 2020-01-14
@CatKiller 

I thought you guys said to change it to the full path so it couldn't be changed and exploited? Or did you mean changing it so that I didn't need sudo so that someone couldn't just swap out the command following sudo?

Well, I somehow broke that symlink and now I can't recreate it. Says it's owned by root and has a big red x on the icon. When I double click it now, it says it's a broken symlink and tells me to delete it. Weird. 

Not sure what entries nor what menu you're referring to, but I did find several guides. I will try that instead.

---

### Post by bingbong6 on 2020-01-14
Yeah so I'm done with this. I just accidentally deleted my bin folder. I thought I was in /root/ but it was /. Only difference on command line was ~ VS /.

So in the future, if I try this again, I will NOT make another bin folder within my root folder. 

I do have a full system backup. But I was hoping that I could just restore the root partition. I have timeshift setup to backup rsync snapshots of / partition and /home partition. 

I know we're off topic but I have your attention and would appreciate a suggestion. I cant login so I'm booting from a live disk and seeing if I can either copy the bin folder over from my backup, or do it through timeshift on the live disk

---

### Post by TheFu on 2020-01-14
Sorta disconnected stuff follows .... 

```
myusername     mymachinename = NOPASSWD: /usr/sbin/grub-reboot, /sbin/reboot
```
shouldn't work.  Is your username really "myusername" and the hostname really "mymachinename"?

You are trying to do something that normally wouldn't come up until the 2nd year being an admin. Please recognize that skipping over the year as a normal user, becoming a power user, then a full year as a working admin would teach the basic skills which seem to be missing.  Avoiding issues is always better, than having to fix it later.

I wouldn't have put **grub-reboot** or **reboot** into the sudoers file when I only wanted this 1, single, shell script to be used. Would have put the full-path to the script in /root/bin/whatever-you-call-it there.  OTOH, there are 50-500 different solutions. 
```

#!/bin/bash
/usr/sbin/grub-reboot 2
/sbin/reboot now
```

Though I thought reboot was deprecated and I'd probably use **/sbin/shutdown -r now** instead.  Looking on one my my servers, 
```
$ ll /sbin/shutdown /sbin/reboot 
lrwxrwxrwx 1 root root 14 Nov 26 17:34 /sbin/reboot -> /bin/systemctl*
lrwxrwxrwx 1 root root 14 Nov 26 17:34 /sbin/shutdown -> /bin/systemctl*

```
so both are deprecated and we should be using **systemctl** with specific options, it seems. That would complicate your sudoers file, but not mine.  Allowing systemctl to be run with any available options could be really bad. Terrible.  Lots of power in that command to which I wouldn't want just any casual admin to have access.

---

### Post by bingbong6 on 2020-01-14
Yeah I'm giving up on this and just manually typing it in the terminal with sudo and password. Just thought this would be a learning opportunity. I do appreciate your help thus far. I'm definitely getting in over my head. Better to save this sort of experimenting for on my rpi that I can just swap out the sd card for tinkering and learning. 


I did learn some stuff though. Like not to make a /root/bin directory or rather, not to make it and then try to delete it since it's eery easy to misread where you are currently at in the terminal... Please take a look at my other comment just before yours.......

---

### Post by TheFu on 2020-01-14
> **bingbong6 said:**
> I know we're off topic but I have your attention and would appreciate a suggestion. I cant login so I'm booting from a live disk and seeing if I can either copy the bin folder over from my backup, or do it through timeshift on the live disk

50% of a backup is the data. The other 50% is the owner, group, permissions, any ACLs.  If you don't have 100% in your backup data and know how to restore is all, then
a) you need better backups
b) you need to learn to restore so all that is retained

I don't use timeshift and have never looked at it. Sorry. Can't help.  

I use rdiff-backup and have 90-180 days of versioned backups for all my systems.  About once a year, I'll do something stupid and need to restore a file, directory or maybe entire system.  Every few years, a HDD will fail, so I get to restore 1 or 15 systems. Just depends on how many virtual machines are on the disk.  
When I was a really new admin,  I wrote a tiny script to clean up some cache files.  Unfortunately, it found / (the file system root) and did a recursive delete of the entire OS.  Fortunately, I had a cdrom in /cdrom and all the failures to delete jumped out at me.  Also, I'd just make a ufsdump the night before, so I had a clean backup.  But I didn't have a clue how to restore it and didn't have a working system that could boot. It wasn't linux, it was Solaris on a $50K workstation. A $25 book had all I needed to know. About 2 hrs later, the system was restored and everyone using that system  in the company was none-the-wiser. ;)

My point is that you aren't the first and won't be the last to make a mistake and need to fix it.  We all have those scars.  Having excellent backups does let me take more chances than I would have without them.

---

### Post by bingbong6 on 2020-01-14
Well nonetheless. Thanks for all of your input thus far. My really important data is stored off system on a flash drive and an external hdd. But I just don't want the inconvenience of setting up my desktop again. Maybe use the opportunity to distro hop haha.

 BTW timeshift is just a nice gui with scheduling built in that just uses rsync at its core.

---

### Post by TheFu on 2020-01-14
> **bingbong6 said:**
> 
 BTW timeshift is just a nice gui with scheduling built in that just uses rsync at its core.

rsync has some failures as a backup tool. For example, when using the hardlinking capabilities to provide versioned backups, it cannot track changes to the owner, group, permissions or ACLs.

Most backup tools on Linux have some part of rsync used, but the better tools handle the file metadata in their versioning too.

I get that lots of people want a GUI for backups.  Most of my systems don't have a GUI, so that would be useless to me.  Also, running a GUI under sudo is asking for trouble. It is a good way to cause permission issues with a userid.  

Tip: Whenever using sudo with a GUI programs - first - don't.  But if you must, always use **sudo -H** so the HOME directory gets modified too.

---

### Post by CatKiller on 2020-01-15
> **bingbong6 said:**
> @CatKiller 

I thought you guys said to change it to the full path so it couldn't be changed and exploited? Or did you mean changing it so that I didn't need sudo so that someone couldn't just swap out the command following sudo?

I mean that in your script you'd simply have ```
/usr/sbin/grub-reboot 2
```

---

### Post by CatKiller on 2020-01-15
> **TheFu said:**
> so both are deprecated and we should be using **systemctl** with specific options, it seems. That would complicate your sudoers file, but not mine.  Allowing systemctl to be run with any available options could be really bad. Terrible.  Lots of power in that command to which I wouldn't want just any casual admin to have access.

Actually, systemd turns it into a one-liner:

```
pkexec systemctl reboot --boot-loader-entry=windows
``` and you can easily configure polkit to allow the user to do **only** that action without a password. It is much less fragile than sudoers.

---

### Post by CatKiller on 2020-01-15
> **bingbong6 said:**
> My really important data is stored off system on a flash drive and an external hdd. But I just don't want the inconvenience of setting up my desktop again. 

All your user settings are in /home (that's what it's for) so copying those back into a fresh install will make everything how it was. There are also commands for listing every package that you've installed so that you can automate reinstalling them in a fresh install.

---

### Post by CatKiller on 2020-01-15
For completeness: > **bingbong6 said:**
> Not sure what entries nor what menu you're referring to, but I did find several guides. I will try that instead.

Gnome used to default to a standard drop-down menu for launching applications, and many desktop environments still do.

Desktop files are agnostic ways of defining the properties of something that you want to launch. The launcher menu, any docks you use, the panel, the context menu, and launchers on the desktop are all controlled the same way, and it works for all desktop environments. Because of that abstraction of listing the attributes in a text file it's much more flexible and prevents you from, say, deleting important files when you just want to change how it runs.

---

### Post by bingbong6 on 2020-01-15
@catkiller

Is there anyway to just restorey /bin file only? I have the backup. Others have mentioned fire up a live disk, go into terminal as root (which I will avoid in the future bc this is what got me in this pickle), then copy the /bin file from my backup to my system root. Any reason this wouldn't work or at least wouldn't be worth a shot?

---

### Post by CatKiller on 2020-01-15
It's definitely worth a shot. If you simply deleted that directory, and your backup contains that, then that's what your backup is for.

---

### Post by bingbong6 on 2020-01-15
I know some would disagree, but I don't mind when stuff like this happens. I have external backups of important data and my home desktop is just for play anyway. I always learn something when I break stuff. In this case, I learned the hard way what everyone warns about avoiding logging in and doing stuff as root in the terminal. 

I'm not a sys admin or any computer related career. I'm a Mechanical Engineer and that's how I've always learned; tear stuff apart to learn how it works and then put it back together. Probably not always the right approach with computers, but that's more or less what I was trying to do with executable. Seemed like something worth exploring to learn a thing or two. 

I think for now, I will just continue to use my script via terminal and enter a password. I mentioned that I was using dconf to force a prompt when double clicking an executable file, and you mentioned that I could just use a flag terminal=true to achieve this. **How do I set a terminal=true flag on my executable?** 

I think I'll avoid the nopasswd method Until I learn more about good security practices and how to edit permissions etc. Think I got a bit ahead of myself. I appreciate your help and TheFo's help.

---

### Post by CatKiller on 2020-01-15
> **bingbong6 said:**
> I always learn something when I break stuff.  

That is a perfectly healthy attitude. I broke a bunch of stuff in the beginning, too. 

>  I think for now, I will just continue to use my script via terminal and enter a password. I mentioned that I was using dconf to force a prompt when double clicking an executable file, and you mentioned that I could just use a flag terminal=true to achieve this. **How do I set a terminal=true flag on my executable?** 


It's not for the script, it's for the launcher that launches the script. As I mentioned earlier, that abstraction is very handy. You can put your script wherever makes sense for that, and have your launcher wherever you need to launch it from.

There's a post [here](https://ubuntuforums.org/showthread.php?t=2364670), in a different context, that describes a bit about how the desktop files work. I think there were links to more information, too. You can drag and drop into a text editor from the menu, or /usr/share/applications, if you want to see how it all works for other applications.

You can either use sudo and launch your script in a terminal, or use pkexec and launch your script without a terminal, whichever you prefer.

---

### Post by TheFu on 2020-01-15
Something else you should notes is that Catkiller and I come at the problem from slightly different ways. This is because we have different backgrounds, I'd bet. I'm trained as an ASE, worked in that area for about 5 yrs before transitioning more into software.  I come from a Unix admin, programming, huge organization background. We tried to be consistent with management of all the different systems.  So I will always prefer the more cross-platform technique to solve issues.  sudo is cross-platform.  I've never heard of pkexec on anything except Linux. If you can use the Linux-specific solutions, it can work.

Also, I've been burned a few times in scripts when I was lazy and didn't fully specify the path to every command.  Someone can change the PATH and bam - a completely different program gets used than the one intended.

In a script, I'd never use this:
```
pkexec systemctl reboot --boot-loader-entry=windows
```
though I might be tempted to use:
```
/usr/bin/pkexec  /bin/systemctl  reboot --boot-loader-entry=windows
```
When you finally get to the point of automating many things via cron, you'll appreciate this slight difference.  It is both for security and to avoid future failures.  Using the full path so that the PWD/CWD aren't important for any input to a script is a design best practice.  We see people NOT doing that here all the time and they have problems with their scripts.  Windows allowed end-users not to really know about PWD, which is critical for anyone doing scripting or programming.

Anyways, we've beaten this topic enough.  Good luck.

---

### Post by bingbong6 on 2020-01-15
Thanks, I figured that you two come from different backgrounds. Both of you have lots of history on this forum (I cautiously equate this to knowledge and trustworthiness), and you both proposed different approaches. From an outside/novice perspective, what you describe definitely seems more future proof and logical. But, I'm sure catkiller's way is able to achieve the same end result as defined by me, which is to just get it working. Anyway, I'll consider all of this should I revisit this, but I think I need to take a step back and do some reading and learning via research. Then I will use a raspberry pi as mentioned to attempt some of this stuff as a sandbox.

---

### Post by bingbong6 on 2020-01-23
@TheFu 

you don't allow direct messages so I thought I'd ask it here: I don't remember where I found it, but at some point you linked this (your?) website [https://blog.jdpfu.com/2014/12/28/learning-linux](https://blog.jdpfu.com/2014/12/28/learning-linux) 

Is there a contact section on there somewhere? Or comment section? On the about page it mentions something about leaving comments.

---

