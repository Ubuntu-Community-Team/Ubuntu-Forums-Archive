---
title: "Clarification with one small thing in AutoFS"
date: 2016-02-13
forum: General Help
---

### Post by Roasted on 2016-02-13
Hello friends. I've been tinkering with AutoFS lately on my systems at home. I'm finding it's quite excellent. I have it auto mounting my CIFS/Samba shares from my server (Ubuntu Server 14.04), which just acts as a large data storage point as most of our systems run smaller SSDs (because price + speed). On top of that, it provides surprising speeds given it's basically mounting the shares via terminal instead of gvfs. I suppose it's cutting out some overhead and streamlining things a bit. (I'm talking to the tune of gvfs 13 MB/s average, autofs 22 MB/s average pulling the same ISO from server to laptop over wireless - nice!)

There's one thing in particular I'm curious about. Just know that everything seemingly works, so this is curiosity more than anything. In the example command I was provided that I tailored to match my needs using my own mount point, IP to server, etc etc., there's a wildcard used in the one path. Here are my files:

auto.master:
```
#
******* This area was snipped because it is many lines and I changed nothing in the default auto.master except the last two lines below *******
#
+auto.master
/media/jason/NAS /etc/auto.smb.nas.jason --timeout=60 --ghost
/media/jason/web /etc/auto.smb.web.jason --timeout=60 --ghost
```

auto.smb.nas.jason (auto.smb.web.jason is identical except different IP):
```
* -fstype=cifs,rw,credentials=/etc/.smbcredentials,uid=1000,gid=1000,file_mode=0700,dir_mode=0600,forceuid,forcegid ://192.168.1.20/&
```

Then of course /etc/.smbcredentials just contained username=username, password=password, and domain=workgroup (all on separate lines), owned by root:root with 660 permissions.

What I'm most curious about is the wildcard used in the -fstype line. I see in the man page:

```
Wildcard Key
A map key of * denotes a wild-card entry. This entry is consulted if the specified key does not exist in the map. A typical wild-card entry looks like this:

    *    server:/export/home/&

The special character '&' will be replaced by the provided key. So, in the example above, a lookup for the key 'foo' would yield a mount of server:/export/home/foo. 
```

I'm curious if using a wildcard is safe, or advised? I figured if it's in the man page, I assume it provides some degree of purpose, but what features are available vs what's recommended could be two different things. I'm also having trouble understanding what "specified key" I would need to provide in the event I didn't want to use a wild card in that line.

Secondly, for bonus points I'm curious why /& is needed at the end of the IP address in auto.master. I tried without just to see what would happen but it errored out.

Overall I'm mostly curious about the functional purpose behind * in use with -fstype and /& in use at the end of the IP of auto.master. Thanks for any insight!

---

### Post by TheFu on 2016-02-13
I dunno, but could it be that those 2 characters are the replacements for what is mounted and where it is mounted?

I've never used either, but if you look at the documentation about mounting home directories with wildcards here ... [https://help.ubuntu.com/community/Autofs#Wildcard_characters](https://help.ubuntu.com/community/Autofs#Wildcard_characters) that explains.

Also, autofs has ZERO to do with performance of the transfers. That is the difference between NFS and CIFS.  autofs just handles the mount/umount stuff and passes any options to the tool that does the real work.

---

### Post by Roasted on 2016-02-13
> **TheFu said:**
> I dunno, but could it be that those 2 characters are the replacements for what is mounted and where it is mounted?

I've never used either, but if you look at the documentation about mounting home directories with wildcards here ... [https://help.ubuntu.com/community/Autofs#Wildcard_characters](https://help.ubuntu.com/community/Autofs#Wildcard_characters) that explains.

Also, autofs has ZERO to do with performance of the transfers. That is the difference between NFS and CIFS.  autofs just handles the mount/umount stuff and passes any options to the tool that does the real work.

