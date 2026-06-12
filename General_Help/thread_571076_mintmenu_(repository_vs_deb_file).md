---
title: "mintmenu (repository vs deb file)"
date: 2007-10-08
forum: General Help
---

### Post by bone2006 on 2007-10-08
I've tried a few thing out there and nothing seems to impress me as much as mintmenu.    I'm not sure though if I'm better off adding their repository to my system or downloading the individual deb file(s) and installing only the mintmenu

[http://www.linuxmint.com/repository/](http://www.linuxmint.com/repository/)

I guess my concern is if there's repeated software in both repositories.  For instance both applications are in both repositories and the one in linux mint was newer, wouldn't it take the newer version?

Or if I just added deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) bianca/ to my list can I be certain that it would only effect the mintmenu?

thanks in advance

---

### Post by SuperDuck on 2007-10-08
Why don't you just run Mint? ;)

---

### Post by FuturePilot on 2007-10-08
> **bone2006 said:**
> I've tried a few thing out there and nothing seems to impress me as much as mintmenu.    I'm not sure though if I'm better off adding their repository to my system or downloading the individual deb file(s) and installing only the mintmenu

[http://www.linuxmint.com/repository/](http://www.linuxmint.com/repository/)

I guess my concern is if there's repeated software in both repositories.  For instance both applications are in both repositories and the one in linux mint was newer, wouldn't it take the newer version?

Or if I just added deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) bianca/ to my list can I be certain that it would only effect the mintmenu?

thanks in advance

I'd be careful in doing that. It might want to install and/or upgrade other things. From what I know (I've tried installing the deb file manually) Mintmenu depends on a whole ton of stuff that is specific to Linux Mint.

---

### Post by ryanVickers on 2007-10-08
That is nice, but it looks like a real memory hog!  I installed the slab menu from SLED 10 (in ubuntu) and when the applet in on the panel, it's about 30MB! :(

---

### Post by bone2006 on 2007-10-09
> **SuperDuck said:**
> Why don't you just run Mint? ;)

There were too many bugs on my machine and other machines.  Seems like somethings they did increased bugs.  

I found out that on each of my machines if I want certain applications/codecd installed I can just create a text file name it backup.text put each thing I want installed on each line, then run:
cat backup.txt | xargs sudo apt-get -y install

This will get me all the software/codecs that I want and it's tailored to my needs.  Change the background and change the menu and I have a better version of linux mint.  I have all the benefits of linux mint plus the applications I use.

I like SLED menu a lot, but I think mintmenu is an improvement.  Would love to see it in the repository, for the time being I'll just continue to use SLED and hopefully SLED will improve as well.

---

### Post by ryanVickers on 2007-10-09
sorry, I hould have said "... from SLED 10 (in ubuntu) ..." ;)

---

### Post by bone2006 on 2007-10-13
I just tried it out on my 64bit ubuntu and it's using 7.3mb not 30mb for me.  Much better than 30, but 7mb still seems kind of high honestly.

---

### Post by mpgarate on 2007-10-13
has anyone tried the gnome suse menu? I really like that one... any idea if its possible to install for ubuntu?

---

### Post by bone2006 on 2007-10-13
Is that gnome-main-menu ?  Here's what it looks like, thought even the description tells you that it's from suse.  Thought the two were the same and that mintmenu was the one that' different.

[IMG]http://reverendted.files.wordpress.com/2006/06/screenshot-gnome-main-menu-favorite-apps.png[/IMG]

---

### Post by bone2006 on 2007-10-14
After weeks of using this menu I'm ready to uinstall it.   When my system has been up for days it's really slow at responding.
Any thing else out there that's similar?

---

### Post by Malac on 2008-04-17
Try the original that mintMenu is taken from. Forum is here :
[http://ubuntuforums.org/forumdisplay.php?f=156](http://ubuntuforums.org/forumdisplay.php?f=156)

There is an SVN version with instructions on installing here :
[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)

Hope this helps

---

