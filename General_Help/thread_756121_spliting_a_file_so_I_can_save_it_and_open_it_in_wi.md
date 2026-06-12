---
title: "spliting a file so I can save it and open it in windows"
date: 2008-04-15
forum: General Help
---

### Post by error404 on 2008-04-15
I have a folder that it's about 7gb, and I need to .zip it or .rar in small portions like 700mb so I can join them in Windows XP


any suggestions? 

thanks!

---

### Post by forrestcupp on 2008-04-15
If it is multiple files, you can just select 700 MB of files for each zip file.  If it is actually a 7 GB file, I don't know what to tell you.

I assume the files are bigger than 700 MB, or you wouldn't be asking.

---

### Post by error404 on 2008-04-15
BTW
both computers are connected to the same router, so... If I could just link them together I could transfer the files like that too.However, I spent the whole day trying to do that with no luck

---

### Post by djrobthaman on 2008-04-15
Why is it that you need to split the 7gb file for windows?  Are you using a fat file system?  NTFS should be able to handle that size.  

Anyway, if you want to connect the two pcs over the lan you can do the following:

UBUNTU BOX

Install the samba gui client (go to add/remove applications, search for samba and install the programme that pops up by that name)

Open it and and click on "Server Settings" in the drop down menu.  In the "Authentication" drop down menu, select the "share" option".

Then you just put your file in a folder somewhere, right click on the folder in nautilus and select the share option.  Or you can do this in the "Shared Folders" option in the System drop down menu in the ubuntu navigation bar. 

WINDOWS BOX

Go through the regular steps to join the network.  I think you have to go into the control panel, click create home network, then type the name of the network (the default mshome is fine), type the name of your computer and hit ok.  Then you have to restart (ughhh).  After that, if you want to share a folder from here you can just right click the folder, click properties and set it up by clicking on the "Sharing" tab


Now you should be set up to transfer files between those two computers.

---

### Post by qamelian on 2008-04-15
You could use a utility like hjsplit. It isn't in the repos, but will turn up quickly enough if you search for it on Google. There are various versions and front-ends for different OSs. I tend to like the java version because the same jar file can be used on basically any OS with a working java VM. I use it frequently when splitting and joining large files is necessary.

You can find the various version of hjsplit here:
[http://www.freebyte.com/hjsplit/](http://www.freebyte.com/hjsplit/)

---

### Post by error404 on 2008-04-15
yes, it's fat32

Windows finds the Ubuntu box, but when i try open the folder it ask for a password/login and I never setup any! :confused:

---

### Post by mali2297 on 2008-04-15
You can install rar from the multiverse repository (use Synaptic). Say the folder is called *example*, then you use the command
```

rar a -v700M example.rar example

```
This should give you a split archive where each part is max 700 MB.

---

### Post by error404 on 2008-04-15
> **mali2297 said:**
> You can install rar from the multiverse repository (use Synaptic). Say the folder is called *example*, then you use the command
```

rar a -v700M example.rar example

```
This should give you a split archive where each part is max 700 MB.

thanks for all the answers (everybody had a different approach :) )

as of right now, I'm trying the rar -v700m .... I don't know if it's working yet (the file is being generated right now) but so far so good :popcorn:

---

### Post by error404 on 2008-04-15
yes... it's working \\:D/

---

### Post by djrobthaman on 2008-04-15
I'm glad the archiving worked out for you, but just to let you know in case you want to share between computers at some other time.  That password issue gets resolved when you select "share" in the authentication drop down in samba.

---

