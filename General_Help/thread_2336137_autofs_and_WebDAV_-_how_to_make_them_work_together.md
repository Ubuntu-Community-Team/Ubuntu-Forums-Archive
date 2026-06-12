---
title: "autofs and WebDAV - how to make them work together"
date: 2016-09-05
forum: General Help
---

### Post by ZippyDan on 2016-09-05
I am using placeholders for real server names and folders, however, I have tried to make them as representative of the real names as possible, so please do pay attention to my capitalization and punctuation just in case that has anything to do with my problem.

I'm running **Ubuntu 16.04**.  
I've installed **autofs** and **davfs2**.

The following command successfully mounts:
    ```
mount -t davfs https://servername.mydomain.com:3333/Shared.Folder /testmount
```

It asks me for a username and password, which are _username@mydomain.com_ and _myypassword_ and then results in a succesful mount.

This tells me several things:

[LIST=1]
[*]My WebDAV server is working and configured correctly.
[*]HTTPS works fine.
[*]My credentials authenticate succesfully.
[/LIST]
So now I'm trying to get this working with **autofs**.

Here are my files:

**/etc/auto.master**
    ```
/Server.mount /etc/auto.Servername.mount
```

**/etc/auto.Servername.mount**
    ```
storage-folder -fstype=davfs,ro :https://servername.mydomain.com:3333/Shared.Folder
```

**/etc/davfs2/secrets**
    ```
https://servername.mydomain.com:3333/Shared.Folder username@domain.com mypassword
```

With this setup, if I try to browse to */Servername.mount/storage-folder*, I get a *No such file or directory error*.

Now I'm like 95% sure that my problem is a syntax error or an authentication error.  There are not a lot of examples to be found on the web for WebDAV-based implementations of autofs, and some of them show conflicting syntax.  Nevertheless, I've tried everything I could think of.

I think it is likely that the colon in the *auto.Servername.mount* file is screwing up the parsing, so I've tried all the following combinations:
    ```
storage-folder -fstype=davfs,ro https://servername.mydomain.com:3333/Shared.Folder
storage-folder -fstype=davfs,ro https\://servername.mydomain.com\:3333/Shared.Folder
storage-folder -fstype=davfs,ro :https\://servername.mydomain.com\:3333/Shared.Folder
storage-folder -fstype=davfs,ro https\://servername.mydomain.com\:3333:/Shared.Folder

```

If that is not causing the problem, then I think it might be something to do with the *secrets* file.  So I've also tried this for my *secrets*:
    ```
/Servername.mount/storage-folder username@domain.com mypassword

```

Since I'm used to using a credentials file with cifs-based autofs mounts, I also tried, just for fun, in my *auto.Servername.mount* file:
    ```
storage-folder -fstype=davfs,ro,credentials=/etc/credentials.Servername.mount https://servername.mydomain.com:3333/Shared.Folder
```

Where *credentials.Servername.mount* was simply:
    ```
Username=username@mydomain.com  
Password=mypassword 
``` 

I also tried with *credentials.Servername.mount* as: 
    ```
https://servername.mydomain.com:3333/Shared.Folder username@domain.com mypassword

```

Nothing works.

So I feel like I'm missing some small but crucial piece of syntax or config here.  I come to you desperate.  Any help would be appreciated!

---

