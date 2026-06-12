---
title: "Same file across multiple samba shares"
date: 2016-03-17
forum: General Help
---

### Post by Devin_Van_Komen on 2016-03-17
Hello, 

So I have a directory of files. Each file contains information on computer passwords and hardware info. Now that is located on a master samba share where only a select few have access. Now I have teams that need password info for their respective teams virtual machines. My plan was to use the source files in the master share, then hard link each team their own password file. That way if they change their passwords, it reflects in the master share. No more haveing to change it in 2 to 4 places. 

Now I thought that was how hard links work, but when one person changes the hard linked file it does not reflect on the master file. So I tried symlinks (which is basically like a windows shortcut right? ) But that failed to reflect the info on the source file as well. Its almost like im just copying and pasting, not creating any sort of liked file structure. Im not sure what I am doing wrong. I tried the following commands in the terminal
```

cp -al source_file target_file
ln source_file target file
ln -s source_file target_file
```

Is there a different type of link that I should be using? I could have sworn Ive used hard links and soft links to perform this exact task before, but for some reason its not working. Any info on helping me do this would be much appreciated thank you. 

samba version 4.1.6-ubuntu
HP Micro server 
Ubuntu server 14.04.1

---

### Post by bab1 on 2016-03-17
> **Devin_Van_Komen said:**
> Hello, 

So I have a directory of files. Each file contains information on computer passwords and hardware info. Now that is located on a master samba share where only a select few have access. Now I have teams that need password info for their respective teams virtual machines. My plan was to use the source files in the master share, then hard link each team their own password file. That way if they change their passwords, it reflects in the master share. No more haveing to change it in 2 to 4 places. 

Now I thought that was how hard links work, but when one person changes the hard linked file it does not reflect on the master file. So I tried symlinks (which is basically like a windows shortcut right? ) But that failed to reflect the info on the source file as well. Its almost like im just copying and pasting, not creating any sort of liked file structure. Im not sure what I am doing wrong. I tried the following commands in the terminal
```

cp -al source_file target_file
ln source_file target file
ln -s source_file target_file
```

Is there a different type of link that I should be using? I could have sworn Ive used hard links and soft links to perform this exact task before, but for some reason its not working. Any info on helping me do this would be much appreciated thank you. 

samba version 4.1.6-ubuntu
HP Micro server 
Ubuntu server 14.04.1
The hard link is used to create a link to the *_same file_* in two places.  The link is really a link to the inode not the file directly.  A true hard linked set of files have the same inode.  If you want a hard link to a specific file you just use the command without first creating a second file.  Something like this (where the "hard" link does not previously exist)```

ln [COLOR="#FF0000"]source_file[/COLOR] [COLOR="#0000FF"]hard_link_to_source_file[/COLOR]
```
The original pointer to the file will be replicated to the location you designate.  The actual inode will only be deleted when both links to that same inode are deleted.

The sym-link does not have the same characteristics.  It has its own inode.  If you delete the source file the sym-link will be broken but not deleted.

---

### Post by Devin_Van_Komen on 2016-03-18
That is exactly what I thought. I did some testing last night and it works on server if I ssh into the server and use nano. BUT if I use samba and text editor, the other file does not show the changes and it acts like the link is broken from here on out. Its really kinda weird. I can make all the changes to a hard link  I want, but it never reflects on the original and visa versa. Is there an option in samba to respect hard links, or would have thing file mounted on different shares be like trying to hard link across two devices, it just breaks it. All the shares are located in on folder in the root directory which explains why I am able to create the hard link, but once Im accessing them through samba, I would guess it breaks them because the shares are now mounted as two separate devices.

-------EDIT-------------

After some research, it appears the problem is with gedit . Gedit for whatever reason is breaking the hard link when saving. It does not do this to files in my home directory, but everytime there is a samba hard link, it breaks it. With soft links I am able to edit the original file and it will preserve the link, but editing the soft link itself will result in the link being broken and a new file be written. So far nano, Kate, Sublime, Gedit, editra, and Komodo all break the hard link. The only way to preserve the hard link is to change the text in ssh via vi or nano. This is very upsetting. again I ask is there a setting in samba to preserve hard links. I have wide links enabled, unix extensions disabled (also tried enabled but it didnt work, only made it so I could not see my symlinks),  and follow symlinks enabled, so that rules that out.

---

### Post by bab1 on 2016-03-18
> **Devin_Van_Komen said:**
> That is exactly what I thought. I did some testing last night and it works on server if I ssh into the server and use nano. BUT if I use samba and text editor, the other file does not show the changes. Its really kinda weird. I can make all the changes to a hard link  I want, but it never reflects on the original and visa versa. Is there an option in samba to respect hard links, or does it just take time for the samba to recognize the changes?

The whole idea of using a hard or soft links via a Samba share is problematic to begin with.  See the pertinent section of the smb.cof man page below```


#Smb.conf global parameter

       unix extensions (G)

           This boolean parameter controls whether Samba implements the CIFS UNIX
           extensions, as defined by HP. These extensions enable Samba to better serve UNIX
           CIFS clients by supporting features such as **symbolic links, hard links, etc**...
           These extensions require a similarly enabled client, and are of [COLOR="#FF0000"]no current use to
           Windows clients.[/COLOR]

           Note if this parameter is turned on, the wide links parameter will automatically
           be disabled.

           See the parameter allow insecure wide links if you wish to change this coupling
           between the two parameters.

           Default: unix extensions = yes

```
Are your Samba clients using Windows?

---

### Post by mcgess on 2016-03-18
[RIGHT][LEFT]Hi

```
cp -al source_file target_file
ln source_file target file
ln -s source_file target_file
```

[/LEFT]
[/RIGHT]
 If target_file is the file you want to access using a link aren't the source and targets the other way around

```
ln targetfile source_file 
ln -s target_file source_file
```

Martin

---

### Post by Devin_Van_Komen on 2016-03-21
Thanks for the info bab1, That makes sense why I cant use wide links and symlinks at the same time. And why hard links keep breaking. Hard and soft links via samba are just not compatible I guess. Looks like ill just have to find another way to sync passwords while not giving all the passwords to everyone...

---

