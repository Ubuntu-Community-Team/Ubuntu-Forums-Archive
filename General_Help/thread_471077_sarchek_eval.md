---
title: "sarchek eval"
date: 2007-06-11
forum: General Help
---

### Post by curtk69 on 2007-06-11
hey dudes, i am very new to linux and must be doin something wrong?

i downloaded this file from sarchek and am trying to install it but its not working.  when i copy n paste their comand line into a shell it doesnt seem to find their file which is right on my desktop, both the zip file and the extracted folder as well

this is one of their response emails to my request for help but its of no use since its no different then the install instruciotns.


I'm not quite sure why you are having a problem. The normal procedure is to
copy or save the email attachment which is called sclin.taz on your Linux
box.  Please verify the size of the sclin.taz file before you run the
command and it's location. The message you are receiving indicates it
doesn't find the file or it doesn't exist.

Once its on your Linux system and run the following commands.


Log in as root.


  1.. Now copy, uncompress, and detar:
  zcat < /tmp/sclin.taz | tar xvfP -

The install procedure will put SarCheck into the /opt/sarcheck/bin
directory.

I hope this helps,


so can someone walk me throught the steps starting with how to login as root?

then howto copy, uncompress and detar;

i think i have already done this but like i said i am a newbie

---

### Post by croto on 2007-06-11
Hey man,

First of all, where did you download the file? Open a terminal (Applications->Accesories->Terminal), and type ls . That will show you what files you have in your home directory. You can use the command cd to change to another directory. So go to the directory where you downloaded the file. Now, in the terminal, type:
```

sudo bash
zcat < /tmp/sclin.taz | tar xvfP -
exit

```

With the first line, you are becoming root (it will ask you a password, just enter *your* user password). The second line "uncompresses and detars"  the file to /opt/sarcheck/bin (acording to what you say). The third line is to go back to the normal user. 
Ok I think that should be enough. Try to change directory (with the cd command) to /opt/sarcheck/bin and list the files there (ls command). One of those files must be the executable. You can run it with (assuming the file is called sar)
```

./sar

```

---

### Post by curtk69 on 2007-06-11
ok i did what you said

you were sucessful in teaching me howto login as root, thanks

but as for the other stuff it still does the same thing, it cant find that file?
are files on my desktop not part of my home directory ?
if not am i supposed to move it there?

---

### Post by croto on 2007-06-12
When you open a terminal, you are in your home directory. That means that if you type **"ls"** you'll see the contents of your home directory. The files you have on the desktop are in the directory Desktop. To change to there, type **"cd Desktop"**. To go back to the previous directory, type **"cd .."**. So the idea would be to use those two commands to find out where the file you downloaded is. Then, after changing to that directory, type the commands I was suggesting in the post before.

EDIT:
Oh I just read that you are saying the file is on the Desktop. So you'll have to change there. Then, after you open a terminal, you'd have to 
```

cd Desktop
sudo bash
zcat < /tmp/sclin.taz | tar xvfP -
exit

```

---

