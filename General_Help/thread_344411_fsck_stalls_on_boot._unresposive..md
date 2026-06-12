---
title: "fsck stalls on boot. unresposive."
date: 2007-01-22
forum: General Help
---

### Post by redbluemangle on 2007-01-22
When I boot up Ubuntu fsck halts the Ubuntu boot screen and goes to a text only thing where it checks my root file system [ok] and then proceeds to check the others ones and it just says "checking..." but doesn't do anything after that and just halts. I can run windows and access all my partitions from windows but Ubuntu will not boot. Any ideas?

---

### Post by hangman_jdf on 2007-02-17
I have the same problem.  If it matters, I am using ReiserFS.  This problem happens about every 1-2 months and last for about one day.  Then every thing goes back to normal.  During a normal boot, it goes from the boot screen to a text screen.  But it runs through the fsck in 2 or so seconds.  Any ideas?

---

### Post by jon_liverpool on 2007-03-03
I've had this problem too. I have both ext3 an reiserfs.

I had two partitions with Ubuntu on. After I installed the second installation, booting into the first one gave me a similar error. Basically, the  fstab file on the first installation was out-dated because the UUID of the second partition had changed. I fixed it by changing the UUID in fstab (which is just a bunch of random numbers) to a readable device in /dev/. For example /dev/sda2. It worked seamlessly afterwards. Just make sure that if you change it, you get the right device otherwise fsck may give you similar errors. check out UUID on wikipedia to find out more about UUIDs.

I'm not sure if this is the same problem that you're having as it will only occur if you're changing partitions on your hard disk in some way.

---

### Post by pizpot on 2007-03-03
Me three. I just put ubuntu 6.10 dual booting with windows and now this morning it won't boot to linux but windows is happy. I'm not going to reinstall linux for this I hope!!!

---

### Post by pizpot on 2007-03-03
OK, I got it to go finally. I tried to use the 6.10 cd, but unless you can mount your drives it won't help. I ended up just booting to ubuntu's recovery mode. It also wanted to fsck my drives and was stuck, but I read that ctrl+alt+ other keys would work. I tried F1 to F7 and ESC and BackSpace and lots of ctrl+C's and ctrl+D's and eventually I got to a root prompt. (sheesh)

From the root prompt, I did this:

cd /etc
cp fstab fstab.backup
vi fstab

Ok, then the screen turned into an editor. hehe good luck using vi. I had to up arrow up to the drive that was the problem (hdb1 in my case) and change the 0 1 at the end of its line to 0 0.

For example, you use the arrow keys to get the the right "1" that you want to make "0". So get the cursor over it, and hit "r". That puts you in "replace 1 character mode". So you hit "0" and it is done. To recap, cursor to the 1, hit "r" and then "0" and then  you must save and exit. Haha, good luck. No really, just type ":wq!" without the quotes.

Be careful with vi. If you do anything funny, it could wreck the file, and you have to restore it with commands like 

rm fstab
cp fstab.backup fstab

Speaking of vi, if you want to quit without saving because you goofed up hit ":q!".
(if there is a better terminal mode editor for newbies, post that here eh)

Then you can boot into linux. 

Then you can open up a terminal prompt and type "sudo fsck -r /dev/hdb1" (in my case) and I also did my other windows partitions (dont do your current linux partition--heed the warning) and now I don't get screenfulls of text when I boot linux as a bonus. 

Take care!

Oh yeah, any linux devs reading this: thank you thank you thank you. I don't mean to be rude. KUTGW.

---

