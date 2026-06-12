---
title: "Having Problems with samba share on system resume"
date: 2013-02-06
forum: General Help
---

### Post by sizzlefire on 2013-02-06
Hello!

I have been having a slight issue with opening a samba share upon system resume. I am mounting my samba shares using the following line in /etc/fstab:

//ip/folder /media/localfolder cifs domain=my-domain,username=me,password=nothingatall,uid=1000,iocharset=utf8 0 0

Which works fine when I boot up my computer normally, but when I am resuming my computer from hibernation or suspension, I end up with the inability to open the file manager for around 3 minutes, and the following error in the system log:

kernel: [20115.858037] CIFS VFS: Server xxx.xxx.xxx.xxx has not responded in 120 seconds. Reconnecting...

Once it reconnects it works fine again, is there any way to make it reconnect faster?

I tried writing the following script:

```
#!/bin/sh
case "${1}" in
    hibernate|suspend)
        sudo umount -l /media/server
    ;;
    resume|thaw)
        sudo mount /media/server
    ;;
esac
```

However this has caused additional issues. Now the computer pretty much refuses to suspend or hibernate at all. It just locks the screen and sits there. I am unsure exactly why it is doing this as at first I thought it was just waiting for umount, but passing -l should have taken care of that.

If there is any way to fix this I would really appreciate some help!

---

### Post by papibe on 2013-02-06
Hi sizzlefire.

I think you are on the right track. Are you putting that script on '/etc/pm/sleep.d/' ?

You should assume the script will be called as root, and [COLOR="Red"]**NOT**[/COLOR] use sudo.

Let us know how it goes.
Regards.

---

### Post by sizzlefire on 2013-02-06
Thank you for the tip about omitting sudo, I did not realize that! Okay I gave it a go and named it 00_mount_share and tried suspending again, and ended up with a very delayed suspend and on resume the share was no longer mounted, and threw the "only root can mount error". This gave me an idea though, since it seems mounting on startup seems to only cause issues, would it be considered a good idea to try to configure fstab to allow me to mount it when I need it? I don't think this would fix my suspend/resume issues though.

---

### Post by papibe on 2013-02-06
Well, it looks like those scripts are executed in user space and not by root. So you need the sudo after all. :p

There's a couple of options. The simplest I can think of is this:

Instead of grating you passwordless permission to /sbin/mount (or adding the 's' bit to it), you may want to create a script with the mount and then authorize it on sudoers. Take a look at [this]("http://askubuntu.com/questions/106191/how-can-i-allow-a-specific-standard-user-in-ubuntu-11-10-to-mount-a-specific-ntf") for details.

Let us know how it goes.
Regards.

---

### Post by sizzlefire on 2013-02-11
Thank you for bringing the ability to do this to my attention! It has given me an idea on a bit of a different way to try to do it. Now when I just read over my last reply I realized I did a terrible job of wording it, when I said that I was getting the error that "only root could mount" I meant I was getting this error once I logged back in, opened nautilus, and clicked on the share on the left sidebar, not in the error logs on the system, I do apologize for the confusion there.

---

### Post by sizzlefire on 2013-02-20
Quick update, I have started using gigolo and once I got it configured I have had absolutely no problems whatsoever mounting, with the exception of losing the ability to connect rhythmbox to my home music share, I fixed that with a rather workaround way using google music, so no big deal there either! 

Thank you for all your help!

---

