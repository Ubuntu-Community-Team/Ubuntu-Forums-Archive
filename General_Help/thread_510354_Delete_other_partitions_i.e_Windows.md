---
title: "Delete other partitions??? i.e Windows"
date: 2007-07-26
forum: General Help
---

### Post by nick.inspiron6400 on 2007-07-26
Hi,

I have had Kubuntu,Ubuntu, and Windows XP for a very long time now. But I have now decided it is time to let go, and give up with Windows.

I would like to delete the Kubuntu and Windows partition, I have installed a program called Gparted. But I can't delete any partitions, as there is a padlock beside them???

Please could someone reply with clear, simple instructions to delete everything but the Ubuntu partition, not forgetting extending it!

Thank you,

Nick.

---

### Post by hessiess on 2007-07-26
boot the live cd and use gparted on there, works perfet. cannot geve anything more spasific.

you did not need to install kbuntu, just install kde on ubuntu

---

### Post by stchman on 2007-07-26
> **nick.inspiron6400 said:**
> Hi,

I have had Kubuntu,Ubuntu, and Windows XP for a very long time now. But I have now decided it is time to let go, and give up with Windows.

I would like to delete the Kubuntu and Windows partition, I have installed a program called Gparted. But I can't delete any partitions, as there is a padlock beside them???

Please could someone reply with clear, simple instructions to delete everything but the Ubuntu partition, not forgetting extending it!

Thank you,

Nick.

So you are saying that you have Ubuntu and Kubuntu installed separately?  Most people install either Ubuntu or Kubuntu and then apt-get the other.

Boot up the LiveCD and bring up Gnome Partition Editor.  Once that is done then select the you will select the Windows XP partition and hit delete.  I would then format it to your favorite file system.  Make sure you hit apply when you are done.

You will also have to edit you /boot/grub/menu.lst to remove the reference to Window XP.

Do the same with the Kubuntu partition, then edit the menu.lst.

---

### Post by nick.inspiron6400 on 2007-07-26
Thanks guys!

Also can i extend my Ubuntu partition so I can make use of my 60B HD?

Thank you.

Nick.

---

### Post by hessiess on 2007-07-26
just make a new partition with /home, then resertch moving home to a pertition. it can make your stuff easer to orgonise...

---

### Post by nick.inspiron6400 on 2007-07-26
How to hell do i do that?????

---

### Post by hessiess on 2007-07-26
sertch the form

or you could resise your ext3 partition, back up everything furst though:) 

its not that hard to work it out yourself

---

### Post by manndani on 2007-07-26
Instructions Here. [http://gparted.sourceforge.net/larry/livecd/livecd.htm](http://gparted.sourceforge.net/larry/livecd/livecd.htm)

---

### Post by nick.inspiron6400 on 2007-07-27
Thank you guys, but hessiess i am not a Linux expert! 

I really dislike those comments that you can work it out yourself, I just switched from Windows!!! And I have been using Windows since 1995.

I will try and resize my partition, I never do back-ups. I have nothing that I want to keep. 

Nick.

---

### Post by hessiess on 2007-07-27
sorry, i can be abit vage, im quite new to linux al well;)  installed it the same day i joined this form. 
been using windows for about 5 years, got bord with it:lolflag:

partitioning isent that dificult, if you have nothing you want to ceep, reinstall ubuntu with the use whole disk option.

---

