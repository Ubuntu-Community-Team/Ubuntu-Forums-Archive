---
title: "cant paste 'sy' script into /home/graham/.gimp-2.8/plug-ins directory"
date: 2020-01-27
forum: General Help
---

### Post by gt123456789 on 2020-01-27
Hi,

I have installed Ubunto onto a laptop and all is working great.

I now want to install a plugin for gimp but it wont let me paste the 'sy' file into the /home/graham/.gimp-2.8/plug-ins directory. I think that this is a permissions issue but dont know what to do next.

Please can someone tell me what I need to do to get the correct permissions so I can get the plugin working.

Thanks in advance

---

### Post by CelticWarrior on 2020-01-27
Please tell us how are you trying to copy it and what are the exact error messages.

---

### Post by gt123456789 on 2020-01-27
I am right clicking on the file to copy and paste into the directory but it is a pink coloured window but it doesnt work.

Please can you tell me the best way to do it. I am deffo no expert in Linux but have a little knowledge (which I know is dangerous)

---

### Post by CelticWarrior on 2020-01-27
The part "it doesn't work" needs elaboration. Nobody here can see what you are seeing.

---

### Post by gt123456789 on 2020-01-27
when I right click in the desired window in the plugin directory i dont gett any options to paste (as I would in Windows)

---

### Post by CelticWarrior on 2020-01-27
Are you using the regular file manager? If so, I really don't understand "window in... the directory"...

---

### Post by gt123456789 on 2020-01-27
the file is zipped in my downloads directory so is there a prefered method for coying the file from there into the gimp plugin directory?

Can you recomend the best way to do it?

---

### Post by CelticWarrior on 2020-01-27
Do you need to copy the zip file as is or decompress it and copy the actual contents to that directory?

---

### Post by gt123456789 on 2020-01-27
there are 2 'sy' files in the zip directory that I need to put into the gimp plugin directory

---

### Post by CelticWarrior on 2020-01-27
So all you need to do is double-click the zip file - it opens with the proper software - then click extract and navigate to the desired directory to be extracted.

---

### Post by gt123456789 on 2020-01-27
when I do that I get the error message: you dont have the right permissions to extract archives in the folder 'plug-ins'

---

### Post by The Cog on 2020-01-27
Do you want to put the zip file into the plugins directory, or do you want to put the two .sy files in there?

I don't think you can copy the contents of a zip file without extracting it first. In xubuntu the copy option in the archive viewer looks like it's working, but paste in the file manager is greyed out afterwards. I guess also true for Ubuntu. Extract the zip, copy the file, then delete the extracted contents again.

---

### Post by CelticWarrior on 2020-01-27
That is precisely what I asked some 9 posts ago...
And that's a huge problem because your user should have permission in its own home folder. Have you been running graphical software with 'sudo' perhaps?

Hopefully it can be correct by ```
sudo chown -R user /home/graham
```

---

### Post by gt123456789 on 2020-01-27
I believe I need to change the permissions for my user account to that of an admin so I can then extract the files but I dont know how to do that.

It is my laptop with 1 user account which is called graham (me). I have tried google to figure out how to change to admin but dont understand how to do it

---

### Post by gt123456789 on 2020-01-27
wgen I paste that code into a terminal window it asks me for the graham password, which I type in but then the prompt stays the same

---

### Post by CelticWarrior on 2020-01-27
Your user is the "admin" when using sudo...

Of course the prompt stays the same. Now, when you try to extract to the same directory, what happens?

---

### Post by The Cog on 2020-01-31
> **gt123456789 said:**
> I believe I need to change the permissions for my user account to that of an admin so I can then extract the files but I don't know how to do that.
You do not need to change the permissions of your account. 

If you are working inside your home directory (/home/graham) then you should not need to raise your permissions at all. I think we need more info to figure out what the problem is. Firstly, can you please show us the permissions of the file you are trying to extract.  And let's see the permissions of the plugins directory too. Open a command prompt and use these commands:
```
ls -l Downloads/filename
ls -ld .gimp-2.8
ls -ld .gimp-2.8/plug-ins
```
Copy all the conversation (commands and responses) and post back here. This should tell us a lot.

By the way, the normal way to raise your user permissions is to use sudo in front of the command. This causes the command to execute as user root - it does not permanently change your ID. For instance, try:
```
ls -a /root
sudo ls -a root
```
See: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

