---
title: "Use NAS media server as home directory in home"
date: 2019-09-09
forum: General Help
---

### Post by tomtom447 on 2019-09-09
Howdy, I have a NAS (Openmediavault) and several computers in my house. I would like to now if it is possible to either synchronize, merge, link, mount all the servers shared directories into the user accounts of all users. The goal is to have everything a user would store in the home directory automatically stored on the NAS so they have all the same files on all the computers and through a web service like FTP.
I have setup user accounts with a home directory on the NAS and it does mount, so I'v got that fare.

---

### Post by TheFu on 2019-09-10
First, don't use plain FTP.  EVER, for remote access to files.  It isn't secure.  Use sftp or scp or sshfs.

Second, HOME directories must have full Unix permissions.  That means the mounts and file systems need to sue NFS.  If you NAS allows that, then you can use **autofs** on each client to mount the HOME anywhere it is needed. In corporations this is common.  However, because Gnome uses DBs to store configurations, I have know idea how well running a GUI will work with access to the same Gnome config files/DBs.  I've never tried it.  If you don't run a GUI or just take steps to manually prevent having more than 1 GUI client running at the same time, it will be fine.

To avoid those issues, many people will setup NFS directories that aren't in HOME directories. Think what could happen if you try to use the same web browser concurrently on 2 different machines and the cache files are being written by both systems?  Or a GUI email client.  It would probably be bad.  I use /D1/, /D2/, and /misc/ for storing files that are NFS mounts. Almost every client system on my network has NFS mounts for those files to the same location on each client.  You can use symbolic links from a HOME directory (not NFS) pointing to an NFS data storage directory in, say, /D1/thefu/documents/  if you like.  If you use autofs, as soon as you try to access that link, the mount will happen dynamically and remain mounted until all the open files there are closed.  Then 3-5 min later, the NFS mount will be removed automatically.

I even use NFS mounts on my laptop, but when I'm not at home, I know those mounts will not work, so I don't ask for them.  

So, the answer is yes, you can do that, assuming OMV supports NFS.

And please don't use plain FTP ever. Actually, it would be best if you disabled that and learn to use other tools.
sftp has clients for every networked OS. When using ssh-keys, it is considered secure enough for use over the internet.  On Windows, WinSCP and Filezilla both are nice sftp clients.  Android has a few, I use ES File.  All the versions of rsync also work, since it uses ssh for a secure tunnel by default.  Again, these all should use ssh-keys, never passwords, when going over the internet.  If you lock down ssh properly, which is a well-understood thing, then the risks are tiny.

Anyways, for which directories need to be local and which can be remote, the *Linux File System Hierarchy Standards* document spells out how reputable distros do things. Ubuntu follows it as do most of the larger distros.

---

### Post by tomtom447 on 2019-09-10
First I said like FTP I know it's not the most secure... Though it's not for secure data. I only need documents, music, pictures, downloads, wine and some game data to be available on all computers through the NAS. NFS is supported by OMV and it's based on Debian so I can add additional share options. I'm not concerned with sharing user settings or program specific content... Outside of games from Steam and Java.

---

### Post by TheFu on 2019-09-10
I don't use steam. Know ZERO about it.

Java is installed, if you use apt, to locations like other binary programs.
Java programs would have their own settings and configuration, which you'd want to ensure was the same across different systems. Making certain the local and NFS mounts appear to be in exactly the same locations would be a first step.  That would apply to steam, I suppose.

Plain FTP should have died in 1997, never to be used again.

---

### Post by tomtom447 on 2019-09-10
Steam and Java games store all settings within the same directory as the game itself and saved content... So not an issue.

---

### Post by TheFu on 2019-09-10
Maybe I'm dense.  Is this solved or what is the holdup?

---

### Post by CatKiller on 2019-09-10
> **tomtom447 said:**
> Howdy, I have a NAS (Openmediavault) and several computers in my house. I would like to now if it is possible to either synchronize, merge, link, mount all the servers shared directories into the user accounts of all users. The goal is to have everything a user would store in the home directory automatically stored on the NAS so they have all the same files on all the computers and through a web service like FTP.
I have setup user accounts with a home directory on the NAS and it does mount, so I'v got that fare.

It is possible. NFS is the protocol you'll want to use, unless you want to use Windows machines too, in which case you might consider Samba - although it is possible to share the same directories using a number of different protocols at the same time, depending on your needs.

You'll need to make decisions about how you want to do it: shared home folders is possible, but is temperamental for concurrent access, and for the shared folders being unavailable. You'll know better than we can guess about whether you'll want to have the same user from multiple machines, and the availability of your storage box.

Another way to do it would be to have the different types of data shared separately - music, videos, games, flat data, and so on - for each user, and mount each of those to the user's home folder at boot. That way, if your box is unavailable each user will still have their settings (which you might want to be different on each machine anyway) and you don't need to worry about programs on different machines trying to write to the same file at the same time.

There shouldn't be any problem having your Steam library or Java files on your NAS.

---

### Post by tomtom447 on 2019-09-11
I already have the directories mounted but they are not synced, merged, linked by or mounted into the home directory...the goal of this post. I want (for example) music located on the NAS to be shown in the music folder of the home directory in all computers and if I are content to one of the computers it should show up on the NAS and all other computers connected. I just don't know if I should use a symbolic link, use some mount script or what. I also want some directory to share between users over the NAS.

