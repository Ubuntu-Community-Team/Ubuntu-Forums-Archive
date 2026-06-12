---
title: "Symbolic Link confusion"
date: 2013-03-31
forum: General Help
---

### Post by CaptainMark on 2013-03-31
I've been creating symlinks between my girlfriends and my home folders to save having the same holiday photos stored twice. I noticed when using the keyboard shortcut ctrl+shift and dragging photos (the gui way to create symlinks I'm told) the link icon appears briefly on the new copy of the photo, great, but then disappears after a few seconds leaving what looks like an actual photo not a link to my copy of the photo. The same result happens when using the terminal. I used ls -l to check and this what I get ```
mark@desktop ~/ $ ls -l /home/lorraine/Pictures/2013/03/total 2072
-rw-rw-r-- 1 lorraine lorraine  23046 Mar  9 21:16 09-03-2013 22:16:07.jpg
-rw-rw-r-- 1 lorraine lorraine 456094 Mar 29 12:31 29-03-2013 12:31:21.jpg
-rw-rw-rw- 1 lorraine lorraine 651321 Mar 30 21:34 30-03-2013 21:34:45.jpg
-rw-rw-rw- 1 lorraine lorraine 965786 Mar 30 21:35 30-03-2013 21:35:40.jpg

```When ls usually shows links instead of a filename like "file.jpg > /home/mark/Pictures/file.jpg"
I checked with the unlink command and unlink does seem to remove the symlink but however if I type ```
find ./ -type l
``` I get no results shown, meaning none of these photos are links.

I guess what I'm asking is: are these links are they actual photos, taking up more space still.

Is it possible that because the files are still cached somewhere then they are just being restored when I'm attempting to create link, 
This is weird

Regards 
Mark

EDIT: If I run ls -l in the few seconds before the link icon disappears then ls shows as links as I was expecting

---

### Post by Impavidus on 2013-03-31
These are actual files, not symlinks, nor hardlinks, so they do use disk space.

---