Oh I understand. The catch is, I was using gvfs with samba/cifs and I'm using autofs with samba/cifs, yet there's a massive difference in speed in between. That's what I was comparing. I figured autofs would be faster with it mounting via terminal, which admittedly seems to remove some overhead that gvfs otherwise provides. I just thought the difference was bigger than I anticipated.

I'll look through the docs there and see. All I know is, without those particular characters, I can't get autofs to work -- which is fine, I was just curious about those components in particular and how they operate. :D

---

### Post by TheFu on 2016-02-13
gvfs has a place ... on other people's systems. Not on mine. 

They aren't "real mounts".  The don't go where I want them and they are per-user.  Every release, the gvfs people learn something new (security-wise) and decide to move where the temporary storage gets placed. This ripples throughout all the GUIs. Yuk. Mounts are meant to be machine to machine, IMHO and should be seen by the file system, not just inside some damn GUI tool.  gvfs is my last choice when there are other options (and there always are).

NFS/fstab
autofs
sshfs
..
..
..
..
samba
..
..
..
..
gvfs

That's my order of preference. Put it into the "don't use it unless I have to" category.  I should say, that I'm old and crotchety - things should work like the old things they are trying to better - at least they should try.  Just for fun, mount something with gvfs then run 'mount' and 'df' at the command prompt. Why aren't gvfs mounts shown?  Why not?  BECAUSE THEY AREN'T REALLY MOUNTS!!!

---

### Post by keithspg on 2016-11-18
Yes, I agree! gvfs used to be useful, now it is more than useless with its convoluted link names. You used to be able to make a simple link to the .gvfs folder to make it 'visible' in nautilus through reboots. I agree with 'The Fu', but using cli is for experienced users. I have 3 inexperienced users at home and they need to use the server file system (I have nfs and cifs set up on the server) and are sometimes on ethernet sometimes on wifi and sometimes not at home (laptops). Having a 'favorites' set up to mount the server folder in nautilus works great until you want to do something with a file on the server with a wine app. Or even if you want to browse photos in nautilus on the server. The GUI is great for being able to 'see' what is there to browse through a lot of files. It is also nice that when a user logs out, the gvfs mount disappears. 

Where do I post suggestions to the GVFS team. There is a wrapper for the wine executable which parses all of this that some guy wrote, but I do not know if it still works and it feels a bit of a kluge to wrap wine. Besides, when gvfs changes again, this will have to be modified again. Try to tell an inexperienced user that they need to copy the file locally to be able to edit it in Excel then save it back on the server in nautilus afterward if you want it saved on the server. You get strange looks and a lot of 'whys'. IMO, if the GVFS mounts showed up in a folder of the user root, that would be fine if it is 'parse-able' by wine apps and also would be easy to explain to a user that "when you browse the network and mount a network folder, it shows up here and you can then browse through it". I do not get that more people are not aggravated by the current behavior if GVFS. I will try autofs and see if it works, but it must be easy to use in nautilus for my users.

Keith

---

