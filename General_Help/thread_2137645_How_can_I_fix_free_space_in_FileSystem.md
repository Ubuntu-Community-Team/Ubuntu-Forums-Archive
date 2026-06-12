---
title: "How can I fix free space in FileSystem?"
date: 2013-04-21
forum: General Help
---

### Post by Jorgerv on 2013-04-21
ubuntu continues saying there is just a few KB left in filesystem ( 40GB disk) so i can not save anything there because of the space, I have used bleachbit to delete temporary files, free space, empty trash and all of that but it did not work for me, also I have the same problem in another disk and the only thing i do with the computer is download torrents using Deluge, why this happens..... what can i do?, for example i had like 20GB in another disk used by some movies and after  I delete those movies it is suposed i had 20GB free but then I tried to save another file and it said it was full, weird right

---

### Post by agillator on 2013-04-21
How do you delete files? If you use the file manager they may be put in a hidden trash directory instead of actually deleted. 'Emptying' the trash container shown on your desktop may not get all the files. Check a few of your directories for a hidden trash directory. To do this, open a terminal window and look in some of your directories for a .Trash* directory. Delete the contents of any you find using the rm command, not the file manager. Then, see if you have more space available.

---

### Post by Jorgerv on 2013-04-21
I just delete them by pressing del key , but the hidden trash directory has a lot of sense, I did not know Ubuntu did that as I deleted trash files using bleachbit so i will try to find any hidden folder but where should i normally search for that .trash, thank you for the initial quick answer

---

### Post by pfeiffep on 2013-04-21
> **Jorgerv said:**
> I just delete them by pressing del key , but the hidden trash directory has a lot of sense, I did not know Ubuntu did that as I deleted trash files using bleachbit so i will try to find any hidden folder but where should i normally search for that .trash, thank you for the initial quick answer

You should be able to view your trash in nautilus - there's a trash icon on left - to view hidden files click on down arrow icon (upper left of nautilus) choose show hidden files.  If you're brazen you can right-click on the trash icon and empty trash.

CLI option overview [here]("https://help.ubuntu.com/community/DeletingFiles")

---

### Post by ibjsb4 on 2013-04-21
You have user trash and root trash.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=delete+trash&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=delete+trash&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=delete+root+trash&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=delete+root+trash&sa=Search&cof=FORID:9)

BleachBit should do a good job of cleaning things up, but heres some other tips.

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

The only thing I don't recommend is deborphan, it can remove wanted files.  So if you do use it, use with caution.

Take a look at your partitions too.  In terminal:

```
df -h
```

General filesystem cleaning.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=clean+file+system&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=clean+file+system&sa=Search&cof=FORID:9)

---

### Post by matt_symes on 2013-04-21
Hi

It may be worth checking the log files.

In the terminal, copy and paste.

```
sudo du -csh /var/log/ /home/"$USER"/.xsession-errors{,.old} 2> /dev/null
```

Enter your password. It will not be echoed to the screen.

Post the results back here.

USER must be in capitals as Linux and Ubuntu is cast sensitive.

Kind regards

---

### Post by Jorgerv on 2013-04-21
I found folders called .trash-1000 but nothing in there, which can be the problem?

---

### Post by matt_symes on 2013-04-21
Hi

Try post #6. Worth a look.

Log files can get big sometimes.

Kind regards

---

