---
title: "Ubuntu 21.04. Newbie here. Please confirm correctness before I do a Timeshift system"
date: 2021-08-11
forum: General Help
---

### Post by Advait on 2021-08-11
[COLOR=#000000][FONT=Arial]Newbie here. See pics. ( [COLOR=#000000][FONT=Arial][https://imgur.com/a/kc9DOay](https://imgur.com/a/kc9DOay) )[/FONT][/COLOR]  Some of my apps got messed up and I want to do a Timeshift system restore to yesterday (Aug 10th). Please look at the pics and see if I&#8217;m all set to do a restore. Will this restore take my apps back to yesterday? I want to make sure cuz I know a bad restore can trash my whole system. Thanks.
[/FONT][/COLOR]

---

### Post by TheFu on 2021-08-11
If you need a backup for your backup ... ouch.

---

### Post by mIk3_08 on 2021-08-11
Don't worry about the apps you can have it back when your system is restored properly But if don't; you can installed it back
they are always available in the cloud so no problem. Apps on Linux most of them are open source and its free as in free to be use. 
Be worry about your important files because if you loose them you can't have it back again, you will be going back to zero. 
And that is  very hard. Good Luck and Regards

---

### Post by Advait on 2021-08-11
> **mIk3_08 said:**
> Don't worry about the apps you can have it back when your system is restored properly But if don't; you can installed it back
they are always available in the cloud so no problem. Apps on Linux most of them are open source and its free as in free to be use. 
Be worry about your important files because if you loose them you can't have it back again, you will be going back to zero. 
And that is  very hard. Good Luck and Regards

Problem is 3 of my apps are not working, and when i reinstall them they also don't work. Is there some way to fully remove an app? Thanks.

---

### Post by mIk3_08 on 2021-08-11
These are some of the command to properly remove the package installed.
```
sudo apt purge <packagename>

```
```
sudo apt remove --purge <packagename>

```
```
sudo apt-get autoremove && sudo apt-get autoclean

```
or there command;
```
sudo apt autoremove && sudo apt autoclean
```

---

### Post by TheFu on 2021-08-11
Packages typically have configuration and data in 2 places.  

```
sudo apt purge {package-name}
```
will remove the program and system configuration files completely.
It will not remove the data or personal configuration files. Those would need to be manually removed.

Personal configuration files are in the userid's HOME directory, somewhere.  There are typical places for those, but applications don't have to follow those rules of thumb.  Typically, look in ~/.config/ .... somewhere.

The easy way to see if the issue is a personal configuration problem is to create a new userid, logout and login using that new userid. Run the program. If it works now, but not before, then it is a personal configuration problem.  If it doesn't work under the new userid, it is likely a system configuration or application problem.

Snap packages do things a little different, so if the package is a snap, mention that and some other people who allow those abominations on their systems can answer. I'm not a fan of snap packages. ;)

---

### Post by GhX6GZMB on 2021-08-11
> **Advait said:**
> [COLOR=#000000][FONT=Arial]Newbie here. See pics. ( [COLOR=#000000][FONT=Arial][https://imgur.com/a/kc9DOay](https://imgur.com/a/kc9DOay) )[/FONT][/COLOR]  Some of my apps got messed up and I want to do a Timeshift system restore to yesterday (Aug 10th). Please look at the pics and see if I’m all set to do a restore. Will this restore take my apps back to yesterday? I want to make sure cuz I know a bad restore can trash my whole system. Thanks.
[/FONT][/COLOR]

You can only restore what has been backed up, but that's too late now.

With Timeshift it is best to tick the "Include Only Hidden Files" for the users in /home (/root doesn't matter), both for backup and restore.
That will bring your system back to its last state.

But all's not lost. You may lose some personalized settings when doing the restore, but everything else will be fine.

---

### Post by monkeybrain20122 on 2021-08-11
What apps are those? Probably resetting them by deleting their config files will help (typically in ~/.config or in your home in the form of .foo, foo being the app, the "." means hidden, show them by ctrl+h)

---

### Post by Advait on 2021-08-12
Issue Resolved.

I got it working. I took a deep breath and did my first Timeshift system restore and it worked! Flameshot and KDEConnect started working again, but my VLC snap was not working. I then removed the VLC snap and installed the VLC flatpak and that now is working normally. So I'm back to normal.

Thank goodness for Timeshift! Now I'll be doing system snapshots a lot more often (and properly commenting them).

---

### Post by mIk3_08 on 2021-08-12
> **Advait said:**
> Issue Resolved.
I got it working. I took a deep breath and did my first Timeshift system restore and it worked! Flameshot and KDEConnect started working again, but my VLC snap was not working. I then removed the VLC snap and installed the VLC flatpak and that now is working normally. So I'm back to normal.
Thank goodness for Timeshift! Now I'll be doing system snapshots a lot more often (and properly commenting them).
Wow! Congratulation. Good Luck and regards. Enjoy using Linux Ubuntu Operating System
> **TheFu said:**
> Packages typically have configuration and data in 2 places.  
```
sudo apt purge {package-name}
```
will remove the program and system configuration files completely.
It will not remove the data or personal configuration files. Those would need to be manually removed.
Personal configuration files are in the userid's HOME directory,  somewhere.  There are typical places for those, but applications don't  have to follow those rules of thumb.  Typically, look in ~/.config/ ....  somewhere.
The easy way to see if the issue is a personal configuration problem is  to create a new userid, logout and login using that new userid. Run the  program. If it works now, but not before, then it is a personal  configuration problem.  If it doesn't work under the new userid, it is  likely a system configuration or application problem.
Snap packages do things a little different, so if the package is a snap,  mention that and some other people who allow those abominations on  their systems can answer. I'm not a fan of snap packages. :wink:
Thanks a lot TheFu and monkeybrain20122[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=1843403") for the assistance when I wasn't there to reply to make solve the issue asap.

---

### Post by Advait on 2021-08-12
mlk308 "Enjoy using Linux Ubuntu Operating System"  

Thanks. As an Ubuntu newbie I'm totally amazed at how much effort I had to put in to get it working for my needs. Every step of the way I had to spend hours wrestling with some arcane technical issue. What a slog! ](*,)   

I totally LOVE the open source community and ideals (which is why I'll stick with Ubuntu), but I really really miss the user friendliness of Windows.

---

### Post by TheFu on 2021-08-12
If you only point-n-click, you'll miss 80% of the power that Unix provides.

BTW, how long did it take for you to learn Windows?  Years, no doubt.  Expecting Linux to be any different isn't fair, especially if you are surrounded by Windows people and don't see Unix/Linux used by experts.  The way I use Linux is completely different from the way that I'm allowed to use Windows.

I can assure you that for someone moving from Linux/Unix to Windows, the transition AND frustrations are equal. Heck, after 3 weeks on a Mac, I was ready to through the system against the wall over frustration for all the things it wouldn't let me do.  So much power, just locked away and not allowing it out.

---

### Post by rbmorse on 2021-08-12
Jerry Pournelle used to say that doing things on the Mac was either impossibly simply or simply impossible.

---

### Post by TheFu on 2021-08-12
> **Advait said:**
>  

Thanks. As an Ubuntu newbie I'm totally amazed at how much effort I had to put in to get it working for my needs. Every step of the way I had to spend hours wrestling with some arcane technical issue. What a slog! ](*,)   

Someone else in these forums has a tagline that says, "if it isn't easy, then you are probably doing it wrong."
Linux likes consistency. If you are consistent in how you do the same thing, many self-inflicted problems can be avoided.  For example, I don't use GUI tools to install or remove software.  I know there is just 1 command I need to know with a few options to  add, remove, purge software and keep the installed software cache on the system unclogged.

If I used any GUI, I'd forever wonder what it actually did or didn't do. Millions of people only use the GUI, so I suppose that is fine as well - or perhaps they have 2TB OS partitions and it doesn't matter how full of cruft that partition gets?

Because I have many systems and consider backups mandatory, I'm cautious about leaving cruft on systems. I'd rather not have 3+ copies of junk that isn't needed.

But we are all different and choose how to spend our time.  End-users just want a system that works and doesn't need much maintenance.  [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) has been updated over the years with newer commands, but it is still basically what I do to maintain Ubuntu desktops.

---

