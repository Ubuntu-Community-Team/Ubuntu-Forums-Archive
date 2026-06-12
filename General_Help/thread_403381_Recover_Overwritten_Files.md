---
title: "Recover Overwritten Files?"
date: 2007-04-06
forum: General Help
---

### Post by mountaingsr on 2007-04-06
Hi All,

I searched around a bit but couldn't find an answer that really fit my special situation.

After a recent error in my WinXP install which caused a strange BSOD error on bootup, I decided to use an Ubuntu disk to try to save my files and try out Linux.  In the process of juggling two USB drives, one SATA drive, and one IDE drive (around 800GB of drives, all totalled) I overwrote the Windows partition with the Ubuntu installation (chose the option of auto-partition, etc.).

I've done something stupid like this in windows before, but I was able to use a Norton utility to view the deleted files and recover most of what I needed.  

I have been searching Synaptic, these forums and the web at large for an Ubuntu-friendly piece of software that will run in the Linux environment, but be able to view deleted files in the NTFS format and copy them to a USB drive (formatted any way you like).  So far I've found nothing. 

Of course, on top of all of that, I (correct me if I'm wrong here) believe I can't unmount the drive I need to operate on as I've successfully installed Ubuntu over top of it.

Should I delete the Linux install, attempt a Win reinstall, and hope that I'm able to recover some data?
Is there a piece of software I can use from Ubuntu that will allow me to achieve what I want?
Should I kiss the data good bye and start trying to exist in this new environment?

Any help is much appreciated.

PS Obviously I've abbreviated much of this story for brevity's sake.  If there are necessary details I've overlooked, please ask.

Thank you,
Ryan

---

### Post by dbbolton on 2007-04-07
i think you might be out of luck. file recovery utilities like midnight commander only work on ext2/3 filesystems. maybe you could take your computer to a data recovery lab.

---

### Post by Cappy on 2007-04-07
Any large files you had are probably lost. Basically, you've overwritten a lot of the parts of your files already. I recently did something VERY similar to this on accident last week (I accidently repartitioned my NTFS drive as EXT3). I was able to recover all my data by using Windows partition and using recovery utilities .. most don't work on deleted partitions even though they claim they do (I tried about 6 different programs that I selected and only 2 actually worked). Of all the ones I tried, I would recommend Restorer2000 (Windows only) and RecoverSoft (Boot disk,  OS independant). I ended up using Recoverer2000 because it recovered all of my filenames while Recoversoft didn't. Both of those have trials. 
If I were you, I would either hook up your hard drive to windows on another computer and use Restorer2000 or just use RecoverSoft. Reinstalling Windows on the same drive will probably cause you to lose even more.
On a side note, if you decide to use the trial RecoverSoft you can extract the trial exe and you will get an iso you can burn in linux =)

[http://www.recoversoft.com/data_rescue_pc_info.htm](http://www.recoversoft.com/data_rescue_pc_info.htm)
[http://www.restorer2000.com/](http://www.restorer2000.com/)

I might as well warn you, data recovery programs aren't free.

Lastly, you should stop using your Ubuntu partition! When you use your Ubuntu partition you start overwriting data that could be recovered!

---

### Post by mountaingsr on 2007-04-07
Thanks for the recommendations Cappy.  I'm downloading Restorer2000 right now, I'll report back when I have some time to work with it.

---