### Post by rnerwein on 2013-03-31
hi
i think here is an example for that what you want.
in my home folder /home/richi/tmp is a file named: blablu
1. i cd to /home/testuser/tmp
2. run: ln -s /home/richi/tmp/blablu blablu
3. that gives me: ls -l blablu ---> lrwxrwxrwx 1 root richi 22 Mär 31 19:41 blablu -> /home/richi/tmp/blablu (on [COLOR=#ff0000]l[/COLOR]rwx.... you see it's a symbolic link)
4. if it is the same partition you can use although a hard link. ln /home/richi/tmp/blablu blubla
5. now ls -l blubla gives you: ls -l blubla -->[COLOR=#ff0000] 8208405[/COLOR] -rw-rw-r-- 2 richi richi 27 Mär 31 19:39 blubla
6. now cd back to your (my is richi) home e.g.: cd ~/tmp
7. ls -li blablu --> [COLOR=#ff0000]8208405[/COLOR] -rw-rw-r-- 2 richi richi 27 Mär 31 19:39 blablu
as you see: the names are different, but the inode is the same.
ok ?!
happy easter
ciao

---

### Post by sudodus on 2013-03-31
Check what you have in your home directory! For example, do you have a copy of this first file?

```
mark@desktop ~/ $ ls -l /home/lorraine/Pictures/2013/03/

total 2072 -rw-rw-r-- 1 lorraine lorraine  23046 Mar  9 21:16 09-03-2013 22:16:07.jpg
```

Use this command to find all files with the name '22:16:07.jpg' in everybody's home directories (except root and hidden directories)

```
sudo find /home/*/* -name '22:16:07.jpg -exec ls -l {} \;'
```

If you don't have any such file, your linking failed, but if you have something like this
```
lrwxrwxrwx  1 mark mark     34 Mar 31 19:56 /home/mark/Pictures/22:16:07.jpg -> /home/lorraine/Pictures/2013/03/22:16:07.jpg
```
you have a symbolic link in your directory

---

### Post by SuaSwe on 2013-03-31
Looks like the GUI has created copies of your files named after the copy time. :) If I were you I'd just remove the copies you've created and start again. To create a symlink of source directory from the lorraine location to an equivalent mark location, do:

```

mark@desktop:~$ mkdir -p ~/Pictures/2013/03/
mark@desktop:~$ ln -s /home/lorraine/Pictures/2013/03/total ~/Pictures/2013/03/total
mark@desktop:~$ ls -l ~/Pictures/2013/03/total     # should now look like:
lrwxrwxrwx 1 mark mark 8 Mar 31 19:14 ~/Pictures/2013/03/total -> /home/lorraine/Pictures/2013/03/total/

```

---

### Post by CaptainMark on 2013-03-31
The files are named after creation time and that doesn't seem to change, but rather than getting less confused I'm getting more confused
Okay here's where it gets really interesting, to test that it was not my simply misunderstanding symlinks I ran 2 tests, I ran essentially exactly the same commands from my user and then from my girlfriends user (in cli this time) and they bring about different results, the earlier explained "weirdness" only happens when running as user lorraine, see below.
running as user mark:```
mark@desktop ~/ $ ls -l /home/mark/Pictures/2013/03/
total 2544
-rw-rw-r-- 1 mark mark 530178 Mar 12 16:39 12-03-2013 16:39:09.jpg
-rw-rw-r-- 1 mark mark 295489 Mar 25 08:53 25-03-2013 08:53:26.jpg
-rw-rw-r-- 1 mark mark 725190 Mar 25 08:53 25-03-2013 08:53:32.jpg
-rw-rw-r-- 1 mark mark 365272 Mar 25 08:54 25-03-2013 08:54:21.jpg
-rw-rw-r-- 1 mark mark 651321 Mar 30 21:34 30-03-2013 21:34:45.jpg
mark@desktop ~/ $ ls -l /home/lorraine/Pictures/2013/03/
total 480
-rw-rw-r-- 1 lorraine lorraine  23046 Mar  9 21:16 09-03-2013 22:16:07.jpg
-rw-rw-r-- 1 lorraine lorraine 456094 Mar 29 12:31 29-03-2013 12:31:21.jpg
mark@desktop ~/ $ sudo ln -s /home/mark/Pictures/2013/03/30-03-2013\ 21\:34\:45.jpg /home/lorraine/Pictures/2013/03/30-03-2013\ 21\:34\:45.jpg
[sudo] password for mark: 
mark@desktop ~/ $ ls -l /home/lorraine/Pictures/2013/03/
total 480
-rw-rw-r-- 1 lorraine lorraine  23046 Mar  9 21:16 09-03-2013 22:16:07.jpg
-rw-rw-r-- 1 lorraine lorraine 456094 Mar 29 12:31 29-03-2013 12:31:21.jpg
lrwxrwxrwx 1 root     root         51 Mar 31 21:16 30-03-2013 21:34:45.jpg -> /home/mark/Pictures/2013/03/30-03-2013 21:34:45.jpg
```Then I deleted the link I just made and then running as user lorraine:```
lorraine@desktop ~ $ ls -l /home/mark/Pictures/2013/03/
total 3492
-rw-rw-r-- 1 mark mark 530178 Mar 12 16:39 12-03-2013 16:39:09.jpg
-rw-rw-r-- 1 mark mark 295489 Mar 25 08:53 25-03-2013 08:53:26.jpg
-rw-rw-r-- 1 mark mark 725190 Mar 25 08:53 25-03-2013 08:53:32.jpg
-rw-rw-r-- 1 mark mark 365272 Mar 25 08:54 25-03-2013 08:54:21.jpg
-rw-rw-r-- 1 mark mark 651321 Mar 30 21:34 30-03-2013 21:34:45.jpg
lorraine@desktop ~ $ ls -l /home/lorraine/Pictures/2013/03/
total 480
-rw-rw-r-- 1 lorraine lorraine  23046 Mar  9 21:16 09-03-2013 22:16:07.jpg
-rw-rw-r-- 1 lorraine lorraine 456094 Mar 29 12:31 29-03-2013 12:31:21.jpg
lorraine@desktop ~ $ ln -s /home/mark/Pictures/2013/03/30-03-2013\ 21\:34\:45.jpg /home/lorraine/Pictures/2013/03/30-03-2013\ 21\:34\:45.jpg
lorraine@desktop ~ $ ls -l /home/lorraine/Pictures/2013/03/
total 1124
-rw-rw-r-- 1 lorraine lorraine  23046 Mar  9 21:16 09-03-2013 22:16:07.jpg
-rw-rw-r-- 1 lorraine lorraine 456094 Mar 29 12:31 29-03-2013 12:31:21.jpg
-rw-rw-r-- 1 lorraine lorraine 651321 Mar 30 21:34 30-03-2013 21:34:45.jpg
```The only difference is the need to use sudo to write to another users directory when running as mark.

Can anybody see sense here, as far as I'm aware these codes should yield the same final result

---

### Post by schragge on 2013-03-31
Try verbose action: *ln -sv*. And you can omit the file name if it should stay the same:
```
lorraine@desktop ~ $ ln -sv /home/mark/Pictures/2013/03/30-03-2013\ 21\:34\:45.jpg /home/lorraine/Pictures/2013/03/
```
I'd even run it like this:
```
lorraine@desktop ~ $ ln -sv {~mark,~}/Pictures/2013/03/'30-03-2013 21:34:45.jpg'
```

What filesystem are your home directories located on? Is it NTFS?

---

### Post by SuaSwe on 2013-03-31
So to reiterate, the ln -s commands you've run in both instances are identical, creating a symlink from the original file 21:34:45.jpg in your Pictures subdir to an identical file in Lorraine's Pictures subdir. When you create it as your user using sudo, a symlink is created; when created as lorraine, what looks like a regular file is created.

Out of interest, can you open the 21:34:45.jpg file created in Lorraine's home directory after creating it as per the second example? Technically she should not have sufficient permissions to link from your home directory (unless you are making use of admin groups that she is part of and you are not); I'm wondering if this is why no symlink is created. 

Also, is there any reason why you are not linking to the entire directory rather than individual files? I would think that would be easier in the long-run. :)

---

### Post by schragge on 2013-03-31
> **SuaSwe said:**
> Technically she should not have sufficient permissions to link from your home directory (unless you are making use of admin groups that she is part of and you are not)Now, I'm confused, too. Why shouldn't she? AFAICS, she can read files in mark's directory.

---

### Post by sudodus on 2013-03-31
This looks like a bug to me. I can create symlinks without sudo (I did it before posting my previous post). What system and version are you running?

Would you mind checking hard links? Since your home directories are on the same partition, you can use hard links (which actually means two equal pointers to the same inode, where the data is sitting). The second column in the output of ls -l should be 2 showing that there are 2 links. You can check with ```
du
``` that the disk used will not increase with hard links.

Hard links are created with ```
ln orig link
``` without any option, and I don't think they can be created with GUI file browsers.

---

### Post by nothingspecial on 2013-03-31
I would use a completely different "data" partition for shared directories.

On the other hand, having 2 copies of your photos is not a bad idea.

---

### Post by sudodus on 2013-03-31
> **SuaSwe said:**
> ...
Also, is there any reason why you are not linking to the entire directory rather than individual files? I would think that would be easier in the long-run. :)
+1
I agree. You need not link each file.

It can be a good idea to have already compressed files, typically photos and multimedia files in a separate partition with access for both of you. And then you can have soft links in your home directories to that partition unless you find it convenient enough to access it via the partition icon in the file browser.

This means that you can have different methods for backup of the system partition and the photos and multimedia partition.

---

### Post by sudodus on 2013-03-31
> **nothingspecial said:**
> I would use a completely different "data" partition for shared directories.

On the other hand, having 2 copies of your photos is not a bad idea.
+1
but the 2 copies should be in different partitions, or better, different drives, or even better different houses.

---

### Post by CaptainMark on 2013-04-01
> **SuaSwe said:**
> Also, is there any reason why you are not linking to the entire directory rather than individual files? I would think that would be easier in the long-run. :)
Yes because her 2013/03 directory contains photos I don't want in my home folder, likewise she only wants some photos not all of them, I have a separate home partition but I'd rather not have each user on a different partition, and I have plenty of back-ups and back-ups of my back-ups.

