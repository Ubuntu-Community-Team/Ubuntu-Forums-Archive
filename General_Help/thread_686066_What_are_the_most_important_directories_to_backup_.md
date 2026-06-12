---
title: "What are the most important directories to backup? How do I do it?"
date: 2008-02-02
forum: General Help
---

### Post by enthusaroo on 2008-02-02
Hey everyone,

I am giving my computer to someone. So I need a way to backup the important configuration files and settings and logs that programs on here use. Can anyone tell me what command I can use and what the most important directories to backup? I don't need to make a backup of my /home directory, because I'm backing that one up separately. My plan is to get a new computer, and install Ubuntu afresh again. But the things that matter most to me are like the logs from Pidgin (I have no idea where they are located), and also the notes saved under Tomboy!

---

### Post by nemilar on 2008-02-02
Most configuration files are stored in the /etc folder.  This is for system processes, daemons, and the like.  User programs tend to store their configuration in hidden files in your home directory:

```
ls -a ~
```

Will show you hidden folders.  

Logs are stored in the /var/log directory.


For backing things up, I recommend TimeVault:
[How to Backup your Ubuntu System with Timevault]("http://www.techthrob.com/tech/timevault.php")

It's very easy to use and very effective.

---

### Post by jesrani on 2008-02-02
I am using Simple Backup (It is available in Synaptic) and is a good program I guess (I am a relatively new user). I have used PartImage (From SystemRescueCD) to create image of my partition. I think either should work. Only thing is that probably PartImage has to be restored fully and you cannot select the folder. I think even DriveImageXML can be used. It s available on UB4Win. It allows to browse images and restore file/folder. Even Paragon8 available on UB4Win can be used.

---

