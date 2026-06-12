---
title: "Server newbie with silly questions"
date: 2020-12-08
forum: General Help
---

### Post by frank105 on 2020-12-08
I setup a small practice server at my house to learn a few things and to install Plex server to serve my collection of media to a couple of Firesticks and tablets running Plex player.    

From my ubuntu laptop - I ssh into the server and am running commands.  

```
sudo rsync --progress --recursive /mnt/ROSI/Kodi_Media/Music /mnt/HAMMER/Kodi_Media/
```

So in this example command I am using rsync to create a backup of my Music from one external usb drive to a second usb drive - that doesn't have any of the files at all.  I like the "--progress" as I learn to get a feel for how long this is going to take and when/if it hits a problem.
(ROSI is going to be the primary storage drive.  HAMMER is going to be the offline "mirror" of ROSI) 

[LIST=1]
[*]Can I shutdown my laptop and go to bed while it does this?  I guess that would crash ssh and would that crash the copy?  (I think so).  Reading between the lines in a bunch of studying there seems to be a way to do this all 1 more level removed and then "log back into" the process when I want to?  Sadly I don't even know the right terms to describe this to even do a good search.  I need to learn a lot.
[*]Is rsync the best way to occasionally update a backup of my media files?  I used: ```
sudo cp -vaR /mnt/ROSI/‘Audio Books’ /mnt/HAMMER
```…and backed up my audio books but after reading about rsync this may not have been the best way?  Pointers on best practice for only backing up new media would be appreciated. 
[*]Once I get this all setup and the drives are identical - then would I just be able to issue one command like: ```
sudo rsync --recursive /mnt/ROSI /mnt/HAMMER
```…and the drives would match back up?
[*]To make Plex happy I edited fstab to mount these drives by the UUID.  But now if I boot the server without the backup drive "HAMMER" powered on the server fails to boot because it can't find the drive.  What is the best way to solve this?  I am currently reading up on autofs but not sure this is the best way. 
[/LIST]
Anyway - thanks in advance for any tips, tricks or solutions!

Regards,
Frank.

---

### Post by DuckHook on 2020-12-08
*Thread moved to **General Help** as the more appropriate forum.*

Though you are asking about a "server" issue, the *Servers, Cloud, Juju* forum tends to be visited less often and your issue is actually a general one. I thought you would have more luck with an answer here.

---

### Post by frank105 on 2020-12-08
Thanks!

---

### Post by CatKiller on 2020-12-08
> **frank105 said:**
> Can I shutdown my laptop and go to bed while it does this?  I guess that would crash ssh and would that crash the copy?  (I think so).  Reading between the lines in a bunch of studying there seems to be a way to do this all 1 more level removed and then "log back into" the process when I want to?  Sadly I don't even know the right terms to describe this to even do a good search.  I need to learn a lot.
You are correct that if you're running a command directly through an SSH session from a different machine, shutting down that machine will kill the SSH session, which will kill the command. A straightforward way to do this is to use **screen**.

You'd connect through SSH, then run your command through screen. You can then "detach" from screen, which will leave the command running. Then you can close your SSH session and shut down your laptop. When the command finishes, screen will terminate. You can also "re-attach" to screen while it's running, from the same machine or a different one. It's quite handy.

---

### Post by The Cog on 2020-12-08
Screen creates an in-memory virtual screen for the commands to run in. So yes, run screen and it then gives you a new command prompt. If the ssh connection to screen gets detached for any reason, screen and the command process (or processes, screen can run and switch between several command prompts) continue running. You can detach with Ctrl-A D, or break the ssh connection somehow like shutting down the laptop or pulling the network cable and the command sin screen just carry on. Reconnect to screen ("screen -r") at your convenience. There are plenty of tutorials on using screen on the internet. 

"It's quite handy" is an understatement.
There's a very similar one called tmux, which has a few more features but the built-in help screen is horrible. Screen is probably better to start with.

---

### Post by TheFu on 2020-12-08
It is possible to detach processes from the login-bash shell too without using screen.  I do it all-the-time.

rsync is in my list of top-5 commands for Unix people. It is really very useful, but it depends on which file system the source and target are using, whether parts of the storage are local and/or remote, and which userid is being used to run the command. For non-native storage file systems, all sorts of things break, like permissions, owners, groups, ACLs, xattrs, so using sudo isn't actually useful, unless that storage was mounted incorrectly.