### Post by Morbius1 on 2016-09-05
Consider my post a bump since I've never used autofs with webdav but I do use it with cifs mounts and something doesn't look right to me.
> /Server.mount /etc/auto.Servername.mount
**/Server.mount** defines the parent folder of the mount point.
> /storage-folder -fstype=davfs,ro :[https://servername.mydomain.com:3333/Shared.Folder](https://servername.mydomain.com:3333/Shared.Folder)
**/storage-folder** is the subdirectory of that parent folder.

AutoFS is looking for this path: **/Server.mount//****storage-folder. **There is no such thing because of the double slashes. Drop the leading slash in your auto.Servername.mount file:
> storage-folder -fstype=davfs,ro :[https://servername.mydomain.com:3333/Shared.Folder](https://servername.mydomain.com:3333/Shared.Folder)
Now it will look for /Server.mount/storage-folder

I hope this gets you further along.

---

### Post by ZippyDan on 2016-09-05
> **Morbius1 said:**
> the leading slash in your auto.Servername.mount file:

Thanks for the reply.  Unfortunately, this was an error made when creatin the post, but it is not an error in the actual config file.  On my machine there is no leading slash.  I have corrected the post.

---

### Post by TheFu on 2016-09-05
I thought Windows domains where entered as userid\\\\domain - not as an email address. Did that change?

DAV has lots and lots of history of security issues, so I've never used it. I use autofs a bunch for nfs, USB, and simple CIFS stuff (no AD anything).

---

### Post by ZippyDan on 2016-09-05
That *could *be the problem, however, I tested with *mount* and it worked fine as *username@mydomain.com.* Since both *mount* and *autofs* are using the same *davfs2* library, I assume that if that format works in one, it should work in the other?

As for security issues, I'm using HTTPS and a very long, strong password.  I tried using CIFS, but I couldn't get it to work with a very basic setup (not even via a simple *mount*).  The thing is, I'm trying to get this to work over an Internet connection, where both sides have a public IP (no VPN in the middle).  I've read that many ISPs block the ports used for NFS and CIFS filesharing, so that would explain why I couldn't get those to mount.

WebDAV seems like the best solution for me in this situation.

---

### Post by TheFu on 2016-09-05
Good points. Thanks for sharing.  Try **username\@mydomain.com** Autofs and mount probably use different parsers, sometimes escaping is needed.  Just a thought, don't know if it will help.

Over the internet without VPN?????!!!!  Scary.  I'd never trust just HTTPS as enough security. Many reasons.
WebDAV also has a long history of security problems. Guess most are addressed by using a VPN or only allowing trusted users onto the LAN.

Sounds like a very tough problem.

---

### Post by ZippyDan on 2016-09-05
Ah, yes.  The WebDAV server is also set to only allow connections from the single public IP belonging to the Ubuntu box.

Also, the files I am transferring are automatically loaded into a website for public access, so I think I have sufficient security for the use case.

---

### Post by TheFu on 2016-09-05
This is for publishing website updates?  rsync dude. rsync.

---

### Post by ZippyDan on 2016-09-05
I will rsync with the folder once I get it mounted.  Unfortunately I ran into other problems getting rsync to work directly.  The server is a Synology box, so I don't have complete control over it.  I have to use the built-in packages.  I'd much rather troubleshoot Ubuntu than troubleshoot the Synology.  Synology works great for specific package-supported operations, but if you have to start messing with more advanced configurations from the console... I'd just rather not.

---

### Post by ZippyDan on 2016-09-05
> **TheFu said:**
> Good points. Thanks for sharing.  Try **username\@mydomain.com** Autofs and mount probably use different parsers, sometimes escaping is needed.  Just a thought, don't know if it will help.


I wish there was documentation for this.  I can't find any documentation as to Syntax for a *auto.XXXX* file at how it would parse an *http://* or *https://*

Similarly, where is the documentation for how */etc/davfs2/secret* is parsed?  It is silly that I have to be guessing how to do this correctly.  :(

---

### Post by TheFu on 2016-09-05
Documentation for the format is in Section 5 of the autofs manpage.  Don't see anything about DAV in there, however.
[https://savannah.nongnu.org/projects/davfs2](https://savannah.nongnu.org/projects/davfs2) appears to be the project site, but I didn't look too closely for it.

---

### Post by ZippyDan on 2016-09-05
I got it working.  

For reference, here is a working **autofs** with **WebDAV** setup

**Install prereqs**
```
$ sudo apt-get install autofs
$ sudo apt-get install davfs2
```

**/etc/auto.master**
```
/Server.mount /etc/auto.Servername.mount
```

**/etc/auto.Servername.mount**
```
storage-folder -fstype=davfs,ro :https\://servername.mydomain.com\:3333/Shared.Folder
```
Note: change "ro" [read only] to "rw" [read-write] depending on your needs.

**/etc/davfs2/secrets**
```
/Server.mount/storage-folder "username@domain.com" "mypassword"
```

**How I fixed it**

I had several problems.

[LIST=1]
[*]I found a "definitive" guide to the parsing question for *auto.Servername.mount* on the fourth page of google results: [https://freetz.org/wiki/packages/autofs](https://freetz.org/wiki/packages/autofs) So you do indeed need to escape the other colons using a backslash.
[*]I had to turn on verbose logging to find my second problem (which was embarrassingly bad).  Open */etc/autofs.conf* and find the line that says *logging = none*.  Uncomment it and change *none* to *verbose*.  Reload autofs : *$ sudo /etc/init.d/autofs reload* and then check for errors in */var/log/syslog* (log file location and name will vary by distro).
[*]*syslog* was telling me *key "storage-folder" not found in map source(s).*  Now to be fair, my *storage-folder* name is somewhat long and complex.  But I had checked it and checked it many times and again and again I missed that it was actually misspelled by one letter.  So that was my second problem, in */etc/auto.Servername.mount* I had actually written something like *storage-foldr* instead of *storage-folder*, so obviously when I was trying to access */Servername.mount/storage-folder* it was not finding any references to that in the config files.
[*]After I fixed this, verbose logging gave me my next lead, as it was now showing the error *Could not authenticate to server: rejected Basic challenge*.  So this told me I was now down to an authentication error.  I opened */etc/davfs2/secrets* and started poking around, and this time I actually RTFM because the answers were right there in the documentation contained within the *secrets* file.  It spells out exactly which characters need to be escaped with backslash, and it turns out that the @ in my username wasn't the problem, but I did have a problematic character in my password!  It turns out that putting the password in quotes is an alternate and easier way around the issue, and I put the username@domain in quotes too just for good measure.
[/LIST]
Everything works now!

---

