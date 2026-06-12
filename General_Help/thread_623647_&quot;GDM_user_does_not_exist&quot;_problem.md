---
title: "&quot;GDM user does not exist&quot; problem"
date: 2007-11-26
forum: General Help
---

### Post by Gahmuret on 2007-11-26
Hi, all. I'm a complete Linux virgin, just trying to get an Ubuntu 7.10 installation running on an older laptop. Bear with me--I'm going to explain in detail what I was doing and the problem that arose. 

I managed to get Ubuntu installed with no problems, and started the Update Manager. It greyed out, and I just assumed it was doing its thing--after all, it needed 88 updates, so I figured it would take a while. I did a few other things, like copying some music onto the machine, and adding my wife as an administrator--which might be the root of the problem that was about to occur. I was ready to log off, but the Update Manager still hadn't finished (and we're talking a few hours this thing had been running), and indeed, it didn't seem to have done anything at all. So I went through the proper shutdown routine, and turned the laptop off. So far, so good. Then I tried to restart it, and after the Ubuntu splash screen went away, I got bunch of text and a non-graphical screen with the message, "The gdm user does not exist. please correct gdm configuration and restart."

Well, I finally got to a normal logon after following some of the advice in [this thread.]("http://ubuntuforums.org/showthread.php?t=535096&highlight=user+gdm+does") I also tried [this]("http://ubuntuforums.org/showthread.php?t=267503"), but that did nothing other than tell me that my username "is not in the sudoers file." 

Anyway, now I have a normal desktop--even shows my name at the top of the screen. Problem is, a lot of stuff that requires authentication doesn't work now. Under System>Administration, I have only: Keyring manager, Network Tools, Printing, System Log, System Monitor, and Update Manager. Maybe I'm going senile, but I thought there was a bunch of options there before.  I wanted to just remove my wife's login, figuring that it might somehow have corrupted something, but I don't even have the option anymore. No way to create a new user, either. When I clicked on my name to use the User Switcher, it didn't even show my wife's username. I tried to run the Update Manager, but it told me I didn't have permission--and I'm an administrator! I tried to switch users by going through the logoff routine, and again, it didn't recognize my wife's login info. 

Something with the passwords/authentication is screwy. Can anyone help me? And please remember, I know next to nothing about using Linux! I'm a complete noob, so be as simple as you can be.

---

### Post by geirha on 2007-11-26
Seems some configuration of certain packages hasn't completed. It will probably be fixed by hitting CTRL+ALT+F1 and log in to that console, then run ```
sudo dpkg-reconfigure -a
``` this will reconfigure all installed packages, which will take some time (some hours probably), and it may ask some questions along the way. 

I've encountered similar problems myself, where some packages somehow got "badly" configured. Running dpkg-reconfigure -a fixed it all.

---

### Post by Gahmuret on 2007-11-26
> **geirha said:**
> Seems some configuration of certain packages hasn't completed. It will probably be fixed by hitting CTRL+ALT+F1 and log in to that console, then run ```
sudo dpkg-reconfigure -a
``` this will reconfigure all installed packages, which will take some time (some hours probably), and it may ask some questions along the way. 

I've encountered similar problems myself, where some packages somehow got "badly" configured. Running dpkg-reconfigure -a fixed it all.

Thanks for the response, but it didn't work. 

When I logged in I got this prompt: Ryan@laptop:~$

I entered sudo dpkg-reconfigure -a

It asked for my password, and I typed that in, then it went straight to the prompt again without doing anything.

---

### Post by Gahmuret on 2007-11-26
Thought I'd add some info. When I try to use the Update Manager to install updates, it gives me the following error in a new window:

> Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '29360131' '--update-at-startup' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator. 

But I AM the administrator! It still doesn't recognize the username/password I set up for my wife, and I didn't do anything to my own user profile. I've also rebooted a few times now, and it seems to boot up normally (not sure of this, since I'm a new user), but still won't recognize me as administrator. 

I'm very close to just reinstalling at this point. It would probably take less time since this is a new installation anyway.

---