rsync is actually faster when at least 1 of the disks is remote.  Different block checking is used when remote storage is involve than when it is all local, at least after the 1st sync.  Obviously, the first time a huge set of files gets sync'd between storage, all those files have to be copied.  But for all the times after the first time, only the diffs get sent.

BTW, rsync doesn't delete anything in the target storage, so if you want that to happen, there are multiple, different --delete options. If you have lots of storage available, --delete-after is safest.  If you barely have enough storage, then --delete-before will make room first, but it is bad for backups, since for a little bit, that 1st copy of many deleted files in the mirror do not exist.

And Plex doesn't like it when storage in a library isn't available.  Don't tell your Plex system about the backup storage. Just .... don't.

I mirror plex media files a few times a week.  These are local storage on the same system:
```
ionice rsync -av --stats --progress $EXCLUDES --delete /d/D1/ /d/b-D3/
ionice rsync -av --stats --progress $EXCLUDES --delete /d/D2/ /d/b-D4/
ionice rsync -av --stats --progress $EXCLUDES --delete /d/D3/ /d/b-D5/
```
Note that I do NOT use sudo.  All the storage uses ext4 as the file system sitting on some enterprise logical volume management storage, LVM, but for rsync, typical partitions are fine for the file systems.

```
$ ls -l /d/D1/M
drwxrw[COLOR="#FF0000"]s[/COLOR]--- 1297 tf   plex 61440 Dec  4 18:53 M/
```

I'm the owner.
plex is the group.
Note the group permissions with the setgid bit set. Because plex (the group) has rwx+s access, I don't have to leave permissions open for "other" at all.  For stuff that only gets played via plex, this is fine.  But for Music and photos which have other players/organizers, I leave the permissions for "other" as r-x.

I strive NOT to use ACLs, but some people love the confusion they can bring.  Once I lost 2 days trying to figure out why I couldn't read a file where I clearly had permissions to read access. Turned out my boss was playing around with ACLs and had removed access by my userid specifically.  Stuff like this is fun for hacking contests, but just causes issues in enterprise use.

Hopefully, I didn't add more questions than were answered. Hopefully.

---

### Post by CatKiller on 2020-12-08
> **The Cog said:**
> "It's quite handy" is an understatement.
&#128522;

Another very useful feature is that you can create named screens. So, as an example, my scripts that start Minecraft servers do so in named screens so that I can SSH to that machine from anywhere (my phone, usually) and attach to the particular instance that I want to administer and then simply detach after I'm done.

---

### Post by frank105 on 2020-12-08
Excellent!!  That is what I was looking for!!  

It is amazing how much info you can find if only I had just the smallest idea where to start!!

Okay - I have successfully used screen, detached, named, reattached a couple of times and it worked GREAT.  

But it will take me a little bit to digest the rsync intel.  I did run a  large folder through rsync and it worked great. Speedy too.  But I  think I need to slow down and identify my long term strategy.  File  formats, which drive should be lead/backup and deleting??  Never thought  about deleting but got to have a plan.  I will do some thinking and  post a few more thought questions after but I really wanted to get my  THANKS out to you all. 

Regards,

---

### Post by SeijiSensei on 2020-12-09
I run rsync on the machine with the backup device attached and suck down the files from my remote virtual servers. I find it easier to "pull" files than "push" them.  I also use the --files-from and --exclude-from directives to rsync to create lists of files, directories, or "[globs]("https://man7.org/linux/man-pages/man7/glob.7.html")," to backup or exclude. For example, here is a sample exclusion list:
```

proc/
sys/
net/
*backup*
*.iso
*cache*
*thumbnails*
run/
dev/
local/share
.VirtualBox
VirtualBox

```

---

### Post by frank105 on 2020-12-11
Hi again gang,

Thanks for all the info.

Looks like TheFu has already marched up the path I am heading down.   Not sure if I should mark this solved and write another one?  And YES - everyone is correct SCREEN has a ton of use and it is Awesome.  Just what I was looking for.  I read a bit about IONICE too.  OMG - thanks for the hint about not telling plex where my backup drive was - I was literally about to do that for some other testing.  I stopped.  So plex seems pretty happy so far.