Anyway, Last night I'be been on the #bash irc channel and got some help from some very helpful individuals, The chat can be found as an attachment for future reference.
In short they helped me use strace to detect what the command was doing and it seemed that the symlink was being created without error but then some other process is changing the link to an actual file after a few seconds, but didn't know what kind of process would do that.
I've racked my brains trying to figure out what would do that and tried un-installing loads of different programs to see if they were causing it, I gave up and went to bed but then it just came to me in the morning (perhaps I was dreaming about it :P) Dropbox, it's monitoring my Pictures directory for online syncing

I don't know why or how, I'm pretty sure it shouldn't but the Dropbox daemon is changing all my symlinks to actual files IF the file is a .jpg it doesn't happen to any other file types, and it doesn't happen outside my monitored folders, as a final check I killed the Dropbox daemon and tried again and the links work exactly as expected.

I have no know workaround yet, but at least I have the cause covered, now onto the Dropbox website to report a bug.

Many thanks for trying to help me all

---

### Post by sudodus on 2013-04-01
A bug it was, but far from what I had expected. You had a very bright dream :KS

You can use ***hard links*** as work-around. I don't think Dropbox would change them too, but you'd better check ;-)

---

### Post by CaptainMark on 2013-04-01
Surprisingly hard links are just the same, unfortunately anyway it's not a viable work around for me in this situation as I need something that she can do on her own without my interaction, she okay with browsing my files via gui and dragging over the ones she wants whilst holding ctrl + shift but any terminal work or user privileges is not going to work for her.