---

### Post by SeijiSensei on 2019-09-11
On the NAS, create a folder, we'll call it /shared, with full permissions.  If you want to insure that one person cannot delete another person's files, use the "[sticky bit]("https://www.thegeekstuff.com/2013/02/sticky-bit/?utm_source=feedburner")."  I've never used a NAS, just Linux servers, but you want to create a file structure like this.

```

sudo mkdir /shared /shared/Music /shared/Documents ...
sudo chmod 1777 /shared -R
[etc.]

```

Prepending "1" to the permissions creates the sticky bit.  The directory /tmp has similar permissions. 1777 gives everyone list, read, and write privileges, but no user can delete another's files.

Now, in each user's home directory, create a symbolic link to the shared Music directory like this:

```

cd /home/user1
sudo ln -s /shared/Music
[etc.]

```

You can have the OS create the shared directory for new users by putting the same symbolic link in /etc/skel.

```

cd /etc/skel
sudo ln -s /shared/Music

```

Now all new users will have the Music symlink created automatically.

Follow the same approach to create a shared directory.

If you don't want to let users put files in /shared/Music, you would need to use permissions like 0755 for the shared directories, and have them owned by an administrative user or root.

---

### Post by HermanAB on 2019-09-11
OK, well, you say this is a home system.  So assuming that you can conk whoever abuses the system upside the head with a wet noodle, then you can cut as many security corners are you like to.  At home, FTP is OK for a network protocol.  Yes, FTP is insecure, but so is SMB, CIFS and NFS!  Also bear in mind that Windows only supports two network file protocols by default and the venerable old Anonymous FTP is one of them.

I use SSH for everything, but that is just me.  You only need to be paranoid when people *really* are after you...

The main problem with a NAS is all the failure corner cases.  You need to mount the NAS shares after both the NAS and the host computer are up and networked and it is amazing how many times such a system will fail to mount automatically for no apparent reason.  You can try running your script from rc.local - which runs after the network is up.  Make a counted loop with a 'sleep 1' statement that will retry at least 5 times before giving up, to keep the support calls down.

---

### Post by TheFu on 2019-09-11
> **tomtom447 said:**
> I already have the directories mounted but they are not synced, merged, linked by or mounted into the home directory...the goal of this post. I want (for example) music located on the NAS to be shown in the music folder of the home directory in all computers and if I are content to one of the computers it should show up on the NAS and all other computers connected. I just don't know if I should use a symbolic link, use some mount script or what. I also want some directory to share between users over the NAS.

If you have the NAS directories mounted to a directory using NFS, perhaps /Music/ on the Linux machine, 
[LIST=1]
[*]**ln -s /Music ~/MUSIC**  # that will create a symbolic link to the /Music directory. ~/MUSIC cannot pre-exist.
[*]Everything under /Music is accessible in ~/MUSIC
[/LIST]
You can do the same for Documents and anything else.  
~/MUSIC is NOT the same as ~/Music or ~/music. All are different than ~/MUSIC.
I wouldn't directly mount NAS storage into any HOME directory for a number of subtle reasons.

You can use normal Unix file and directory permissions to control the access to the files by different userids on each system.

If other people's directions above here are clearer, then use those.  I wanted to shortest example possible.

---

### Post by tomtom447 on 2019-09-11
Thank you SeijiSensei and TheFu, I think symbolic links will do nicely. I wasn't sure what was the best solution. On the NAS each user gets a separate directory and a predefined set of permissions within a home directory, so I populated the user accounts with the folders I wanted and set a permanent mount on the computers that logins a user to the account on the NAS when they login to the computer. I just have to symlink the directories into ~home and make sure any applications can save docs, media... to the NAS through symlink.

I don't know about sharing a folder across user accounts on OMV as I think I would need an add-on for that... OMV like most NAS is a bit different than a server and not as straightforward, but I chose it to be more of a rounded, complete out of the box, and all in one IS I have worked on other servers that are a bit easier to manage settings wise, but I didn't want to build a ui from scratch to manage things on the go and it has all the tools included in that interface. Hopefully I will be able to set this up with your instructions, and will come back with results.

---

### Post by TheFu on 2019-09-11
> **tomtom447 said:**
>  
I don't know about sharing a folder across user accounts on OMV as I think I would need an add-on for that... OMV like most NAS is a bit different than a server and not as straightforward, but I chose it to be more of a rounded, complete out of the box, and all in one IS I have worked on other servers that are a bit easier to manage settings wise, but I didn't want to build a ui from scratch to manage things on the go and it has all the tools included in that interface. Hopefully I will be able to set this up with your instructions, and will come back with results.

Standard Unix file and directory permissions handle this need.  People working together in groups is a standard thing for Unix systems and has been since the early 1970s.  By using NFS, you have access to groups and can setup a shared group if you want everyone to have write access to the same files.  But if you only intend for the accounts to have read-only access - that's what the "other" part of the permissions are all about.

chmod is the command to manage permissions.  Beware that root/sudo on a different machine using NFS access cannot change anything.  This is a security default for NFS.

---

