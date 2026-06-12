---
title: "How to share files with friends and family from my server by sending them a link"
date: 2017-11-21
forum: General Help
---

### Post by freeflyjohn on 2017-11-21
Prior to getting my Dell T30 server which is running Ubuntu 16.04, I used Dropbox to share files such as pictures and video with friends and family.

This simply involved copying the Dropbox link for a file and sending the link in an email or message.

Is there a way to do something similar with Ubuntu ?

I have got SSH and Filezilla working, both of which use SSH keys with a passphrase for added security.  However, this is not as straightforward for friends and family to use unlike Dropbox links.

I don't need a personal cloud on my server as I am not interested in keeping files synced between different devices, I am just interested in sharing files (some might be large video files) with friends and family in a way that's easy for them to access the files and thats also secure for my server.

As I have implemented SSH keys, the only way I can share files with friends and family is to send them the key (which for security reasons is best not done via email etc) and they would then need to install Filezilla and configure Filezilla to access to my server.

A far simpler (and more secure?) method would be to send them a link to a file I want to share, but is there a way of doing this with Ubuntu ?

---

### Post by monkeybrain20122 on 2017-11-21
Dropbox works the same way in Ubuntu. I have been sharing files by sending people dropbox links for a while.

---

### Post by freeflyjohn on 2017-11-22
> **monkeybrain20122 said:**
> Dropbox works the same way in Ubuntu. I have been sharing files by sending people dropbox links for a while.

The reason I wanted to stay away from Dropbox is because it has a size restriction (unless you pay a monthly subscription).  I often have to delete files from Dropbox because I have exceeded the limit.

As I have my own server I was hoping I could use my own storage space to share files with family and friends.

But the Filezilla method with SSH keys is not very convenient, especially for one off file sharing.

---

### Post by HermanAB on 2017-11-22
You can run your own anonymous FTP server and put encrypted zip files on it.  FTP is one of the few file transfer protocols that is natively supported by Windows and zip encryption is one of the few encryption methods that ordinary mortals can handle.

---

### Post by freeflyjohn on 2017-11-22
> **HermanAB said:**
> You can run your own anonymous FTP server and put encrypted zip files on it.  FTP is one of the few file transfer protocols that is natively supported by Windows and zip encryption is one of the few encryption methods that ordinary mortals can handle.

FTP is not as secure as SFTP, which is the setup I have using SSH and keys I think ?

---

### Post by gordintoronto on 2017-11-22
There are two issues with running a server on a residential Internet connection, which have nothing to do with Ubuntu:
 - your ISP might not allow you to run a server over their connection,
 - you probably have a dynamic IP address, so others don't know where to find your computer. One solution is to buy a domain name and use the software provided by dnsexit.

Teamviewer might be worth a look. although it might provide TOO MUCH access.

You could always put a link in an encrypted zip file.

---

### Post by freeflyjohn on 2017-11-23
> **gordintoronto said:**
> There are two issues with running a server on a residential Internet connection, which have nothing to do with Ubuntu:
 - your ISP might not allow you to run a server over their connection,
 - you probably have a dynamic IP address, so others don't know where to find your computer. One solution is to buy a domain name and use the software provided by dnsexit.

Teamviewer might be worth a look. although it might provide TOO MUCH access.

You could always put a link in an encrypted zip file.

- your ISP might not allow you to run a server over their connection,
[I]I don't think this is an issue as I am able to connect to my server remotely using terminal (e.g. PuTTY) with SSH and a key,  I am also able to connect to my server remotely using Filezilla and a key.

[/I]- you probably have a dynamic IP address, so others don't know where to find your computer
[I]I don't think this is a problem either, I have registered with Dynu which provides a free dynamic DNS service and again this works remotely with terminal and Filezilla.

[/I]The downside (and the reason for this post) is that using Filezilla with keys is cumbersome to just share a file/s with family and friends, I don't want to them access to my whole server either.

I might be able to limit someones their access by adding a user to the key and restricting the users access (to a shared folder for example) but I haven't looked into this because it this still means the user would have to download and install Filezilla, configure Filezilla and I would have to share the key via email which is not recommended.

It would be so much easier if I could just send them a link that downloads the file directly, just like I do with Dropbox.

---

