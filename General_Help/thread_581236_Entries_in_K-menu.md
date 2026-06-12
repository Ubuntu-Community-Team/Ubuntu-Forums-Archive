---
title: "Entries in K-menu"
date: 2007-10-19
forum: General Help
---

### Post by Bosonator on 2007-10-19
Hi,

I just installed Gutsy Kubuntu on my laptop, and I see that the entries for programs in the K-menu aren't just the name of the program, but something like "_: Entries in K-menu: digiKam app-name Photo Management ...". Everything works fine, but it's kind of sloppy, so does anyone know how to fix that so that only the program name is displayed? 

Thanks!

---

### Post by davidjmayo on 2007-10-19
Hope this what you want to do
You want digiKam to say just that not digikam-photo management??

If I'm correct then all you need to do is:
right click on the bottom bar and unlock panels

right click k-menu and choose menu editor

I don't know an automated way so this has to be done one by one
go through the k-menu and for each you want to change click on it and then remove the comment and/or description. The k-menu will change to what you will see.

when finished do file save or just close with the red x which will prompt you to save changes,

now lock the panels again with a right click on the bottom bar

I haven't checked this but I think from before this is a per user setting so if you have other accounts you may have to do it again or find where it is (somewhere in /home/username/.kde probably-- where .kde is a hidden file)

---

### Post by bitterbug on 2007-10-22
I'm seeing the same thing. 
Almost all entries in the menu are prefixed that way. Only a few are not.
I wonder if this is a legacy of using the home folder I was using for 7.04.

The OS is a fresh install, but I just left my home folder partition intact to save on the pain of copying the whole drive back.

---

### Post by Bosonator on 2007-10-22
that could be.... I can't seem to change anything. I might try deleting and recreating the problem entries.

---

### Post by jlacroix on 2007-10-22
On a somewhat related note, when I change the kmenu naming format to "Name Only" in kcontrol, it's a MAJOR pain in my #$#& to manually go through an alphabetize them by name. Is there an easier way?

---

### Post by bitterbug on 2007-10-22
Interesting. Switching from Name/Description to Name Only fixes it... as long as you don't need descriptions :)
Seems to be some sort of parsing error.

---

### Post by toppy on 2007-10-22
I've got the same problem.

I just downloaded and installed Kubuntu 7.10 last night.  Totally fresh install with no old home directory.

As bitterbug says, looks like a parsing error.  The "_: Entries in K-menu: TITLE app name, " string does not show up in the menu editor so the parsing problem is only in the menu display.

---

### Post by redz1234 on 2007-10-23
I installed Kubuntu for the first time ever on this machine last night and the issue is happening over here aswell. I also changed it to "Name Only" and everything is working now.

- ReDz

---

### Post by glupee on 2007-10-23
I was having the same problem. Changed the kde menu to name only, but i've started to notice the same problem on certain buttons and file menu's.  I don't remember all instances (currently at work), but i do remember that when i send something to the trash bin, the ok or send to trash button has the same parse problem. it's also in some drop down menus.

---

### Post by benmoreassynt on 2007-10-24
This definitely seems like a bug. I've come across a few bugs in Gutsy - the first time I've ever found some really irritating ones.

---

### Post by davidjmayo on 2007-10-25
there appears to be a fix but I don't have this problem so can't confirm this
see  [http://kubuntuforums.net/forums/index.php?topic=3087586.0](http://kubuntuforums.net/forums/index.php?topic=3087586.0)

---

### Post by glupee on 2007-10-25
> **davidjmayo said:**
> there appears to be a fix but I don't have this problem so can't confirm this
see  [http://kubuntuforums.net/forums/index.php?topic=3087586.0](http://kubuntuforums.net/forums/index.php?topic=3087586.0)
As i posted in that thread as well :D
this fix worked for me!:KS

---