I've emailed Dropbox and shall report back when/if I hear anything, I don't see why they wont recognise it as a bug as I've used their recommended method for linking directories outside of the Dropbox folder, but I'm half expecting a short email saying, "Dropbox doesn't support symlinking so stop bothering me" even though we all know that this shouldn't happen, you know what these large companies get like when you ask about Linux features

---

### Post by schragge on 2013-04-01
You may want to have a look at [this](http://aurelio.net/articles/dropbox-symlinks.html).

---

### Post by CaptainMark on 2013-04-01
Yeah this isn't really applicable, I'd be happy if dropbox just followed the symlinks to their destinations like this blog says but unfortunately this isnt whats happening here, dropbox is deleting symlinks and replacing them with the content at their destination, so it definitely still is a bug but I expect the Dropbox support staff will not bother looking into the issue after seeing "linux" and "symlinks" they will just give up without investigating

---

### Post by Impavidus on 2013-04-01
As a side note:
> **CaptainMark said:**
> 
...
```

mark@desktop ~/ $ sudo ln -s /home/mark/Pictures/2013/03/30-03-2013\ 21\:34\:45.jpg /home/lorraine/Pictures/2013/03/30-03-2013\ 21\:34\:45.jpg
[sudo] password for mark: 
mark@desktop ~/ $ ls -l /home/lorraine/Pictures/2013/03/
total 480
-rw-rw-r-- 1 lorraine lorraine  23046 Mar  9 21:16 09-03-2013 22:16:07.jpg
-rw-rw-r-- 1 lorraine lorraine 456094 Mar 29 12:31 29-03-2013 12:31:21.jpg
lrwxrwxrwx 1 [COLOR=#ff0000]root     root[/COLOR]         51 Mar 31 21:16 30-03-2013 21:34:45.jpg -> /home/mark/Pictures/2013/03/30-03-2013 21:34:45.jpg
```
...

This creates a symlink owned by root, which is not very convenient and needs to be fixed with a **sudo chown**. Instead you could use```

mark@desktop ~/ $ sudo [COLOR=#ff0000]-u lorraine[/COLOR] ln -s /home/mark/Pictures/2013/03/30-03-2013\  21\:34\:45.jpg /home/lorraine/Pictures/2013/03/30-03-2013\  21\:34\:45.jpg
[sudo] password for mark: 
mark@desktop ~/ $ ls -l /home/lorraine/Pictures/2013/03/
total 480
-rw-rw-r-- 1 lorraine lorraine  23046 Mar  9 21:16 09-03-2013 22:16:07.jpg
-rw-rw-r-- 1 lorraine lorraine 456094 Mar 29 12:31 29-03-2013 12:31:21.jpg
lrwxrwxrwx 1 [COLOR=#ff0000]lorraine lorraine[/COLOR]     51 Mar 31 21:16 30-03-2013  21:34:45.jpg -> /home/mark/Pictures/2013/03/30-03-2013  21:34:45.jpg
```
**sudo** stands for switch user do. It defaults to root, but you can use a different user.

---

