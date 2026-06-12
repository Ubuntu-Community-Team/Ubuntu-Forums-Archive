---
title: "Hard disk fills up with An unknown data"
date: 2016-01-10
forum: General Help
---

### Post by offir on 2016-01-10
i have ubuntu 15.04
Yesterday I had 10 GB free hard disk space
After two hours of surfing the web
Hard disk fills up

How can one fix it
Why is this happening

---

### Post by ajgreeny on 2016-01-11
What surfing were you doing; downloading anything or just general surfing?

We need to know what is using all that space so first run command ```
du -h  | sort -h
``` to see if any of your home folders are larger than expected and using the disk space.

In your file manager you can right click on any root filesystem folders to see the size on disk which might give you a clue or you can use **Disk Usage Analyser** to see things in GUI.

---

### Post by HermanAB on 2016-01-11
You can get a list of files - large to small - with this command:
$ ls -RSal

---

### Post by offir on 2016-01-11
> What surfing were you doing; downloading anything or just general surfing?
just general surfing that is way it is so strange

> 
We need to know what is using all that space so first run command

```
du -h  | sort -h
```

to see if any of your home folders are larger than expected and using the disk space.


I got a big list
I checked against the folders

The same size



To be more clear
I had 1.6 GB free space
I deleted some files and came to 10 GB
After two hours of surfing (youtube mostly) without downloading files (I can not download)
I received a warning that the drive is full

More deleted files and came to 2.2 GB free space

At the moment it has not changed

---

### Post by ajgreeny on 2016-01-11
Sorry; my mistake as I forgot I have an alias for du which did strange things when I tried the command.

You need to limit the depth of the command to stop it being recursive, hence your huge output list.

Try ```
du -h -d 1 | sort -h
``` instead to show just folders in the one level of your home directory content.  To see files in the /home folder as well as folders use ```
du -ha -d 1 | sort -h
```

---

### Post by XBNCPRk on 2016-01-11
Does this space free up after you close whichever browser you are using? Alternatively, does clearing the browsers cache free up this space as well? 

When you say deleted files, you mean deleted and emptied the trash too, I assume? 

And when ajgreeny mentioned seeing if any folders were large, I believe he meant are larger than they should be, not that they are the same size as noted in Nautilus or whatever you are using to browse your directory. Certainly if theres something filling up folders youll see a noticable jump in the size of one of them while recreating the issue youre having.

---

### Post by offir on 2016-01-11
> Sorry; my mistake as I forgot I have an alias for du which did strange things when I tried the command.

You need to limit the depth of the command to stop it being recursive, hence your huge output list.

no problem

i did what you said

i get a smaller list

one of the folder says 68 GB (movies)
on gui it says 72 GB
i did try to download a movie to this folder but at the end it failed 
i try servel times
but that was a week ago 




> Does this space free up after you close whichever browser you are using? Alternatively, does clearing the browsers cache free up this space as well? 
i use firefox
 i config it to delete all info and Cache when i close it



> When you say deleted files, you mean deleted and emptied the trash too, I assume?
of course


> And when ajgreeny mentioned seeing if any folders were large, I believe he meant are larger than they should be, not that they are the same size as noted in Nautilus or whatever you are using to browse your directory. Certainly if theres something filling up folders youll see a noticable jump in the size of one of them while recreating the issue youre having.
i know I understood

---

### Post by ajgreeny on 2016-01-12
What exactly is in that movies folder?  Do you have any bad files that are corrupt duplicates of the failed download?

---

### Post by offir on 2016-01-12
> What exactly is in that movies folder?
youtube  clips mostly 
movies i download with qbittorrnet 

> Do you have any bad files that are corrupt duplicates of the failed download? 

i dont know
i dont see any files that corrupt or duplicates 
all files are working

when a download is failed it is deleted from the downloads tab 
and that is it 
it dont show any where

---