### Post by again? on 2017-11-23
Megsync works similar to dropbox but with a 50gb limit on free accounts.
Has an ubuntu client.
[https://mega.nz/sync](https://mega.nz/sync)

---

### Post by freeflyjohn on 2017-11-23
> **guber2 said:**
> Megsync works similar to dropbox but with a 50gb limit on free accounts.
Has an ubuntu client.
[https://mega.nz/sync](https://mega.nz/sync)

Thanks, it just seems daft having to use a third party server (such as Dropbox or Megasync) when I already have my own server to that could host files for sharing.

I'm not interested in syncing between devices, just sharing files with friends and family, some of which could be large files like videos etc.

I just thought there might have been a way to do this using a simpler method than the Fillezilla approach with SSH keys.

---

### Post by mastablasta on 2017-11-23
> **freeflyjohn said:**
> 
A far simpler (and more secure?) method would be to send them a link to a file I want to share, but is there a way of doing this with Ubuntu ?

simple or secure won't go together. i suggest you install Owncloud or Nextcloud or Seafile or if this is about photos and videos, you can try the Piwigo galery. though they are "clouds", they actually do what you want to do perfectly.

they do not load the server much. these "clouds" are relatively small in size an don't need much CPU. 

you get dropbox/google drive functionality in that you can just send a link, mark its availability time (for how long the material is available), add a password if you with and then they can access the site.

you can also isolate them from other server function and lock them down further if you wish. but do note that additional security will also reduce "user friendliness".

if you don't want or need to sync, then just don't use their client.

sFTP protocol has a lot of drawbacks (e.g. if you want to just look at some photos, you need to download them first to do it)

edit: another option would be to use apache server and then create websites. while this will work for pics, i am not sure it will do for videos. you could then lock down websites with password etc.

---

### Post by Autodave on 2017-11-23
Is there a way to make a directory on his server so that only that directory (folder) would be available to his friends and family? Then they could use something like Teamviewer to access it?

---

### Post by freeflyjohn on 2017-11-23
> **mastablasta said:**
> simple or secure won't go together. i suggest you install Owncloud or Nextcloud or Seafile or if this is about photos and videos, you can try the Piwigo galery. though they are "clouds", they actually do what you want to do perfectly.


Thanks, Ill take a look at [COLOR=#000000]Owncloud or Nextcloud or Seafile ([/COLOR]Piwigo appears to be photos only)[COLOR=#000000].

But doesn't that mean the files have to be uploaded from my server to the cloud, in which case there would be a [/COLOR][COLOR=#000000]storage [/COLOR][COLOR=#000000]limit just like Dropbox ?

I wanted to cut out the "middle man" (i.e. the cloud) so that the files can be shared directly from my server to the user.  This also avoids the storage limit restrictions that cloud servers such as Dropbox have.

[/COLOR]To give you an idea of the sort of files I would share:


[LIST]
[*]I have a GoPro camera which I use for skydiving so I like to share footage with fellow skydivers.  These files can be 1Gb or more in size.
[*]I have a daughter and like to share pictures and videos with family, so again video files can be large in size
[/LIST]

---

### Post by freeflyjohn on 2017-11-23
> **Autodave said:**
> Is there a way to make a directory on his server so that only that directory (folder) would be available to his friends and family? Then they could use something like Teamviewer to access it?

I'm wary of using Teamviewer which is why Ive gone to the effort of using SSH with a key and SFTP with a key.

From what I have heard and read, Teamviewer is a big security risk and is more for desktop sharing and remote desktop control.

---

### Post by mastablasta on 2017-11-23
> **freeflyjohn said:**
> [COLOR=#000000]

But doesn't that mean the files have to be uploaded from my server to the cloud, in which case there would be a [/COLOR][COLOR=#000000]storage [/COLOR][COLOR=#000000]limit just like Dropbox ?

[/COLOR]

no,they are on your server. essentially you would run your own "Dropbox". you set the file size limit, access speed, access to files & folders, encryption etc. whatever you want. of course if you want to load large files on it you will be able to load them fast (if server is on LAN), but then you also need good internet connection (the upload speed), so that your family can download/see the file.

if this is just about sharing media, there should also be media servers available. server in this case means service running on your server.

still to serve media files you need to transcode them first (look into handbrake application for example) into a smaller file size. compressed but not losign the quality. there are popele out there that can compress 20Gb blu ray file into good quality 1,2 Gb file. 

or you can use youtube private channel for videos. :)

---

### Post by freeflyjohn on 2017-11-23
> **mastablasta said:**
> no,they are on your server. essentially you would run your own "Dropbox". 

Thanks, this is exactly what I am looking for.  Ill investigate Owncloud or Nextcloud or Seafile.

As for a media server, I am already running Plex Media Server which I can share with family and friends (I've not tested this yet). 

My server is a Dell T30 with an Intel Xeon E3-1225v5 processor so its powerful enough to transcode multiple streams on the fly.

But I dont want to have to add files to my Plex library just to share my media with family and friends.  And Im not interested in streaming it to them, I want them to be able to download it from my server.

I might also want to share other large files which arent media files so would like that flexibility to.

---

