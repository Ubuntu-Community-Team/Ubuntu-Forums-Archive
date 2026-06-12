---
title: "Computer Lab for handicapped adults.... Can you help me?????"
date: 2020-07-08
forum: General Help
---

### Post by az64x on 2020-07-08
I volunteer at a non profit that cares for 130 handicapped adults near Houston.     I am a retired IT person, but so very new to Linux.  Can You Help Me?????

 
 
 I want to setup several old computers as Internet surfing machines for the handicapped adults.  However the handicapped people download so many virus files that it effects entire network.

 
 
 I want to use Lunbuntu or Ubuntu on a boot-able USB.  Every night they will turn off the machine.  The next morning they start with a new  Lubuntu from the USB.  The users could not store or read anything on the USB nor the computer hard drive.

 
 
 They could ONLY surf the web and NOT save any files
 
 
 I would like to set the Temp files to be stored on the computer hard drive. So it will run a little faster.
 
 
 **_What would be ideal is_ i**f the computer hard drive could be quick formatted (or erased) every morning after the USB Lubuntu starts up.  So no matter what virus files are downloaded, they would be remove tomorrow.

 
 
 Something like the Autoexec.bat file in DOS.

 
 
 I would appreciate any help.

---

### Post by overdrank on 2020-07-08
You have asked this question before in your other [**thread**]("https://ubuntuforums.org/showthread.php?t=2424615&p=13879032#post13879032")

---

### Post by TheFu on 2020-07-08
That old thread provided a number of options.
Seems some basic understanding for how Unix-systems work is lacking based on the questions.  There  is no need to reformat a HDD. That would be a total waste of effort for ZERO return.  Unix systems are multiuser and non-admin uses can't harm the OS. By deleting a userid and recreating a new one daily, you would effectively prevent any virus from being on the system more than 1 day.

The bootable USB isn't needed either, but if that is what you want, fine.

Be certain to have a way to patch the systems weekly.  if they are on the network with ssh enabled, patching from a central system is trivial.  Same for all software installation and any userid or file cleanup desired.  Each of these things would be a 5 line script - extremely trivial.  

DOS skills only translate slightly.  Scripting on Unix systems brings full programming capabilities for everyone.

---

