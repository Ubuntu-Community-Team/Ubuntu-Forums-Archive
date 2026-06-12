---
title: "How to transfer .exe to Ubuntu server"
date: 2012-11-25
forum: General Help
---

### Post by BStrizzy on 2012-11-25
Hey guys, I am trying to upload a specific file folder to my ubuntu server and i keep getting an error message. I am sending this file via my windows 7 operating system and it contains an .exe(which is the file) I am getting an error message on. Any ideas why this is happening? 

It is a mame emulator that im trying to post on my server so my roomates can play my games too.

---

### Post by coldcritter64 on 2012-11-25
> **BStrizzy said:**
> .. Any ideas why this is happening? ...
It would also help if you posted the actual error message, doing so is likely to get you better assistance and not wild guesses :).

---

### Post by BStrizzy on 2012-11-25
> **coldcritter64 said:**
> It would also help if you posted the actual error message, doing so is likely to get you better assistance and not wild guesses :).


there are 32 more of these error messages. Keep in mind that I do not have a samba server because I am normally on my ubuntu operating system. Will i need this samba in order to make this happen and for my roomates who have windows to upload there stuff as well?
[IMG]file:///C:/Users/BStrawt/AppData/Local/Temp/moz-screenshot.png[/IMG][IMG]file:///C:/Users/BStrawt/AppData/Local/Temp/moz-screenshot-1.png[/IMG]

---

### Post by coldcritter64 on 2012-11-25
> **BStrizzy said:**
> there are 32 more of these error messages. Keep in mind that I do not have a samba server because I am normally on my ubuntu operating system. Will i need this samba in order to make this happen and for my roomates who have windows to upload there stuff as well?
[IMG]file:///C:/Users/BStrawt/AppData/Local/Temp/moz-screenshot.png[/IMG][IMG]file:///C:/Users/BStrawt/AppData/Local/Temp/moz-screenshot-1.png[/IMG]

Can see now why you didn't post the error. :)

If you are trying to share files with windows you [s]WILL[/s] (edit: wrong emphasis) need the samba service and possibly winbind as well installed. I'd say there is a good chance that is why the errors are popping up. Cheers.

---

### Post by personalpc on 2012-11-25
long story short, yes samba is a great tool for sharing files to windows users. If you would like to get around using samba, you can use ftp or if you prefer the security of ssh there is always sshfs. check out this link [http://code.google.com/p/win-sshfs/]("http://code.google.com/p/win-sshfs/")

---

### Post by personalpc on 2012-11-25
> **coldcritter64 said:**
> Can see now why you didn't post the error. :)

If you are trying to share files with windows you WILL need the samba service and possibly winbind as well installed. I'd say there is a good chance that is why the errors are popping up. Cheers.

samba is only good in network. Apache or sshfs much better much faster for windows on outside networks. Cheers mate!

---

### Post by BStrizzy on 2012-11-25
> **coldcritter64 said:**
> Can see now why you didn't post the error. :)

If you are trying to share files with windows you WILL need the samba service and possibly winbind as well installed. I'd say there is a good chance that is why the errors are popping up. Cheers.

thanks alot, can you tell me more about samba, i can not get a solid definition and how to create it

---

### Post by coldcritter64 on 2012-11-25
> **BStrizzy said:**
> thanks alot, can you tell me more about samba, i can not get a solid definition and how to create it
Others above have mentioned methods you should also consider, depenping on your needs. Samba is one method for filesharing. 

Does your install have a desktop or is it headless? Need to know for advice regarding installation methods. A desktop that has Nautilus installed makes it rather easy to install samba, whereas a headless server = command line.

---

### Post by rnerwein on 2012-11-26
> **BStrizzy said:**
> there are 32 more of these error messages. Keep in mind that I do not have a samba server because I am normally on my ubuntu operating system. Will i need this samba in order to make this happen and for my roomates who have windows to upload there stuff as well?
[IMG]file:///C:/Users/BStrawt/AppData/Local/Temp/moz-screenshot.png[/IMG][IMG]file:///C:/Users/BStrawt/AppData/Local/Temp/moz-screenshot-1.png[/IMG]

 your thumbnail shows me an ERROR 8 and this is a unix error-number which means:

#define ENOEXEC      8  /* Exec format error */

try to rename your file to xxxxx.txt - i guess than it will work.

---

### Post by BStrizzy on 2012-11-26
> **rnerwein said:**
> your thumbnail shows me an ERROR 8 and this is a unix error-number which means:

#define ENOEXEC      8  /* Exec format error */

try to rename your file to xxxxx.txt - i guess than it will work.

Ok will do. when I upload it as a txt, when the user downloads it from the server do they just change the file back to xxxxx.exe?

---

### Post by BStrizzy on 2012-11-26
> **personalpc said:**
> samba is only good in network. Apache or sshfs much better much faster for windows on outside networks. Cheers mate!

awesome advice, I will be installing samba later today and seeing if we can't get this to work

---

### Post by BStrizzy on 2012-11-26
> **coldcritter64 said:**
> Others above have mentioned methods you should also consider, depenping on your needs. Samba is one method for filesharing. 

Does your install have a desktop or is it headless? Need to know for advice regarding installation methods. A desktop that has Nautilus installed makes it rather easy to install samba, whereas a headless server = command line.

Ok I have a desktop headless unit that I use, and usually use everything thru command line. I do have a monitor and a keyboard that is stashed away next to the headless unit that will take me like 5 seconds to hook back up. I also do not have a gui on the server and also thinking about adding one. 

I also have, but rarely use webmin, and I know in the networking tab I can set up a share there? saw some youtube videos with this method but not very clear

what do you think I should do? 
1.) set it up thru SSH? which I enjoy doing/learning
2.) hook up the headless unit to my monitor and do it thru command line?(straight from headless server)
3.) hook up the headless unit to monitor and do it thru the GUI (that you can help me install also :) )
4.) or use webmin

---

