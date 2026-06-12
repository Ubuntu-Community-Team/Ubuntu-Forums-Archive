---
title: "Permissions for Jellyfin Service account in Ubuntu"
date: 2021-10-13
forum: General Help
---

### Post by robertsaron on 2021-10-13
I have installed Ubuntu 20.04 LTS. I then installed the jellyfin server, and when trying to add media folders, This is the message that appears: "For Linux on Arch Linux, CentOS, Debian, Fedora, openSUSE, or Ubuntu, you must grant the service user at least read access to your storage locations."

A couple of hours of searching revealed that the service account is called: jellyfin. 

How do I assign that service account permissions over my Pictures, music and Video folders and read, write access? I have not found anything that are simple and easy to follow instructions.

---

### Post by TheFu on 2021-10-13
Is this a trick question?

Normal Unix permissions and techniques apply.  Any Unix permissions tutorial will help.  If you only want jellyfin to be able to view the different media, just allow "other" read access to all the files and directories.  That should be the default, unless you do using non-native Linux storage.

If you need more help, post the permissions using **ls -al** for the directories and a few files.  Assuming the are all the same permissions, owners, and groups, this is pretty standard Unix permissions stuff.  As long as you aren't abusing the root account, the default permissions should be fine for jellyfin - at least to read.

If you want jellyfin to be able to rename and delete content, then you'll need to get much better at Unix permissions and groups.  I've written about that here a few times.  Just search these forums for "working together".

But if you use NTFS or some other non-native file system - things are harder.

For lurkers ... I'm loving Jellyfin and slowly find myself using it more and more than plex server. I certainly love the huge difference in privacy that jellyfin provides over plex.  It is crazy how plex is constantly trying to phone home about everything (every mouse click and keyboard typed) and I only see Jellyfin hit the internet when I specifically ask it to grab some metadata about my content.  Jellyfin isn't quite as feature rich for sharing with others over the internet, but that can be provided through a VPN, if needed.

Updates: grammar in last paragraph.

---

### Post by robertsaron on 2021-10-14
I have never had to set permissions for anything before in Ubuntu, or linux in general. Everything I did was done under one account, and never needed another account for anything else. While I have used Ubuntu for a long time, I do not mess around with permissions.  I will try your suggestions, and thanks for the help. I spent hours looking on line, and could not find anything specific.

The partitions were set up for ext3 or what ever ubuntu uses when doing the install. I just need the service account to be able to read, write and Delete, on Videos, Music, and Pictures. 

I love jelly fin allot more than Kodi, Plex, and Emby. Jelly fin is allot more user friendly. While the others are more powerful, I find Kodi getting to talk to another Kodi instance difficult. Jellyfin while not as feature rich as others will get there. If I had more $$ I would donate to Jellyfin development.

---

### Post by TheFu on 2021-10-14
There is nothing magical about Jellyfin permissions.  I just use the same permissions that plex media has.  That's basically, 

```
thefu   plex    drwxrw[COLOR="#FF0000"]s[/COLOR]r-x    media-directories/
```
Plex can rename and delete content. The [COLOR="#FF0000"]setgid flag[/COLOR] means that all sub-objects (files/directories/links) retain the "plex" group, of which my userid is a member.
Jellyfin gains access in the "other" permissions .... read-execute (5).  That's only needed on directories.  For the files, read-only (4) is fine.

That would be **chmod 775** on directories and
**chmod 664** on the files.

If you only want jellyfin to have read-only access, then you don't need to worry about any group stuff or the setgid flag.

---

### Post by ActionParsnip on 2021-10-14
If you want to give this access to the folders in your user's home folder then I suggest you make a new group with your user and jellyfin in it then apply this group to the folders in your home folder that you want to give access. Personally I suggest you use a separate folder, owned by jellyfin and give that full access to the data in the folder.

---

### Post by TheFu on 2021-10-14
> **ActionParsnip said:**
> If you want to give this access to the folders in your user's home folder then I suggest you make a new group with your user and jellyfin in it then apply this group to the folders in your home folder that you want to give access. Personally I suggest you use a separate folder, owned by jellyfin and give that full access to the data in the folder.

The jellyfin installer creates a jellyfin userid and jellyfin group. 
```
$ id jellyfin
uid=128(jellyfin) gid=139(jellyfin) groups=139(jellyfin)

```
The short way to provide access for userids to Jellyfin controlled files would be to add your userid to the jellyfin group.

Media files really shouldn't be placed under a HOME directory for a number of reasons.  Mainly because media files tend to grow and grow and grow and usually need a different backup solution from what we need for files in our HOME directories.  Whether media file storage areas should be owned by the jellyfin userid or the human userid is a little more complex. But if files are constantly being added and removed in those storage areas, using any account OTHER than the userid for the human would become just too much hassle, IMHO.  Once setup with the setgid flag at the top level and any pre-existing directories deeper, the group management aspects should basically be on automatic. I haven't had to touch those in years on my media server.

---

### Post by robertsaron on 2021-10-14
The last time I set up my jellyfin server on ubuntu, I did not have to apply permissions. Everything just worked out of the box. I just find it interesting as to what changed, between now and then. 

It is not hard to manage my media, I just put the file on a folder on windows, and it syncs across everything. My media storage needs are going down. It is mostly music and documents, and stuff for school.

---

### Post by TheFu on 2021-10-14
Hard to provide help without any facts.

---

### Post by robertsaron on 2021-10-15
I use a cloud service called pCloud to back up all my documents, music, movies, etc.. I have installed on my cell phone, windows, and linux box. I drop in a file, and it syncs across my computers. I delete a file on one computer, and it is remove on the other machine. I bought a life time subscription.

---

### Post by robertsaron on 2021-10-15
When doing the command: groups there is not a jellyfin group. Unless I am using the wrong command. 
There is a service account called jellyfin: jellyfin:x:127:134:Jellyfin default user,,,:/var/lib/jellyfin:/bin/false is how it comes up
I am not finding much about service accounts when looking online, is it possible to give read/write/delete access to a service account?
I only need 3 folders for it to have read/write/delete privileges. Is that possible to do with a service account? 
If I could find this information online through a google search, I would, but my lack of skill in this area makes it difficult to find the answers I need.

---

### Post by TheFu on 2021-10-15
Not sure what more I can do to help.  My prior posts answer all those questions AND list the commands to use along with where to search in these forums for "working together" steps.

On Unix, *service accounts* (as you call them) aren't special. They are just userids. Yes, an account can be given read/write/delete access to files and directories, just like your userid can.

May if you read the replies and did what was requested/suggested?  If something I wrote isn't clear - quote that and ask. It would be helpful if you put in what you think it says too, so any misunderstanding could be corrected.

---

### Post by robertsaron on 2021-10-15
Is applying permissions to a service account the same as applying them to a user? 
Do I need to full folder path, or just the name of a folder?

How do I add a service account to a group? I cannot find anything on how to do that, I have spent so so many hours looking. 

I did look for Working together, and am not sure if I found it or not.

---

### Post by robertsaron on 2021-10-18
I actually did not need to modify any groups or permissions. What was happening, is that I could not browse the full path, to add my music and other media in the jellyfin UI. BBased on the message I  got, it was assumed that permissions were to blame. I found a way to copy the full path from nautilus, that was painful, and then paste that full path into the Jellyfin, so it could then display the media. With out modifying any permissions it just works.

---

