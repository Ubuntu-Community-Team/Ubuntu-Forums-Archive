---
title: "Sufficient way to backup for upgrade"
date: 2017-04-25
forum: General Help
---

### Post by ELMIT on 2017-04-25
Every document I read about upgrade says, first make a backup. 

What is the best / efficient way to backup for an upgrade from 16.04 to 17.04?

---

### Post by ajgreeny on 2017-04-25
I suspect you will get almost as many different suggestions to this query as you get answers; everyone seems to have their own favourite.  My next thought is to ask why you are upgrading to a version that now has only 9 months support from one with 4 years remaining; that is not to say "don't do it" but just to make sure you are aware of this.

Just to start the ball rolling, I use rsync to backup just my /home, along with copies of any system files I have manually edited, to an external hard disk (ext4 formatted) with a no encryption or compression, so if ever needed, I can very simply get the backed up file or files I have lost without a complete restoration.

I do not bother with full system backups as it is so easy to reinstall if it is ever needed, and the only files that are of real value to me are my own personal files in /home.

I know many users feel that rsync is not and never was meant to be a backup solution, but nevertheless it does everything I want very effectively.  Some of the other backup applications available use rsync in the background to do their job so I feel no need to apologise for using it "naked", as it were.

If it's any consolation to you, I have been using a separate /home, or now /data partition, for many years and through many distro version upgrades, and so far have never had a single problem with loss of personal files from my system when using the "Something Else" option at installation of the new system.

---

