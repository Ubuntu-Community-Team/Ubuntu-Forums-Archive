---
title: "Difference in LAN paths"
date: 2020-10-19
forum: General Help
---

### Post by Dennis N on 2020-10-19
Depending on how the connection is made, I get two different paths to the same file on my VM host machine from the VM:

The connection path syntax after using Files "Other Locations > connect to server" for initial connection from Ubuntu 20.10 beta VM to host machine: 
```
sftp://192.168.0.116/mnt/data/music/ogg/music-file.ogg

```
It works to play the file.

Typical connection path syntax saved in my old music player playlists, which previously worked: 
```
sftp://dmn@192.168.0.116/mnt/data/music/ogg/music-file.ogg
```
This syntax no longer works to access files - it must be changed to the first path above,
_My question is:_
What is the significance of adding** dmn@** (username@) into the path vs. leaving it out?

---

### Post by ActionParsnip on 2020-10-19
If you mount the file system using /etc/fstab it will appear as a local folder on your file system, then you won't need to worry about that. The data will appear to be local :)

---

### Post by Dennis N on 2020-10-19
> **ActionParsnip said:**
> If you mount the file system using /etc/fstab it will appear as a local folder on your file system, then you won't need to worry about that. The data will appear to be local :)

You mean I can use an IP address in /etc/fstab? How would the login to the host be managed if I haven't logged into the VM first?

---

### Post by ActionParsnip on 2020-10-19
Sure if the server has a static IP. You can alternatively use names. Your home router (I'm assuming its a home setup) will do DNS for you but yes, you can use IP addresses in /etc/fstab without issue.

If you exchange SSH keys then you won't need passwords either.
[https://www.jscape.com/blog/setting-up-sftp-public-key-authentication-command-line](https://www.jscape.com/blog/setting-up-sftp-public-key-authentication-command-line)

Passwords are so clunky :)

---

### Post by Dennis N on 2020-10-19
> **ActionParsnip said:**
> Sure if the server has a static IP. You can alternatively use names. Your home router (I'm assuming its a home setup) will do DNS for you but yes, you can use IP addresses in /etc/fstab without issue.

If you exchange SSH keys then you won't need passwords either.
[https://www.jscape.com/blog/setting-up-sftp-public-key-authentication-command-line](https://www.jscape.com/blog/setting-up-sftp-public-key-authentication-command-line)

Passwords are so clunky :)

I don't know the syntax for such an fstab entry to connect to a remote computer - I didn't see any mention of how to connect from fstab in the linked article - it connects with terminal. 

Assuming I could set up the key authentication, could you give an example of an fstab entry, perhaps using the IP and user name in my first post, to connect to root folder of host?  

Not being into networking or servers at all, never tried the key exchange method. In the past, Files remembers the details of how to connect if you choose that option on initial connection.

I still would like to know the answer to my question in post #1. 

Thanks for helping.

---

### Post by TheFu on 2020-10-19
NFS.
Probably want to use **autofs** to mount only when requested.  Then the storage can be treated like local storage.

sshfs is another option, but much slower because ssh encryption.

---

### Post by Dennis N on 2020-10-19
I edited the playlists with batch replace to correct the paths for a quick fix. Unless I find some guide (with actual examples) to network connection using fstab, I will stick with the bookmarks method I've been using up to now.

---

