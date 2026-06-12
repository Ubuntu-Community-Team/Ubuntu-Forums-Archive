---
title: "Stopping one user from using instant messaging"
date: 2007-01-07
forum: General Help
---

### Post by robc02 on 2007-01-07
Is there an easy way to prevent one of my users from using instant messaging - or any other programs if I think it necessary? Each user has his or her own account. I have looked at the Users and Groups - User Privileges menu but am unsure whether any of the options will do what I want.

---

### Post by kidders on 2007-01-07
Hi there,

I can't see any way of doing this unless you force your LAN to communicate with the outside world through an authenticating proxy. That would be the only way of distinguishing one user from another.

---

### Post by meng on 2007-01-07
I guess you could change the ownership/group of the executable itself, ensure that execute permissions are restricted ("others" cannot execute), then exclude the user in question from that group. It's rather messy though.

---

### Post by kidders on 2007-01-07
Hi meng,

The other problem with that approach is that it wouldn't actually prevent anyone from using instant messaging per se ... it would only stop them doing it with that particular copy of one specific app. :-| That's why, in my response, I gravitated towards a network-level solution. Do you think the proxy idea is any good? :-k

---

### Post by meng on 2007-01-07
> **kidders said:**
> Hi meng,

The other problem with that approach is that it wouldn't actually prevent anyone from using instant messaging per se ... it would only stop them doing it with that particular copy of one specific app. :-|

Yes of course, but the OP also asked about preventing a user from executing an application. So I interpreted the question as more than just preventing use of a protocol.

---

### Post by jdm2 on 2007-01-07
I have a solution for you but it is only a simple solution.  If a person knows how to use the comand line then they probably can get around it.  Are you using ubuntu desktop?  If so then go to applications>accessories>Alacarte Menu Editor
Then you can go into it and remove the im app from the menu but it only is a temp.  solution.

---

### Post by robc02 on 2007-01-07
Just to put this in perspective - the one user is my teenage daughter. She has her own networked computer, running Xubuntu, but needs access to my computer for occassional tasks that her old hardware struggles with. I just want to dissuade her from using my computer more than absolutely necessary -and preventing her from using amsn will do just that. So a simple solution might well do, though I think she might quickly learn how to start it form the command line. 
Surely there is a often a need  to restrict certain users to only a limited number of applications?
Thanks for your help so far!

---

### Post by kidders on 2007-01-07
I'd say meng's solution is probably best. (Mine could be overkill.) Banking on people not hitting ALT+F2 and typing the name of the app they want to run would be ... well ... ineffective, imo. Many people rarely run things any other way.

---

### Post by Biggus on 2007-01-07
> **kidders said:**
> Banking on people not hitting ALT+F2 and typing the name of the app they want to run would be ... well ... ineffective, imo. Many people rarely run things any other way.

Yes, but not generally teenage girls, at least they didn't when I was a youth.

---

### Post by Lord Illidan on 2007-01-07
> **Biggus said:**
> Yes, but not generally teenage girls, at least they didn't when I was a youth.

Don't underestimate them, especially when google is just a step away..for all we know, she could be coming on the forums asking how to start amsn from the terminal..

How about using firestarter to block those ports used by IMing, and making sure that your daughter's account has no admin access?

---

### Post by robc02 on 2007-01-07
Thanks for you replies. I quite like the idea of changing the groups etc of the executable - that should do what I want. I hav elloked for files to do with amsn and have found several in /usr/share and some links in /usr/bin. Will changing the group of teh links in /usr/bin be the way to go? They are currently owned by root with root as teh group. If I create a group calle, say, amsnuser, and make myself the only member, should this do the trick?

---

### Post by kidders on 2007-01-08
I imagine that removing the world execute bit from the amsn executable is what to do. If you want to be able to run it yourself, change the group that owns it to something suitable.

If you really don't want her chatting though, you won't want to leave your daughter unattended for very log. As I mentioned before, there's nothing stopping her from downloading a second copy of aMSN (or any other chat app) ... and let's face it, it's not rocket science.

Incidentally, is it just the MSN network that concerns you? What about web-based Java chatrooms ... or the web-based version of MSN itself, for that matter? Without wanting to pry into your personal circumstances, it might be more straightforward to simply ask her not to go chatting. You could then take a snapshot of what your PC is doing every now and then while she's using it, just to make sure.

Perhaps something like ** if [ "`users | sed 's/.*username.*/username/'`" = "username" ]** would tell you when she's logged in, and  **ps aux > /tmp/snapshot_`date +"%y%m%d%H%M"`.log** would snapshot all running processes for you. Think of it as CIA-style enforcement versus KGB-style enforcement ... "bit brother is watching" can be a good deterrent.

---

### Post by robc02 on 2007-01-08
The chatting in itsef is not the problem. She chats with a group of friends who are on MSN, and she is quite open about it. Really I just want to stop her from hogging my computer when she has one of her own that is quite up to the job. She does not have administative privileges so won't be able to add or remove programs. Hopefully, just making it awkward for her will do the trick. (Having said that, my 12 year old son is more computer literate and could be harder to deter - but I'll worry about that if it happens).

---

### Post by cmost on 2007-01-08
Use the little known ACL (access control lists) feature that is compiled into your kernel already.  ACL's on Linux typically work with all the major filesystems including EXT3.  You will need to use synaptic to add the ACL editing tools to Gnome and you'll have to add the acl option to your /etc/fstab/ for each volume for which you want to use ACL's.  Once setup, you'll have the same fine grained control over files, folders, and executables that you have in Windows NT/2K/XP_pro.  You can specify on a per user basis, read/write/execute or no access.  This avoids many of the problems that occur with the classic user/group/other permission scheme.  Google will help you modify the fstab file (I can't post mine at the moment...on Windows at work.)  Don't worry, it's extremely easy.  Good luck!

---

### Post by robc02 on 2007-01-08
ACL sounds just the job. I have downloaded  and am looking into using it. 
Is it just for command line or is there a GUI? 
I also need to find out which file to change the ACL on. Where am I likely to find the startup file for amsn?

---

### Post by hikaricore on 2007-01-08
> **robc02 said:**
> ACL sounds just the job. I have downloaded  and am looking into using it. 
Is it just for command line or is there a GUI? 


Info:
[http://www.die.net/doc/linux/man/man1/eiciel.1.html](http://www.die.net/doc/linux/man/man1/eiciel.1.html)
[http://rofi.pinchito.com/eiciel/?s=2](http://rofi.pinchito.com/eiciel/?s=2)

Install:
```
sudo apt-get install eiciel
```

You may need to logout and back in for the tab to appear in nautilus.


> **robc02 said:**
> Where am I likely to find the startup file for amsn?

```
whereis amsn
```

Should show you the location of the binary and any symlinks.  :)

---

### Post by hikaricore on 2007-01-08
For some reason eiciel isn't loading in nautilus for me on edgy like it should be.  I can load the stand alone configuration tool from Applications/System Tools fine.  But in nautilus, I can see it's resizing the properties box, just not adding itself.  *boggle*

---

### Post by cmost on 2007-01-08
Have you updated your /etc/fstab to support acl's?

---

### Post by hikaricore on 2007-01-09
> **cmost said:**
> Have you updated your /etc/fstab to support acl's?

Updated it but never remounted the partitions >.< Thanks for reminding me.  Yesterday was a very long day.. lol

---

### Post by robc02 on 2007-01-10
Thanks for your help. I have installed acl and eiciel. There is no launch icon in any of the main menus but when I open a file in Nautilus there is a tab in the Properties box - so that will do.

---

