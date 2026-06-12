---
title: "No permission to access mounted SMB share (Ubuntu Linux"
date: 2017-04-16
forum: General Help
---

### Post by flemmingss on 2017-04-16
I am running a server with ubuntu server (the newest Long term release).
On the server I have installed plex media server, and the server i "up and running" (The local website works)
anyway, my mediafiles is not on this machine, they are on a SMB dataset share on my FreeNAS server witch run ZFS. //freenas/video

This is my permission setup on this share, as you can see all folders have the same setup:
[IMG]http://itpro.no/supportforum/uploads/monthly_2017_04/Uten_navn.png.c6e11927a8cfcb07fb8afa6e39d6af34.png[/IMG]
on my FreeNAS I have a user "plex" that are a member of the video_readonly group, because the user should have read only access. Screenshots to this is attatched to this post.

But even if the permissions looks ok and works in windows, i can't get them to work in linux:

```
flemmingss@plex:/mnt$ ls -la /mnt/videols: cannot open directory '/mnt/video': Permission denied
flemmingss@plex:/mnt$ ^C
flemmingss@plex:/mnt$ sudo ls -la /mnt/video
[sudo] password for flemmingss:
total 9
d---rwx---+  4 nobody 1001    0 Apr 10 23:13 .
drwxr-xr-x   5 root   root 4096 Apr 12 17:48 ..
----rwx---   1 root   1001  979 Apr 10 22:38 .config-smb-video.json
d---------  51 root   root    0 Apr 10 23:00 Filmer
d---------  49 root   root    0 Apr 11 01:07 Serier
flemmingss@plex:/mnt$
```
```
flemmingss@plex:/mnt$ sudo ls video/SerierAmerican Dad                          Dilbert                Man Show
Auction Kings                         Etaten                 Mantracker
Bobs.Burgers                          Family Guy             Mot I Brøstet sesong
Breaking Bad                          Folkeopplysningen      Penn & Teller - ********
Conspiracy Theory with Jesse Ventura  Futurama               Pimp My Ride
Cops                                  Helt Perfekt           Pokemon
Dag                                   Ice Road Truckers      Politiet
Dark Side Of Porn                     Ingen Grenser          Pro at Coocking
De 7 dødssyndene                      Kjetil & Kjartan Show  RAN
Den Unge Fleksnes                     Louis Theroux          Redd menig Osen
flemmingss@plex:/mnt$
```
[COLOR=#660066][/COLOR][COLOR=#000000]
flemmingss@plex[/COLOR][COLOR=#666600]:/[/COLOR][COLOR=#000000]mnt$[/COLOR][FONT=&amp]have also tried some of this: [https://ubuntuforums.org/showthread.php?t=2087341](https://ubuntuforums.org/showthread.php?t=2087341)[/FONT]
[FONT=&amp]**sudo gpasswd -a plex plugdev**[/FONT]
[FONT=&amp]no change[/FONT]
[FONT=&amp]**sudo gpasswd -a plex flemmingss** (min mine user on the ubuntu server)[/FONT]
[FONT=&amp]got access to  video\Filmer and video\Serier in Plex, but no more then that (no other folders or files.[/FONT]
[FONT=&amp]**sudo gpasswd -a plex root**[/FONT]
[FONT=&amp]no change.

[COLOR=#000000][/COLOR]```
[/FONT]flemmingss@plex:~$ cd /mnt/video-bash: cd: /mnt/video: Permission denied
flemmingss@plex:~$ sudo ls -l /mnt/video/
total 0
d--------- 51 flemmingss flemmingss 0 Apr 10 23:00 Filmer
d--------- 49 flemmingss flemmingss 0 Apr 11 01:07 Serier
flemmingss@plex:~$ sudo ls -l /mnt/
total 8
drwxr-xr-x  2 root       root       4096 Apr  9 00:11 cdrom
drwxr-xr-x  2 root       root       4096 Apr 11 19:12 samba
d---rwx---+ 4 flemmingss flemmingss    0 Apr 10 23:13 video
flemmingss@plex:~$
flemmingss@plex:/$ sudo ls -l /mnt/video/Serier
total 0
d--------- 10 flemmingss flemmingss 0 Apr  9 21:45 American Dad
d---------  3 flemmingss flemmingss 0 Apr  9 21:32 Auction Kings
d---------  4 flemmingss flemmingss 0 Apr  9 21:50 Bobs.Burgers
d---------  5 flemmingss flemmingss 0 Apr  9 21:59 Breaking Bad
d---------  5 flemmingss flemmingss 0 Apr  9 22:11 Conspiracy Theory with Jesse Ventura
d--------- 27 flemmingss flemmingss 0 Apr  9 23:07 Cops

d---------  3 flemmingss flemmingss 0 Apr  9 23:10 Dag[FONT=&amp]
```
[COLOR=#660066][/COLOR]
my /etc/fstab looks like this:

**//192.168.1.119/video  /mnt/video  cifs  iocharset=utf8,credentials=/home/flemmingss/.smbcredentials,sec=ntlm,uid=1000,gid=1000  0  0**
(but I have tried many combinations of changes in this files, all seems to give the same results)
[/FONT]


[B]Users Summary:
Freemnas:[/B]
plex is member of the group video_readonly with have read only access to /video/ dataset

**Ubuntu:**
plex is the user created and used by Plex Media Server
flemmingss is my default user.

Also, I am not really used to linux, only using it for server stuff because a whole window install for something like this is a waste of resources

---

### Post by flemmingss on 2017-04-17
bumping this

---

### Post by flemmingss on 2017-04-25
[COLOR=#000000]bumping this[/COLOR]

---

### Post by flemmingss on 2017-04-30
bumping this

---

### Post by flemmingss on 2017-05-07
[COLOR=#000000]bumping this[/COLOR]

---

### Post by flemmingss on 2017-05-14
[COLOR=#000000]bumping this[/COLOR]

---

