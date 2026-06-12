---
title: "rar files"
date: 2007-11-24
forum: General Help
---

### Post by thinsoldier on 2007-11-24
## What a sucky user experience ##

right click a .rar file and "open with archive manager"...got an error message.

The average joe is not going to think to open a CLI and type sudo apt get anything.
Unrar should be installed by default.

Add/Remove programs should have Unrar listed in there but it doesn't!

The only thing that comes up when you search for 'rar' is 7zip.

I installed 7zip.

7zip doesn't show up in any of my menus.

alt+f2 and type 7zip....nothing

open a CLI and type 7zip ... nothing

Restart

Repeat previous steps, still no 7zip to be found anywhere.

Go to add/remove again and search for 'rar' again.
NOW 'RAR' program shows up in the list.

I search my menus again. I don't see a Rar program anywhere!

I try right clicking on the .rar file again and chose "open with archive manager"
it works now.

...this sucks.

---

### Post by thinsoldier on 2007-11-24
...and while I'm in a ranting mood....

Gnome needs an easy to find "Force Quit" menu item in the main application menu like OS X has.


Sometimes when I right click a file and choose "open with other application" it gives me a nice list of already installed applications (7zip and RAR ARE NOT LISTED HERE even though I JUST INSTALLED THEM!!!!)
But other times it just gives me an Open File dialog window....
I have no friggin clue where these things get installed to! I don't know what the linux equivalent to P:/Program Files is (yes I have that many drives)
And this worries me. I have no idea what I'm supposed to do when my tiny ubuntu drive runs out of space and I want to install more stuff.

In OS X I can put a .app anywhere and just use it. In windows I can choose any location I want to install a file. All games installed to G:\ and all useful programs installed to P:\
What's the linux equivalent to this kind of flexibility without having to edit a handful of text files and praying it works and hours of trial and error?

---

### Post by zvacet on 2007-11-24
Rar,unrar,p7zip are CLI programs.Good thing is that you don´t have to use CLI to run that programs.If you have some rar file just right click on it and select **unpack here**.That&#729;s all.

---

### Post by mali2297 on 2007-11-24
Welcome to the community. :-)

I think you should have a look in the package manager [Synaptic]("https://help.ubuntu.com/community/SynapticHowto").
There you can search for **unrar** and install it. The archive manager will be able to extract rar files thereafter.

EDIT:
I didn't read your post carefully enough. You managed to extract the rar files after all, then what is the problem?
You want a separate application just for rar?

---

### Post by geirha on 2007-11-24
> **mali2297 said:**
> Welcome to the community. :-)

I think you should have a look in the package manager [Synaptic]("https://help.ubuntu.com/community/SynapticHowto").
There you can search for **unrar** and install it. The archive manager will be able to extract rar files thereafter.

EDIT:
I didn't read your post carefully enough. You managed to extract the rar files after all, then what is the problem?
You want a separate application just for rar?

The point he is trying to make is that; if a user comes along and wants to unrar a rar-archive, the user will get a cryptic message telling him/her that it didn't work. How would the user know that he/she must install the unrar package?

And that is obviously something that should be improved. The archive manager should guide you through the install of unrar, like totem does with the codecs now, imo. But this thread should be moved to the idea forum though, or possibly be filed on launchpad I guess.

---

### Post by rune0077 on 2007-11-24
Erh, but, mm, that's just not true. I am pretty sure I have never installed any software to unzip RAR files, and I'm also pretty sure I have been able to do this anyway. I think Ubuntu is quite able to this without needing to install anything. Then again, I could be wrong (wouldn't be the first time).

---

### Post by rsambuca on 2007-11-24
> **rune0077 said:**
> Erh, but, mm, that's just not true. I am pretty sure I have never installed any software to unzip RAR files, and I'm also pretty sure I have been able to do this anyway. I think Ubuntu is quite able to this without needing to install anything. Then again, I could be wrong (wouldn't be the first time).

You are wrong.  :)

Ubuntu can not do this without the unrar package.  Perhaps you installed the ubuntu-restricted-extras meta-package?

---

### Post by sirdilznik on 2007-11-24
I could be wrong, but I believe rar is NOT free software (free as in speech) and the licensing conflicts with the GPL thus legally Ubuntu cannot include unrar.  I think there may be a different version of rar that is free, but provides limited functionality.  Someone correct me if I'm wrong, but I believe Ubuntu's hands are tied on this one since it is a legal issue.

---

### Post by rune0077 on 2007-11-24
> **rsambuca said:**
> You are wrong.  :)