### Post by oldos2er on 2016-11-18
> Where do I post suggestions to the GVFS team. [https://wiki.gnome.org/Projects/gvfs](https://wiki.gnome.org/Projects/gvfs)

---

### Post by Roasted on 2016-11-18
> **keithspg said:**
> Yes, I agree! gvfs used to be useful, now it is more than useless with its convoluted link names. You used to be able to make a simple link to the .gvfs folder to make it 'visible' in nautilus through reboots. I agree with 'The Fu', but using cli is for experienced users. I have 3 inexperienced users at home and they need to use the server file system (I have nfs and cifs set up on the server) and are sometimes on ethernet sometimes on wifi and sometimes not at home (laptops). Having a 'favorites' set up to mount the server folder in nautilus works great until you want to do something with a file on the server with a wine app. Or even if you want to browse photos in nautilus on the server. The GUI is great for being able to 'see' what is there to browse through a lot of files. It is also nice that when a user logs out, the gvfs mount disappears. 

Where do I post suggestions to the GVFS team. There is a wrapper for the wine executable which parses all of this that some guy wrote, but I do not know if it still works and it feels a bit of a kluge to wrap wine. Besides, when gvfs changes again, this will have to be modified again. Try to tell an inexperienced user that they need to copy the file locally to be able to edit it in Excel then save it back on the server in nautilus afterward if you want it saved on the server. You get strange looks and a lot of 'whys'. IMO, if the GVFS mounts showed up in a folder of the user root, that would be fine if it is 'parse-able' by wine apps and also would be easy to explain to a user that "when you browse the network and mount a network folder, it shows up here and you can then browse through it". I do not get that more people are not aggravated by the current behavior if GVFS. I will try autofs and see if it works, but it must be easy to use in nautilus for my users.

Keith

I still like gvfs. There's no beating opening up Nautilus, CTRL L, punch in smb://ip.of.file.server, boom done. I dig it for that. You can bookmark those links to make it easier to access as well.

For systems that will be connecting to a network resource frequently (such as at home), autofs is the ticket. I have autofs mounting the main smb share to my file server at home (with rwx permissions controlling access to individual directories from there). It works well, very happy with it. It's graceful in terms of suspend, shut down, reboots of the wireless router, etc. Seems to do the job.

---

### Post by keithspg on 2016-11-18
Roasted,

I agree. Super easy and useful... except with wine programs. I know there are other programs out there, but MS Office is still the 'big dog' and though I do not advocate bowing to it, allowing it (and other wine apps) to access files and folders which are GVFS mounted would be a huge help. I do not feel this is a 'wine problem', but more a gvfs problem. Previously, all you needed to do was create a non-hidden link to the gvfs folder and it just worked. Now the mounting format and means has changed and IMO is broken. It appears to be a development of gvfs that broke it. 

Keith

---

### Post by Roasted on 2016-11-18
> **keithspg said:**
> Roasted,

I agree. Super easy and useful... except with wine programs. I know there are other programs out there, but MS Office is still the 'big dog' and though I do not advocate bowing to it, allowing it (and other wine apps) to access files and folders which are GVFS mounted would be a huge help. I do not feel this is a 'wine problem', but more a gvfs problem. Previously, all you needed to do was create a non-hidden link to the gvfs folder and it just worked. Now the mounting format and means has changed and IMO is broken. It appears to be a development of gvfs that broke it. 

Keith

Ah, I understand. Well, only way to find out. Fire up autofs and see. :) I'm very happy with it. I like how automated it is.

Couple examples:

--I have Clementine's "music" directory pointed to /media/jason/vault/NAS/music
--I have Shotwell's "picture" directory pointed to /media/jason/vault/NAS/pictures

Fire up Clementine -- boom, music, streaming over the LAN, with a really sweet interface and not some botched web interface as I've used in the past.
Kick on Shotwell -- pictures sync changes to acknowledge new/removed images, and bingo, I have 36,000 (or so) images in the Shotwell database.

Only downside to Shotwell is things like tags and merged events don't really work, as Shotwell stores those items locally in .shotwell-db or some file like that, so those changes don't sync to server. Works fine, but if my wife sets up a bunch of tags, she'll see them and continue to see them on her laptop -- I'll never see them, though. I had thoughts about symlinking the db to a location on the NAS (accessible via autofs), but I'm not sure I care about tags enough. Shotwell organizes things very nicely, so I can drill through year/month/day categories easily anyway. Maybe someday.

But anyway, yeah give it a shot. I've had a great experience with autofs. It was a little goofy to set up but once done, it's not bad. For example, I thought I had autofs set up wrong, including everything I was reading (including confirmation from a buddy who's a fluent autofs user) confirmed I had it set up right -- yet it wouldn't fly. The issue? First time firing it up, you have to manually put in the path within Nautilus, i.e. CTRL L, type in path manually once, and it works from then on -- bookmarking on the left nav with Nautilus as well.

Good luck!

---