### Post by ajgreeny on 2016-01-12
Any discussion of the downloading of youtube videos is forbidden on the forum as it contravenes youtube terms and conditions, (see section 5L of [https://www.youtube.com/static?gl=GB&template=terms](https://www.youtube.com/static?gl=GB&template=terms)) and I note from your comment above that you have downloaded clips.  As your problem or question was not directly about this I shall not close this thread.

Please remember this in future.

Regarding your original query, it is still difficult to know what is causing your problem and so far we still do not know where all the space is being used.

Can you show the output of terminal command ```
df -h
``` which will tell us how much room there is on all the mounted filesystems and how much of that is already in use.  Then if you can post the output of that ```
du -h -d 1 | sort -h
``` command we may be able to put the two together and figure out which of your home folders (if indeed it is in your home) is using all the space.

---

### Post by offir on 2016-01-13
>  Any discussion of the downloading of youtube videos is forbidden on the forum as it contravenes youtube terms and conditions, (see section 5L of [https://www.youtube.com/static?gl=GB&template=terms](https://www.youtube.com/static?gl=GB&template=terms)) and I note from your comment above that you have downloaded clips. As your problem or question was not directly about this I shall not close this thread.

it is diy clip not something with Copyright




> Can you show the output of terminal command


```
df -h
```



```
Filesystem      Size  Used Avail Use% Mounted on
udev            2.0G     0  2.0G   0% /dev
tmpfs           396M  6.3M  389M   2% /run
/dev/sda1       143G  130G  5.7G  96% /
tmpfs           2.0G  164K  2.0G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           2.0G     0  2.0G   0% /sys/fs/cgroup
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           396M   24K  396M   1% /run/user/1000



```




> 

```

du -h -d 1 | sort -h
```

command we may be able to put the two together and figure out which of your home folders (if indeed it is in your home) is using all the space. 


i get the same list as before 
with this in first and second line

```

du: cannot read directory &#8216;./.gvfs&#8217;: Permission denied
du: cannot read directory &#8216;./.cache/dconf&#8217;: Permission denied

```


now it show me 5.6 GB free

---

### Post by ajgreeny on 2016-01-13
> it is diy clip not something with Copyright
In your particular case there is therefore no problem, but the forum will still not allow discussion of youtube downloads as the info would cover everything including copyright material.

To your problem.

The root partition sda1 is 96% full which will be a problem on any system.

You should have no difficulty with that du command on your home ,and it should run and give some output even on the .gvfs and .cache/dconf folders.

Let's see what the permissions are on those folders by running command ```
ls -la .gvfs .cache/dconf
``` and post back the output here.  I suspect you may have permission problems in your home if you can't run the du command and that may be the root cause of all your problems.

---

### Post by offir on 2016-01-13
> Let's see what the permissions are on those folders by running command


```
ls -la .gvfs .cache/dconf
```

and post back the output here. I suspect you may have permission problems in your home if you can't run the du command and that may be the root cause of all your problems. 


this is what i get

```
ls: cannot open directory .cache/dconf: Permission denied
ls: cannot open directory .gvfs: Permission denied

```

---

### Post by ajgreeny on 2016-01-13
HHmmmm, something very wrong here as those files must belong to you and should output something like:-
```
~$ ls -la .gvfs .cache/dconf
.cache/dconf:
total 8
drwx------  2 *username username* 4096 Dec  8  2014 ./
drwx------ 47 *username username* 4096 Jan 13 19:17 ../
-rw-------  1 *username username*    1 Dec  9  2014 user

.gvfs:
total 128
drwx------   2 *username username*   4096 Mar 29  2013 ./
drwxr-xr-x 104 *username username* 122880 Jan 13 19:14 ../
``` with your username where I show username in italics.

That makes me wonder if there are other ownership problems in your home that might be the root cause of this whole problem.
What is the output of [code]ls -la[code/] in your terminal?

---

### Post by offir on 2016-01-14
output for 
```
ls -la
```




```
total 55780
drwxr-xr-x 53 offir offir     4096 &#1497;&#1504;&#1493; 14 06:54 .
drwxr-xr-x  3 root  root      4096 &#1497;&#1493;&#1500; 10  2015 ..
drwx------  3 offir offir     4096 &#1497;&#1493;&#1500; 10  2015 .adobe
drwxrwxr-x  2 offir offir     4096 &#1497;&#1504;&#1493; 10 17:43 amule
drwxrwxr-x  4 offir offir     4096 &#1497;&#1504;&#1493;  6 15:34 .aMule
drwxrwxr-x  3 offir offir     4096 &#1497;&#1493;&#1500; 18 08:47 .avidemux
-rw-------  1 offir offir     6373 &#1497;&#1504;&#1493; 13 21:14 .bash_history
-rw-r--r--  1 offir offir      220 &#1497;&#1493;&#1500; 10  2015 .bash_logout
-rw-r--r--  1 offir offir     3760 &#1497;&#1493;&#1500; 10  2015 .bashrc
drwx------ 30 offir offir     4096 &#1504;&#1493;&#1489; 13 17:49 .cache
drwxrwxr-x  6 offir offir     4096 &#1488;&#1493;&#1490; 20 15:29 .clamtk
drwx------  3 offir offir     4096 &#1497;&#1493;&#1500; 10  2015 .compiz
drwx------ 37 offir offir     4096 &#1497;&#1504;&#1493;  1 20:04 .config
drwxr-xr-x  4 offir offir     4096 &#1497;&#1504;&#1493; 14 06:56 .copy
drwxr-xr-x  6 offir offir     4096 &#1504;&#1493;&#1489; 15 07:08 Copy
drwx------  3 offir offir     4096 &#1497;&#1493;&#1500; 10  2015 .dbus
drwxr-xr-x  2 offir offir     4096 &#1497;&#1504;&#1493; 13 07:58 Desktop
-rw-r--r--  1 offir offir       29 &#1497;&#1504;&#1493; 10 21:53 .dmrc
drwxr-xr-x  2 offir offir     4096 &#1504;&#1493;&#1489; 19 10:08 Documents
drwxr-xr-x  3 offir offir    12288 &#1491;&#1510;&#1502; 29 10:57 Downloads
drwxr-xr-x  2 offir offir     4096 &#1491;&#1510;&#1502; 28 07:53 dwhelper
-rw-r--r--  1 offir offir     8980 &#1497;&#1493;&#1500; 10  2015 examples.desktop
drwx------  4 offir offir     4096 &#1497;&#1504;&#1493; 14 06:54 .gconf
drwxr-xr-x 24 offir offir     4096 &#1488;&#1493;&#1511; 10 10:37 .gimp-2.8
-rw-r-----  1 offir offir        0 &#1505;&#1508;&#1496; 15 19:41 .gksu.lock
drwx------  3 offir offir     4096 &#1505;&#1508;&#1496;  3 10:00 .gnome
drwx------  4 offir offir     4096 &#1491;&#1510;&#1502;  8 11:54 .gnome2
drwx------  2 offir offir     4096 &#1497;&#1493;&#1500; 10  2015 .gnome2_private
-rw-------  1 offir offir     5212 &#1491;&#1510;&#1502;  8 14:05 .gnubiffrc
-rw-rw-r--  1 offir offir 47539262 &#1491;&#1510;&#1502; 15 21:52 [COLOR="#FF0000"]google-chrome-stable_current_amd64.deb[/COLOR]
drwxrwxr-x  2 offir offir     4096 &#1491;&#1510;&#1502;  8 11:55 .gstreamer-0.10
-rw-------  1 offir offir       29 &#1497;&#1504;&#1493; 14 06:54 .gtk-bookmarks
drwx------  2 root  root      4096 &#1505;&#1508;&#1496; 16 08:31 .gvfs
drwxr-xr-x  2 offir offir     4096 &#1505;&#1508;&#1496;  3 11:22 .hplip
-rw-------  1 offir offir    62136 &#1497;&#1504;&#1493; 14 06:54 .ICEauthority
drwxr-xr-x  2 offir offir     4096 &#1488;&#1493;&#1490; 17 08:00 .icons
drwx------  4 offir offir     4096 &#1488;&#1493;&#1490;  1 18:18 .ike
drwxrwxr-x  3 offir offir     4096 &#1491;&#1510;&#1502; 15 13:20 .java
drwx------  3 offir offir     4096 &#1497;&#1493;&#1500; 10  2015 .local
drwx------  3 offir offir     4096 &#1497;&#1493;&#1500; 10  2015 .macromedia
drwx------  4 offir offir     4096 &#1497;&#1493;&#1500; 10  2015 .mozilla
drwxrwxr-x  2 offir offir     4096 &#1497;&#1493;&#1500; 10  2015 .mplayer
drwxr-xr-x  2 offir offir     4096 &#1497;&#1493;&#1500; 10  2015 Music
drwx------  3 offir offir     4096 &#1497;&#1493;&#1500; 10  2015 .nv
-rw-rw-r--  1 offir offir     1708 &#1488;&#1493;&#1490; 15 07:53 .nvidia-settings-rc
drwxrwxr-x  2 offir offir     4096 &#1505;&#1508;&#1496;  4 11:04 .oracle_jre_usage
drwxr-xr-x 14 offir offir     4096 &#1497;&#1504;&#1493; 13 21:10 Pictures
drwx------  3 offir offir     4096 &#1505;&#1508;&#1496;  3 09:59 .pki
-rw-r--r--  1 offir offir      675 &#1497;&#1493;&#1500; 10  2015 .profile
drwxr-xr-x  2 offir offir     4096 &#1497;&#1493;&#1500; 10  2015 Public
drwxrwxr-x  3 offir offir     4096 &#1497;&#1493;&#1500; 12  2015 .q3a
drwxrwxr-x  2 offir offir     4096 &#1505;&#1508;&#1496; 24 08:11 q3ut4
drwxrwxr-x 34 offir offir     4096 &#1497;&#1504;&#1493; 10 17:45 qbittorrent
drwxrwxrwx  3 offir offir     4096 &#1502;&#1512;&#1509; 30  2014 [COLOR="#00FF00"]Quake3-UrT.app[/COLOR]
-rw-rw-r--  1 offir offir  1104300 &#1505;&#1508;&#1496; 24 09:18 Quake3-UrT-Ded.exe
-rwxrwxr-x  1 offir offir   814747 &#1505;&#1508;&#1496; 24 09:18 Quake3-UrT-Ded.i386
-rwxrwxr-x  1 offir offir   959740 &#1505;&#1508;&#1496; 24 09:18 Quake3-UrT-Ded.x86_64
-rw-rw-r--  1 offir offir  2630873 &#1505;&#1508;&#1496; 24 09:18 Quake3-UrT.exe
-rwxrwxr-x  1 offir offir  1696699 &#1505;&#1508;&#1496; 24 09:18 Quake3-UrT.i386
-rw-rw-r--  1 offir offir      314 &#1505;&#1508;&#1496; 24 09:18 Quake3-UrT_Logitech_Game_Recognition.reg
-rwxrwxr-x  1 offir offir  1932046 &#1505;&#1508;&#1496; 24 09:18 Quake3-UrT.x86_64
drwx------  2 offir offir     4096 &#1497;&#1493;&#1500; 10  2015 .sbd
drwxrwxrwx  3 offir offir     4096 &#1497;&#1504;&#1493; 10 21:52 [COLOR="#00FF00"]share[/COLOR]
drwx------  5 offir offir     4096 &#1505;&#1508;&#1496; 22 07:32 .Skype
drwx------  2 offir offir     4096 &#1488;&#1493;&#1490; 27 11:40 .ssh
-rw-r--r--  1 offir offir        0 &#1497;&#1493;&#1500; 10  2015 .sudo_as_admin_successful
drwxr-xr-x  2 offir offir     4096 &#1497;&#1493;&#1500; 10  2015 Templates
drwx------  3 offir offir     4096 &#1488;&#1493;&#1511; 10 10:36 .thumbnails
drwx------  4 offir offir     4096 &#1497;&#1493;&#1500; 10  2015 .thunderbird
drwxrwxr-x  4 offir offir     4096 &#1497;&#1493;&#1500; 12  2015 UrbanTerror42
drwxr-xr-x  2 offir offir     4096 &#1497;&#1504;&#1493;  2 07:47 Videos
drwxrwxrwx  8 offir offir    53248 &#1497;&#1504;&#1493; 13 16:58 [COLOR="#00FF00"]videos2[/COLOR]
drwx------  9 offir offir     4096 &#1488;&#1493;&#1490;  6 11:01 .warzone2100-3.1
-rw-------  1 offir offir       56 &#1497;&#1504;&#1493; 14 06:54 .Xauthority
-rw-rw-r--  1 offir offir      131 &#1497;&#1493;&#1500; 10  2015 .xinputrc
-rw-------  1 offir offir       82 &#1497;&#1504;&#1493; 14 06:54 .xsession-errors
-rw-------  1 offir offir       82 &#1497;&#1504;&#1493; 13 07:08 .xsession-errors.old

```




the hdd stop fills up 
it says 5.8 for 2 days now

---

### Post by ajgreeny on 2016-01-14
You certainly need to take ownership of that .gvfs folder which is currently owned by root.  I am surprised that it has not caused more problems that you have seen; it could have locked you out of logging in to your user account, which I assume from what we have said so far is not the case.

Run command ```
sudo chown offir offir] /home/username/.gvfs
``` 
You could also look at ~/.cache/dconf to see who owns that with a right click on it in the file-manager; it shouls also be owned by you so if it is owned by root use a similar chown command  ```
sudo chown offir offir] /home/username/.cache/dconf
``` 
Have you ever used sudo to start a GUI application; that could explain why some of your home folders are now owned by root.  If you have you should not do so again but use either **gksudo**, which you will need to install first with the package **gksu**, or use ```
sudo -H <aplication>
```as they will retain the user ownership of everything in home.

Having got this sorted let's see if the space problem is overcome; I suspect it might be coincidental but we need to get this right first.

---

### Post by offir on 2016-01-15
> You certainly need to take ownership of that .gvfs folder which is currently owned by root. I am surprised that it has not caused more problems that you have seen; it could have locked you out of logging in to your user account, which I assume from what we have said so far is not the case.

Run command


```
sudo chown offir offir] /home/username/.gvfs

```


i try it
and get this message

```
chown: cannot access ‘offir]’: No such file or directory
chown: cannot access ‘/home/username/.gvfs’: No such file or directory
```

i try this as well
```
sudo chown offir offir] /home/offir/.gvfs
```

got this message
```
chown: cannot access ‘offir]’: No such file or directory

