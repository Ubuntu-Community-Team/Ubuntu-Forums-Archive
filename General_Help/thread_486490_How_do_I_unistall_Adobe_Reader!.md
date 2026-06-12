---
title: "How do I unistall Adobe Reader?!"
date: 2007-06-28
forum: General Help
---

### Post by Keen101 on 2007-06-28
ok, I wanted to see if Adobe Reader 7.09 or whatever had the "export pictures" feature like it did on windows, so I downloaded and installed the tar.gz file from adobe. We'll as it turns out It did not, and Adobe Reader was bulky and too slow for my taste. 


But here is the thing, since it was not installed via apt, how do I remove it? 


I thought the installer said just to delete the folder, but I am having a pain trying to use "sudo chown" to rename everything in the folder so i can delete it. Is there a better or easier way?


Thanks
-Keen101

---

### Post by kevinlyfellow on 2007-06-28
> **Keen101 said:**
> ok, I wanted to see if Adobe Reader 7.09 or whatever had the "export pictures" feature like it did on windows, so I downloaded and installed the tar.gz file from adobe. We'll as it turns out It did not, and Adobe Reader was bulky and too slow for my taste. 


But here is the thing, since it was not installed via apt, how do I remove it? 


I thought the installer said just to delete the folder, but I am having a pain trying to use "sudo chown" to rename everything in the folder so i can delete it. Is there a better or easier way?


Thanks
-Keen101

To change the ownership of files in a folder you can use the recursive option
```
sudo chown -R keen:keen folder
```

but I don't really know why you are trying to change the ownership.  You can just remove the folder
```
sudo rm -r folder
```

---

### Post by Keen101 on 2007-06-28
sudo rm -r folder worked!         The reson I was trying to rename everything was because to only command line function I knew was rmdir, and it was not working.



Thanks!
-keen101

---

### Post by kevinlyfellow on 2007-06-29
> **Keen101 said:**
> sudo rm -r folder worked!         The reson I was trying to rename everything was because to only command line function I knew was rmdir, and it was not working.



Thanks!
-keen101

I never heard of that command before!  I'll have to try it out sometimes... Thanks for sharing that :-)

---

### Post by MCSE_Crossover on 2007-06-29
be careful with it though. RM -r is a VERY powerful command. Execute it in the wrong place and **poof** there goes your hard drive.

---

### Post by kevinlyfellow on 2007-06-29
True, many people like to alias rm in their .bashrc (~/.bashrc) to rm -i which asks them everytime it is about to delete a file if you want to do it.  If you'd like to do that for safety, just put this
```
alias rm="rm -i"
```
in ~/.bashrc and also in /root/.bashrc  If it becomes too much to handle for a job running the command unalias rm will bring it back to its default.  Did that make any sense?

---

### Post by stchman on 2007-06-29
> **Keen101 said:**
> ok, I wanted to see if Adobe Reader 7.09 or whatever had the "export pictures" feature like it did on windows, so I downloaded and installed the tar.gz file from adobe. We'll as it turns out It did not, and Adobe Reader was bulky and too slow for my taste. 


But here is the thing, since it was not installed via apt, how do I remove it? 


I thought the installer said just to delete the folder, but I am having a pain trying to use "sudo chown" to rename everything in the folder so i can delete it. Is there a better or easier way?


Thanks
-Keen101

Adobe 7 reader is available through Synaptic from medibuntu.

[http://www.stchman.com/install_adobe.html](http://www.stchman.com/install_adobe.html)

If you want to re-install it use this procedure.

---

