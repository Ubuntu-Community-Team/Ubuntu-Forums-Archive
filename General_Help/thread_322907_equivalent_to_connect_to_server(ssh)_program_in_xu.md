---
title: "equivalent to connect to server(ssh) program in xubuntu?"
date: 2006-12-21
forum: General Help
---

### Post by honeydew on 2006-12-21
I just started using xubuntu w/beryl and I am loving it.  However over the past year or so I have become very accustomed with the connect to server script in ubuntu(natilus)  where I can mount a ssh session as a file system.  I would do this under the connect to server(?) script in the places(?) menu.  I am in dire need of a equivalent to something like this in xfce.. or should I install natilus?  I searched google for thunar ssh capability but I didnt come across anything of substance.  Please any thoughts or a ideas will be a big help.

---

### Post by lamego on 2006-12-21
I believe that feature as you know it is specific to Nautilus...
You can install putty which is available on the repositories and is a fine SSH client...

---

### Post by dannyboy79 on 2006-12-21
> **honeydew said:**
> I just started using xubuntu w/beryl and I am loving it.  However over the past year or so I have become very accustomed with the connect to server script in ubuntu(natilus)  where I can mount a ssh session as a file system.  I would do this under the connect to server(?) script in the places(?) menu.  I am in dire need of a equivalent to something like this in xfce.. or should I install natilus?  I searched google for thunar ssh capability but I didnt come across anything of substance.  Please any thoughts or a ideas will be a big help.

i am not sure what you are trying to accomplish but you can just use the command line to ssh into your other box! if you are trying to copy something over to another computer than simply, cd the directory containing the file, then "scp filename username@ip:" and this will copy the file over to /home/username directory of your other computer. i use xubuntu and I can tell you, if you have an older computer with limited space, installing nautilus is goiung to bring in tons of gnome dependencies you don't want! if you're doing this over a local lan, why would you need to encrypt your traffic? post back with specifically you want to do and I can maybe help some more.

---

### Post by honeydew on 2006-12-21
yah I am currently using scp and sftp... but I like the movement I recieved from the natilus pluggin.  I use ssh localy and when I am traveling.  It was nice being able to click a icon to my specific server and copy edit files as I needed.  I have read about something sshfs or something which I may look into.  Gftp is suppose to have support for this however it kept on freezing on my machine when I tried to run ssh.  a simple gui that supports sftp would do just fine.  Or I would happily use something along the lines of ncftp if there is a command lind sft client that has more options.

---

