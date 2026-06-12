---
title: "problems creating a symbolic link with ls"
date: 2016-03-09
forum: General Help
---

### Post by jantaro2 on 2016-03-09
Hello, would like to move my 53GB folder ./bitcoin, of course to another  drive because I m running out of space on my SSD. I tried, but I cannot  do it:


first I go to my home directory by typing cd /home

then I try to create a symbolic link

sudo ln -s /path/to/mystoragedrive/.bitcoin .bitcoin

it returns me back to the "$" line with no errors so I suppose the command runs fine but...

well I start again the dowloading of the blockchain with

bitcoind -daemon

but the blocks download to my SSD drive. So nothing has changed after running this.

Should  I erase or change the name of my ./bitcoin folder of the SSD?, right  now I got this 53GB folder ( ./bitcoin ) both in my storage drive and my  SSD.

or maybe this would solve the problem:?

bitcoind -daemon -datadir=/path/to/mystoragedrive/.bitcoin

or  maybe could I change something on the config files of bitcoind and/or  bitcoin-qt.? I don´t wanna deal with this -datadir flag every time I  start the program.

Please help, would not like to mess up anything that´s why I´m asking. Kind regards!.

---

### Post by pqwoerituytrueiwoq on 2016-03-09
run ls -l ~/.bitcoin
ln will not make a symlink if it is going to overwrite anything, unless you use the f option (force)

another option is to use /etc/fstab to bind ~/.bitcoin to /path/to/mystoragedrive/.bitcoin

example bind
[FONT=courier new]/home/root                                /root           bind    defaults,bind   0       0[/FONT]
this is like having a link doing this: [FONT=courier new]/root -> /home/root[/FONT] except you can't tell it is a link
this will not delete anything in /root
if you unmount /root all the stuff that was there when you created the mount point will be there (this can be used to make a super hidden folder)

---

### Post by ajgreeny on 2016-03-09
Your comment > first I go to my home directory by typing cd /home may be your first mistake as that does not take you to your home directory but to the folder that contains your home directory, ie /home, so the symbolic link you made is now sitting in /home not in /home/username where I suspect you wanted it to be.

The command to return to your home is simply **cd**

---

### Post by Bucky Ball on 2016-03-09
You don't need to be in any folder. In fact, that could be one of your mistakes. It doesn't work like that. You need the full path. For instance, open a terminal and:

```
sudo ln -s /path/to/mystoragedrive/.bitcoin /home/username/.bitcoin
```

Done. Doesn't matter what folder your in.

Your other major issue is that it works like this:

```
ln -s 'location to link to' 'name of symlink'
```

See? The command in my example will create a link to the folder in your storage drive to the /.bitcoin folder in your /home/username folder. 

And lastly, if you want to move data or a folder, symlinks won't help you. They are not for that. Why not just create a folder on the data drive, drag and drop the data from one to the other, delete the original folder?

---

### Post by ajgreeny on 2016-03-09
But having used the command  ```
sudo ln -s /path/to/mystoragedrive/.bitcoin .bitcoin
``` while you were in /home and not in /home/username, it is now in /home that the symbolic link will be sitting as it will go into the current terminal folder by default.

You must to use the full pathway for the symbolic link if your terminal is not in your home folder.

---

### Post by jantaro2 on 2016-03-10
Really I made a mistake:browsing around,  I found a graphical link on the place that I applied  the command ls . I made it on the wrong folder, I see. Thanks a lot for your help!.

---

### Post by ajgreeny on 2016-03-10
I am very pleased to hear that you have figured out what went wrong!

Please mark this thread as SOLVED  from the Thread Tools menu at the top.
Marked as SOLVED on your behalf.

---

