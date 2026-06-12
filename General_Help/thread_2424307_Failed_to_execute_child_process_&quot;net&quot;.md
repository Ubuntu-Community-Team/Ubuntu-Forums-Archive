---
title: "Failed to execute child process &quot;net&quot;"
date: 2019-08-06
forum: General Help
---

### Post by unradio on 2019-08-06
I get the following error

Called "net usershare info" but it failed: Failed to execute child process «net» (No such file or directory)

Thank you.

---

### Post by wildmanne39 on 2019-08-06
Hello and welcome to the forum, you have posted in a section of the forum that is English only will you please translate your entire post so our volunteers will be able to help you? Normally I would do this for you once but I am on my cell.
Thanks

Back on laptop and I translated it for you, if you would like to post in your own language perhaps one of these sub-forums is the right place.

[https://ubuntuforums.org/forumdisplay.php?f=183](https://ubuntuforums.org/forumdisplay.php?f=183)

---

### Post by #&amp;thj^% on 2019-08-06
I'll help a bit here OP post is:
> I get the following error

Called "net usershare info" but it failed: Failed to execute child process «net» (No such file or directory)

Thank you.
Sorry if I had a un-welcomed reply.

---

### Post by wildmanne39 on 2019-08-06
> Sorry if I had a un-welcomed reply. 
Not at all.:)

---

### Post by #&amp;thj^% on 2019-08-06
> **unradio said:**
> I get the following error

Called "net usershare info" but it failed: Failed to execute child process «net» (No such file or directory)

Thank you.

Nautilus (If your using Gnome) uses the net usershare info command to get information about _non-root user_ defined Samba shares. See the [net manpage]("http://manpages.ubuntu.com/manpages/bionic/en/man8/net.8.html") for more about this command.

If that command fails Nautilus assumes there are no such shares and displays the error message it got just in case you want it.

Creating the folder "/var/lib/samba/usershares/" should prevent the message from appearing:

```
sudo mkdir -p /var/lib/samba/usershares/
```

---

