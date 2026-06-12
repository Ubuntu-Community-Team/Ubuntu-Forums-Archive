---
title: "Data Recovery After Failed Xubutu 16.04 Update"
date: 2016-08-13
forum: General Help
---

### Post by newbie2linux2 on 2016-08-13
Hi -

I'm at the end of my rope trying to figure out how to recover my data after a failed Xubuntu 16.04 LTS update.
I ran Xubuntu 15.04 LTS on an old Samsung Netbook and used it as a file storage / home plex server. During the update to 16.04 the system became unresponsive and I restarted the computer (obviously, should not have done that). After that, I could not log into the system: the new version didn't show up in the grub list of installed ubuntu versions and the old version wouldn't load. Here is the recap of what I've done so far.

1. Ran Xubuntu 15.04 on Samsung Netbook
2. Initiated update to 16.04
3. During upgrade the system froze
4. Restarted the machine
5. After restart, could see the window which allows to select the version of Xubutu to run
6. 16.04 not listed
7. Chose the version that was previously installed (15.04)
8. The system would initiate, show the Xubutu logo and freeze thereafter, no matter what you do
9. Boot from Live USB
10. Can see, mount and navigate the files on the hard drive
11. Navigate to /home directory
12. Go to my folder within /home where all my files are located
13. See Access-Your-Private-Data.desktop and README.txt
14. Try this [http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directo...]("http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/")
15. However, I get "Encryption is not set up" instead
16. Managed to get around this by using the unwrap-passphrase command
17. After getting success, the unencrypted files in the /tmp directory are still encrypted!

Note I have never set up encryption, the only password I've ever used on the system is the one to log into the system.

Is there anyway to restore my files? Is it possible to somehow continue the installation where it was terminated?

I need to recover 120Gb of photos!

Thanks very much!

---

### Post by wildmanne39 on 2016-08-13
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

I am posting a link that has a few tools for recoverings files and images, PhotoRec is n the link also and it is good for recovering photos.

The link is old but the tools are still some of the best for recovery.
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by newbie2linux2 on 2016-08-13
Ok, thanks. I have used those but haven't really managed to get anything. Please note that I can mount the drive and browse through the system files. The problem is that my /home/UserName shows Access-Your-Private-Data.desktop.

---

### Post by Bucky Ball on 2016-08-13
If you do a search for 'Access-Your-Private-Data' you will find a lot of hits. Maybe something there will help. There are a few with 'Solved' next to them, so you might get lucky.

I've never seen this before so curious to see how you go. I will say this: doesn't look like something for testdisk or recovery tools. As far as its concerned, nothing to recover as it appears the data is still there and so is the partition. Looks like you need to tweak with that folder to discover the magic key to open it. :-k

---

### Post by newbie2linux2 on 2016-08-14
Thanks, Bucky Ball. Will search around the site and report back.

---

### Post by newbie2linux2 on 2016-08-14
Ok, I've looked around and I haven't really found anything that could help. What I do understand is that encryption is poorly documented and not well understood.
I have founded references like "[COLOR=#545454][FONT=Verdana]You need two keys for accessing: one for accessing the file content and one to decrypt the filenames to be meaningful." I only had one password, the one to access the system. Can anyone explain what's meant???[/FONT][/COLOR]

---

### Post by Bucky Ball on 2016-08-15
Not this forum. A [google search 'in the wild']("https://duckduckgo.com/?q=Access-Your-Private-Data&t=h_&ia=web").

Not sure how it got encrypted, but as I understand it, normally you would set these two keys when encrypting and keep one VERY safe. As it seems to have encrypted itself, no idea where you might find that key. Others hopefully do. :-k

---

### Post by newbie2linux2 on 2016-08-18
Bump. Anyone??? I haven't been able to find a solution...

---

