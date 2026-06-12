---
title: "accessing external drive"
date: 2018-10-18
forum: General Help
---

### Post by Lloydb39 on 2018-10-18
I have a homemade AMD machine, running 18.04 LTS. I'm trying to access a 320 gig drive from an old laptop, that I now have in an external drive. I can mount it but not do anything with it because I don't have the permissions needed. It is formatted ext4 and has nothing on it but lost+found. Can anyone tell me the terminal commands to change the permissions?

---

### Post by sudodus on 2018-10-18
I think this will work:

0. Check that the ext4 partition is mounted and where it is mounted, the mountpoint.

1. Create one or more directories (with sudo), where you want to store things,

```
sudo mkdir /mountpoint/mydir1
```

Use the actual path of the mountpoint and select a directory name, that you prefer (instead of those in the code above).

2. I guess you want access using your user ID, "$HOME" and execute access (that you can look into the mountpoint directory) for everybody,

```

sudo chown "$HOME" /mountpoint/mydir1
sudo chmod ugo+x /mountpoint/

```

Now it should work to read and write files in the directory  **/mountpoint/mydir1** using your user ID as well as using sudo.

---

### Post by coffeecat on 2018-10-18
You need to chown the filesystem to be owned by you. One simple terminal command:

```
sudo chown yourusername:yourusername /path/to/mountpoint
```

Obviously, substitute your user name for "yourusername". Since there are no files on the filesystem, apart from the lost+found folder, you don't need the -R recursive option for chown. If you are not sure of the mountpoint, post the output of this command:

```
mount
```

This comes up from time to time. My deja vu:

[https://ubuntuforums.org/showthread.php?t=2228600&p=13044702&viewfull=1#post13044702](https://ubuntuforums.org/showthread.php?t=2228600&p=13044702&viewfull=1#post13044702)
[https://ubuntuforums.org/showthread.php?t=2183755&p=12828989&viewfull=1#post12828989](https://ubuntuforums.org/showthread.php?t=2183755&p=12828989&viewfull=1#post12828989)

:)

---

### Post by Lloydb39 on 2018-10-18
OK, just to be sure I understand: it would be "sudo chown lloyd:lloyd  /media/lloyd/767033c0-af46-40dc-ab6f-9e9ea6cb9d42" is that right? Do I do that from the internal drive or the external drive, or does it matter?

---

### Post by coffeecat on 2018-10-18
> **Lloydb39 said:**
> OK, just to be sure I understand: it would be "sudo chown lloyd:lloyd  /media/lloyd/767033c0-af46-40dc-ab6f-9e9ea6cb9d42" is that right? Do I do that from the internal drive or the external drive, or does it matter?

If /media/lloyd/767033c0-af46-40dc-ab6f-9e9ea6cb9d42 is the mountpoint to which the ext4 partition on your 320GB drive is mounted, and your Ubuntu username is lloyd, then yes.

I don't follow what you mean by doing it from the internal or external drive. Unless you mean cd-ing to a particular location, in which case you do not have to. Simply run that command. The referenced mountpoint /media/lloyd/767033c0-af46-40dc-ab6f-9e9ea6cb9d42 tells the system all it needs to know.

---

### Post by Lloydb39 on 2018-10-18
That did it. thanks

---

