---
title: "Deleted file not being freed, still taking up space"
date: 2014-08-01
forum: General Help
---

### Post by mckenna2 on 2014-08-01
Hi, I'm a fairly new Ubuntu user and I'm running a home file server with Ubuntu 12.04 LTS.

The home drive of my server recently completely filled up, and I found the culprit to be a 23G log file for Plex Media Server.
After reading that other people had the same problem, I moved the file (plexmediaserver.log) to trash from nautilus, and replaced it with a new file of the same name, but with no write permissions for anyone besides root (so plex would not write to it again).

The space hadn't freed after that, so I restarted and then Ubuntu wouldn't start up because the disk was still full.

Since then I've tried emptying all trash files (including root, and trash on other disks) through ssh, killing the host process (Plex Media Server) and restarting, but none have worked.
Also, when I checked the trash before emptying it, there was no evidence of the file, and when using df to look at the original file location, there is no evidence of the 23G's.

Please help, and I can provide more info if needed.

---

### Post by SuperFreak on 2014-08-01
Are you sure root trash is emptying. Try Select file and Shift Delete when you delete files in Root Trash

---

### Post by papibe on 2014-08-01
Hi  mckenna2. Welcome to the forum ):P

You have to 'empty' the trash as the same user that deleted the file. There's at least a couple of ways to do that:
[LIST]
[*]Open the Trash, and click the 'Empty' button, or
[*]Right click the icon on the laucher and select 'Empty Trash'.
[/LIST]
Does that help? Let us know if that helped.
Regards.

---

### Post by mckenna2 on 2014-08-01
Thanks for the quick feedback.

Currently, the only way I can delete the trash is through command line on ssh.

I followed the methods here under step 7: [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

So I believe that should permanently delete the files there as if I were to shift-delete in nautilus, but I'm not sure if that ensures I deleted them as the same user. I am logged into ssh under the same username as I deleted the file on, though. 

After restart, this still hasn't fixed the problem...

---

### Post by steeldriver on 2014-08-01
Can you confirm where the file actually is?

```

ls -A ~/.local/share/Trash/files/

sudo ls -A /root/.local/share/Trash/files/

```

---

### Post by mckenna2 on 2014-08-01
steeldriver, I did find what appears to be the file in /root/.local/share/Trash/files/, but when I try to delete it as sudo it says access denied. Do I have to log in as root somehow to get permissions in /root?

Thanks, it's great that I finally know where it is!

---

### Post by steeldriver on 2014-08-01
Hmm... what's the exact command you're using, and the exact error message?

---

### Post by mckenna2 on 2014-08-01
I figured it out!

I transferred ownership of root's trash to myself, and although I could not delete all files in the folder with *, I was able to delete the 24G one, and now my disk usage is down to 37% from 100%!
Now that I think about it, there is a possibility that I deleted the file from gksudo nautilus, which I guess would send deleted files to root trash.  

Thanks everyone, and thanks to steeldriver for helping me find it!

---