But anyway - today's questions:
[LIST=1]
[*]I have two external drives I will be using.  One is online all the time.  The second only when I want to complete a backup.  But I have to edit fstab every time I boot with and without the second drive (Named Hammer).  How do I make this more automagic?  
```
#Comment out to boot without Hammer
#UUID=139c159c-d895-4c86-96f0-a2b1c872f85b  /mnt/HAMMER ext4 rw,exec,auto,user >

```
[*]Now that I have the household almost 100% Linux - ext4 is the best file system for backups?  Right?  I read way too much on this and just need another opinion with probably a PLEX server slant to it.
[*]In the examples above using ionice - are you synchronizing your deleted files too?  I am not sure I understand that command but I want to.
[*]I setup my first Plex server.  Works great in my house.  I had a buddy try and play a movie and it transcodes to a tiny file size with no option not to.  I tried all the tricks I know.  It is giving him a warning of indirectly connecting to the server but not sure if that is the cause.  I have an ISP provided modem/router and they won't let me do any port forwarding or anything.a
[/LIST]

That is what I plan to learn next.  Thanks again everyone. 

Regards,

---

### Post by TheFu on 2020-12-11
>  How do I make this more automagic? 

You can use more complex fstab entries, but you'll still need to manually umount (not unmount), the drive before removal.
OR
you can setup autofs, which will mount and umount the storage when it is requested.  This is what I use, but I'm loath to attempt helping with that after some other difficulties with simple fstab stuff.

> ext4 is the best file system for backups?
There are 50 different file systems. Each is a trade-off; good at some things, not so good at others.  In general, ext4 is a very good compromise, but I wouldn't call it "best" for backups.  However, it is what I use and it is 1000x better than NTFS.  

A good argument can be made that ZFS would be best, but ZFS isn't just a file system. ZFS is volume management and a file system in one that supports many, many, advanced capabilities.  If you haven't delved into advanced, enterprise, file systems, stick with ext4 for a few years.
> In the examples above using ionice - are you synchronizing your deleted files too? I am not sure I understand that command but I want to.
When you don't understand a command, use the manpages to get the exact answer, not our interpretation.  Another tool is explainshell.com - put the command into there and it looks up the manpage and options pointing at which is which.  Beware that manpages have versions that match the exact version of the program on your system, so the manpages ON-YOUR-SYSTEM will be slightly different from the manpages on anyone else's.  Usually, commands don't change very much so it isn't the end of the world to use google or explainshell, but from time to time, the options change.  Just beware that to correct information is on your system, in the manpages there.

> Plex server
I use plex on my LAN only, though I can access it from anywhere in the world with internet connectivity.
I don't use any plex clients. The playback screen overlays are ugly and don't come close to Kodi, which is much nicer.
I don't have a plex account. It isn't required.
When I want access to media while traveling, I use a VPN into my LAN or a SOCKS proxy and access it that way.

There is no need for a plex account. There is no need to use plex clients. Any DLNA client, like VLC or Kodi or any of the 50 others on every platform can be used instead.  I do use the Plex Server webapp a little.

As for transcoding and plex, the available bandwidth and the client system capabilities - or more likely - the capabilities that Plex thinks that client has - will determine if transcoding is forced or not.  If you are on DSL and have little upload bandwidth, don't expect to share any hidef content.

Or you can jump into the entire plex ecosystem and pay them annually for their added value. Nothing wrong with that, but I cannot provide any advice in that area.  To me, plex is a good DLNA server, not much more.

If you like, you can block your plex server from the internet. Just depends on how much privacy you are interested in forcing.  Plex is extremely nosey and sends data constantly to the plex.tv guys.  Let me check my outbound firewall block rules .... Plex is much better than my roku for spying, but it is the 2nd most active spy on my network. The top domains for plex that have 'plex' in the name:
[LIST]
[*]lastfm-z.plexapp.com
[*]htbackdrops.plex.tv
[/LIST]
But There are many, many, others.  Blocks are a trade-off in usability.

---

### Post by SeijiSensei on 2020-12-11
> **frank105 said:**
> [*]Now that I have the household almost 100% Linux - ext4 is the best file system for backups?
Backing up *nix systems by copying files (e.g, via rsync) requires a file system that supports things like permissions and symbolic links. NTFS and other file systems for Windows won't work. I generally just use ext4 everywhere.

---

