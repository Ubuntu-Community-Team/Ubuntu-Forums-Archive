---
title: "How  do I change permissions on a folder safely?"
date: 2020-12-28
forum: General Help
---

### Post by Sour Mash on 2020-12-28
I've got a bunch of folders in my Downloads folder that I can't delete due to permissions - I was running some data recovery jobs to try and salvage a dead drive, it sort of worked and I got what I needed but it's left me with many folders and files that I now don't have permission to delete :-(
They are all useless to me now and just taking up space but I can't figure out how to fix - when I search for a solution I just find lots of posts by people who have got into problems changing permissions - as I am prone to screwing things up, I though I'd ask first :-)
So, what's the idiot proof way to delete 15 folders in my Downloads folder please? 

Thanks

J

---

### Post by mikewhatever on 2020-12-28
Not sure what you mean by safely, but try the following:
```
sudo chown -R $USER ~/Downloads
```

That should change the ownership of all files and folders in ~/Downloads recursively to your user.

---

### Post by #&amp;thj^% on 2020-12-28
if it were me i'd first move the files you want to keep, to a different location. (For safety)
First get an idea of what's there 
```
cd Downloads && ls -al
```
Will show you all with permissions.
*****After you moved all you want to keeep*****
Run:
```
sudo rm -rf *

```
Check again with:
```
cd Downloads && ls -al
```
EDIT: Example of mine:
```
cd Downloads && ls -al
total 107980
drwxr-xr-x  4 me me     4096 Dec 26 15:02  .
drwxr-xr-x 27 me me     4096 Dec 28 09:37  ..
-rw-rw-r--  1 me me    55548 Dec 22 15:35 'disper_0.3.1-2_all(1).deb'
-rw-rw-r--  1 me me    55548 Dec 22 15:25  disper_0.3.1-2_all.deb
-rw-rw-r--  1 me me  3444836 Dec 22 09:36  eddie-ui_2.18.9_linux_x64_debian.deb
-rw-rw-r--  1 me me  2555788 Dec 26 09:41  makemkv-oss_1.15.3-2~focal_amd64.deb
-rw-rw-r--  1 me me   108154 Dec 26 15:02  maldet.pdf
drwxrwxr-x  2 me me     4096 Dec 26 13:12  mps
drwxrwxr-x  4 me me     4096 Dec 23 07:26  ovpn
-rw-rw-r--  1 me me 26517079 Dec 22 09:22  ovpn.zip
-rw-rw-r--  1 me me 72246324 Dec 19 10:24  pia-linux-2.6.1-05824.run
-rw-rw-r--  1 me me  2407184 Dec 19 12:33 'Screenshot at 2020-12-19 12-33-52.png'
-rw-rw-r--  1 me me  2216114 Dec 19 13:59  Summer-Beta.tar.gz
-rw-rw-r--  1 me me    64102 Dec 19 14:03  summericon.png
-rw-rw-r--  1 me me     1770 Dec 22 15:33  ubuntu
-rw-rw-r--  1 me me   856132 Dec 26 12:04  wickr.png

```
After the remove:
```
$ cd Downloads && ls -al
total 8
drwxr-xr-x  2 me me 4096 Dec 28 11:25 .
drwxr-xr-x 27 me me 4096 Dec 28 09:37 ..

```
if I then move back my desired files/folders
```
me@me-ThinkPad-X1-Carbon-7th:~/Downloads$ ls -al
total 107980
drwxr-xr-x  4 me me     4096 Dec 28 11:49  .
drwxr-xr-x 27 me me     4096 Dec 28 09:37  ..
-rw-rw-r--  1 me me    55548 Dec 22 15:35 'disper_0.3.1-2_all(1).deb'
-rw-rw-r--  1 me me    55548 Dec 22 15:25  disper_0.3.1-2_all.deb
-rw-rw-r--  1 me me  3444836 Dec 22 09:36  eddie-ui_2.18.9_linux_x64_debian.deb
-rw-rw-r--  1 me me  2555788 Dec 26 09:41  makemkv-oss_1.15.3-2~focal_amd64.deb
-rw-rw-r--  1 me me   108154 Dec 26 15:02  maldet.pdf
drwxrwxr-x  2 me me     4096 Dec 26 13:12  mps
drwxrwxr-x  4 me me     4096 Dec 23 07:26  ovpn
-rw-rw-r--  1 me me 26517079 Dec 22 09:22  ovpn.zip
-rw-rw-r--  1 me me 72246324 Dec 19 10:24  pia-linux-2.6.1-05824.run
-rw-rw-r--  1 me me  2407184 Dec 19 12:33 'Screenshot at 2020-12-19 12-33-52.png'
-rw-rw-r--  1 me me  2216114 Dec 19 13:59  Summer-Beta.tar.gz
-rw-rw-r--  1 me me    64102 Dec 19 14:03  summericon.png
-rw-rw-r--  1 me me     1770 Dec 22 15:33  ubuntu
-rw-rw-r--  1 me me   856132 Dec 26 12:04  wickr.png

```
All is good...