Ubuntu can not do this without the unrar package.  Perhaps you installed the ubuntu-restricted-extras meta-package?

Oops! Yeah, i probably did :oops: Sorry, please ignore previous post.

---

### Post by rsambuca on 2007-11-24
> **rune0077 said:**
> Oops! Yeah, i probably did :oops: Sorry, please ignore previous post.

No worries!  I think I might have been wrong once before.   ;)

---

### Post by steeder on 2007-12-09
I am also having a problem with tar.gz and trying to UnZIP/Rar etc. I loaded 7ZIP and RAR with Synaptic. I am using Mythbuntu and it does not have all the standard menus as Ubuntu. So when you  rt. click on it there is knothing in the menu about UnZipping or RAR.

Is there a way to add menus?:)

---

### Post by mali2297 on 2007-12-10
> **steeder said:**
> I am also having a problem with tar.gz and trying to UnZIP/Rar etc. I loaded 7ZIP and RAR with Synaptic. I am using Mythbuntu and it does not have all the standard menus as Ubuntu. So when you  rt. click on it there is knothing in the menu about UnZipping or RAR.

Is there a way to add menus?:)

As I understand, Mythbuntu uses the Xfce desktop by default and Thunar as file manager. If so, install the packages **xarchiver** and **thunar-archive-plugin**. Then you can create and extract archive files using the file context menus of the file manager.

Alternatively, you can install **ubuntu-desktop** to get the Gnome desktop environment that comes with the standard Ubuntu distribution.

---

### Post by jwkungfu on 2008-01-19
Hi there, i did what you told the other post... but no luck. Archive manager still won't open my .rar file....??
jw.

---

### Post by Imamoomoocow on 2008-01-20
This ENTIRE thread is a waste of time. It's not a Linux related problem that needs to be solved, it's annother MACFAN deciding that he/she should use linux. I support everyone new to linux, the problem comes when they expect everything to be the same as OS 10 or Windows VIsta. It's NOT. Ubuntu doesn't try to be like anything besides the world's greatest OS (and it totally is). So why do people want it to be like the failure of a OS that OS 10 is.

---

### Post by mali2297 on 2008-01-20
> **jwkungfu said:**
> Hi there, i did what you told the other post... but no luck. Archive manager still won't open my .rar file....??
jw.

Hello. :-)

Which *other* post do you refer to? Try this first:
> 
I think you should have a look in the package manager Synaptic.
There you can search for unrar and install it. The archive manager will be able to extract rar files thereafter.

If you have already done that, try extracting the file from the terminal, If your file, let's call it *foo.rar*, is located on the desktop, type
```

cd Desktop
unrar e foo.rar

```
This is for troubleshooting. Do you get any error messages? Please post them?

Also, have you tried different rar archives?

---

### Post by A$h X on 2008-02-16
Just to confirm, after installing unrar, I then use File Roller to open rar archives? I thought unrar had it's own gui to open the rars. I ask because file roller takes extremely long to open a rar file compared to winrar for windows. Is there any way of speeding it up, apart from using terminal to extract files?

---

### Post by geirha on 2008-02-16
> **A$h X said:**
> Just to confirm, after installing unrar, I then use File Roller to open rar archives? I thought unrar had it's own gui to open the rars. I ask because file roller takes extremely long to open a rar file compared to winrar for windows. Is there any way of speeding it up, apart from using terminal to extract files?

unrar does not have a GUI, no. You could try [Q7Z](http://www.kde-apps.org/content/show.php?content=45453&forumpage=0) which is a GUI for p7zip, which in turn is a port of 7-zip. There's no Q7Z in the ubuntu repositories (yet?), but there's a deb-package at the Q7Z-site which can be installed on gutsy at least. You'll also need to install p7zip-rar from the multiverse-repository in order to be able to extract rar-files.

Haven't really tested it myself, other than installing it on my gutsy-box, so I don't know if it's any faster or not.

---

### Post by rsambuca on 2008-02-16
You should be able to just double-click on a rar file and it will automatically just unpack everything for you.

---

### Post by mali2297 on 2008-02-17
> **A$h X said:**
> Just to confirm, after installing unrar, I then use File Roller to open rar archives? I thought unrar had it's own gui to open the rars. I ask because file roller takes extremely long to open a rar file compared to winrar for windows. Is there any way of speeding it up, apart from using terminal to extract files?

**Xarchiver** is an alternative to Fileroller that also acts as a GUI frontend to unrar. It's in the repositories.

Another alternative that you can try is [PeaZip]("http://peazip.sourceforge.net/").

---

