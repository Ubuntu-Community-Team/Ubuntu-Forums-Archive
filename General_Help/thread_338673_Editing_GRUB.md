---
title: "Editing GRUB"
date: 2007-01-14
forum: General Help
---

### Post by gerowen on 2007-01-14
I've been dual booting Windows and Linux for a long time, but now comes a major turning point in my life.  All of the games I used to keep Windows around for run in Wine now, and I no longer have a need for Windows on my 80 GB hard drive.  I do not have a grub editor installed and I have a couple of questions.

1) What is a good, graphical grub editor that I can use to edit my bootloader?

2) Would installing Grub 2 hurt my current default installation of Grub 1.5?

3) Can I use Grub splash images with Grub 1.5, or do I need to upgrade to Grub 2?

---

### Post by tonyr1988 on 2007-02-12
I know this thread is kind of old, but I found it searching for something else, so I thought I'd give a little bit of help:

1) I'm not aware of a graphical grub editor. However, it's pretty easy to edit without a graphical tool. However...

2-3) Why do you still need GRUB after killing Windows? GRUB simply lets you choose which OS to boot. If you only have Ubuntu, you can just tell it not to show up at all and boot straight into Ubuntu. That's what I do. :) [and I think splash images are only Grub 2 and you shouldn't have problems upgrading, but I'm not positive]

Also, removing Windows from GRUB will not remove your Windows partition. For that, you'll need a partitioner, such as GParted:

> sudo apt-get install gparted

System -> Administration -> GNOME Partition Editor

It will be the same partitioner you used when you installed Ubuntu (remember that far back? :P). It'll allow you to do things like remove your Windows NTFS partition and expand you Ubuntu one to be larger.

(Anytime you do any partitioning, make sure to backup important data, just in case).

If you don't want / need GRUB to show up, then:

> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

A few lines down you'll see:

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

Change that to:

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

---