---

### Post by tea for one on 2020-12-28
You do not need to change the permissions of the folder, you only need permission to delete them.

Open a terminal

```
cd Downloads
```

```
sudo rm -r [COLOR="#0000FF"]name_of_unwanted_folder[/COLOR]
```

---

### Post by Sour Mash on 2020-12-28
> **mikewhatever said:**
> Not sure what you mean by safely, but try the following:
```
sudo chown -R $USER ~/Downloads
```

That should change the ownership of all files and folders in ~/Downloads recursively to your user.

Thank you! That did the trick nice and simply, files deleted, order is restored, until the next time ;-)

---

### Post by Sour Mash on 2020-12-28
> **tea for one said:**
> You do not need to change the permissions of the folder, you only need permission to delete them.

Open a terminal

```
cd Downloads
```

```
sudo rm -r [COLOR="#0000FF"]name_of_unwanted_folder[/COLOR]
```

Thanks but I would have had to do that 15 times in order to delete them all, so I was looking for a more efficient way

---

### Post by Sour Mash on 2020-12-28
Thanks for that, seemed like a cautious but lengthy way of doing it although I do appreciate the guidance.

---

### Post by tea for one on 2020-12-28
> **Sour Mash said:**
> Thanks but I would have had to do that 15 times in order to delete them all, so I was looking for a more efficient way

Not really.

I simply assumed that you would know that you can delete multiple folders in one command.

Perhaps, I should have been more precise:-

```
sudo rm -r [COLOR="#0000FF"]name_of_unwanted_folder01[/COLOR] [COLOR="#008000"]name_of_unwanted_folder02[/COLOR] [COLOR="#FF0000"]name_of_unwanted_folder03[/COLOR] etc
```

---

### Post by TheFu on 2020-12-28
Mostly OT, but maybe not ...

Filename globbing is very powerful:
```
sudo rm -r name_of_unwanted_folder01 name_of_unwanted_folder02 name_of_unwanted_folder03 
```
can be said as 
```
sudo rm -r name_*
```

If you want to be more cautious, 
```
sudo rm -r name_of_unwanted_folder0?
```

[LIST]
[*]* says to match any number of any type of characters, including zero.
[*]? says to match any single character of any type. 1 character matching is required.
[/LIST]

We can match using "*something*" patterns or "*0[123]" patterns to match *01, *02, *03.

There are many other pattern matching patterns and we don't need to be limited to what we may have learned from other OSes.  For example, extensions are not important. Linux doesn't actually care about them.  In another OS, we've been taught  *.txt as a pattern.  In Unix, the '.' is another way to say "any character".  To match on the actual period, a '\.' is needed.

Creating sort, efficient, patterns is a very useful skill.

---

### Post by Impavidus on 2020-12-29
> **TheFu said:**
> 
If you want to be more cautious, 
```
sudo rm -r name_of_unwanted_folder0?
```

[LIST]
[*]* says to match any number of any type of characters, including zero. 
[*]? says to match any single character of any type. 1 character matching is required. 
[/LIST]

We can match using "*something*" patterns or "*0[123]" patterns to match *01, *02, *03.


Another useful one is```
sudo rm -r name_of_unwanted_folder{01..03}
```which will expand to the same if you've got those three folders.
You can experiment with those globs if you use them as the argument of echo:```
echo *something*
echo {1..3}-foo-{01..04}
```

---