```








> You could also look at ~/.cache/dconf to see who owns that with a right click on it in the file-manager; it shouls also be owned by you so if it is owned by root use a similar chown command

```

sudo chown offir offir] /home/username/.cache/dconf
```



i got this message
```
chown: cannot access ‘offir]’: No such file or directory

```

I have attached an Images









> Have you ever used sudo to start a GUI application; that could explain why some of your home folders are now owned by root. If you have you should not do so again but use either gksudo, which you will need to install first with the package gksu, or use

```
sudo -H <aplication>
```

as they will retain the user ownership of everything in home.

this is Already installed

---

### Post by blueridgedog on 2016-01-15
Wouldn't it be

```
sudo chown offir:offir /home/username/.gvfs
```

---

### Post by offir on 2016-01-16
> Wouldn't it be



```
sudo chown offir:offir /home/username/.gvfs

```


i try that too

```
chown: cannot access ‘/home/username/.gvfs’: No such file or directory

```



do i need to change username to offir ?

---

### Post by ajgreeny on 2016-01-16
Yes, you must use command ```
sudo chown offir:offir /home/offir/.gvfs
``` or alternatively to make sure everything belongs to you ```
sudo chown -R offir:offir /home/offir/
```

Sorry, I didn't notice that errant ] or the lack of the : in my first command; that's what you get for trying to type too fast.  I also should have realised that you might not have known to change my use of *username* to your own username, ie offir.  *My bad*

---

### Post by blueridgedog on 2016-01-16
Right...not "username", but use your username as suggested above.

---

### Post by offir on 2016-01-16
> Sorry, I didn't notice that errant ] or the lack of the : in my first command; that's what you get for trying to type too fast. I also should have realised that you might not have known to change my use of username to your own username, ie offir. My bad


There's no need to apologize

I still have to thank you for the help


```
sudo chown offir:offir /home/offir/.cache/dconf

```

```
sudo chown offir:offir /home/offir/.gvfs
```

it worked


The available space on the hard disk has not changed Since yesterday (did not fill up i mean)

---

