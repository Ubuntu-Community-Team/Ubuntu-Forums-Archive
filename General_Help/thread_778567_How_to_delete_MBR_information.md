---
title: "How to delete MBR information"
date: 2008-05-02
forum: General Help
---

### Post by sn0m on 2008-05-02
Hi there
I'm a newbe and have run into problems with MBR.
I have 3 hard drives in my desktop, 2 IDE, one as a master and one as a slave and 1 SATA which i use as my main hard drive to install the operating systems.
I have ubuntu and win xp on my SATA and use the other two as storage for pictures and movies.
However during a botched installation attempt, for some reason I have GRUB corrupt/partially set up in the primary MBR of my primary IDE drive, and would not let me boot either ubuntu or xp, saying files missing or something. Therefore i had to physically disconnect the IDE drives to get my system going again.
How do I delete the MBR information form my primary IDE drive...? thats the question.
Thanks for your help in advance
Koli

---

### Post by rupali_4 on 2008-05-02
You can do everything you want to do in a day on [www.baajaa.com](www.baajaa.com). You can look at job openings, find a date, rent an apartment, sell your bike and buy used items. And if you are interested in showbiz you can post your profile along with pics and your video as well. Also Balaji Telefilms is conducting auditions on [www.baajaa.com](www.baajaa.com) . All this and lots more on [www.baajaa.com](www.baajaa.com) !

One of the new features added on [www.baajaa.com](www.baajaa.com) is Yellow Pages. You can create a simple listing of your business for free. But what is really interesting is that you can Create Your Own Website (with your Logo, 5 pics, Company Profile, List of Products & Services, Video) and you get a Free Premium Yellow Page listing. For just Rs.3999/- !
 
Thanks

---

### Post by jocko on 2008-05-02
I don't know how to delete mbr information, but one thing you could try is to set your bios boot order to not boot from the ide.

---

### Post by Herman on 2008-05-02
:) Hello sn0m,
I agree with jocko.
Your computer will try to boot from whichever hard disk you have set in your BIOS as your first hard disk.
If the MBR in your first hard disk has GRUB installed in it, then everything should be fine.
If not, you might need to [URL="http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD"]install GRUB in it.

[/URL]Regards, Herman :)

---

