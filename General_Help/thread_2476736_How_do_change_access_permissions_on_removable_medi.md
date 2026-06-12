---
title: "How do change access permissions on removable media, so I can access a shared folder?"
date: 2022-07-05
forum: General Help
---

### Post by user_stu on 2022-07-05
Hi,

Apologies for the attachments (as opposed to inline images) - I couldn't see how to insert images other than by uploading first to dropbox or similar, and since I would not keep the files indefinitely on dropbox, it would have left the post incomplete should anyone want to look at it in the future).
****

I have Ubuntu 22.04 running as a guest in virtual box on Windows 10

I installed the virtual box guest additions and added a shared folder via virtual box, to which I need read/write access (but can't work out how to do that).

The location of the shared folder in Windows is:

D:\DOWNLOADS\shared with linux vbox 

Folder as viewed via Nautilus (see 1st attachment)

How do I get read/write access to this folder from the guest ?

Permissions according to Ubuntu (see 2nd attachment)

I know this is likely a chmod thing but I googled and tried a couple different things without success (the commands I copied didn't error but nor did they fix my issue).

Thanks in advance.

Stuart

---

### Post by TheFu on 2022-07-05
Don't have spaces in the names.  If you do, you must use "quotes".  Avoid odd characters in share names, filenames, directory names, until you learn more clearly how to use Linux.

Also, the virtualbox manual has a good explanation for how to access files on the hostOS.   [https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders)

No, it isn't a chmod thing. That is extremely unlikely.

Are you asking how to access CDROMs or the hostOS storage?  For non-native file systems, the only way to control permissions, ownership, groups, etc. .. is by telling Linux specifically which you want for each of those things in the mount command (or the /etc/fstab settings).

BTW, this question is strictly related to virtualbox, so it belongs in the virtualization subfolder.  A moderator will move it. You shouldn't do anything about that now.
And .... inline images are to be avoided here. Don't force people who pay for internet by the byte to was it on things that are easily addressed via text.  For example, to always mount storage from the hostOS into a guest VM, the best/only way I know is through the fstab file.

---

### Post by Morbius1 on 2022-07-05
```
sudo gpasswd -a your-ubuntu-username vboxsf
```
Log out of your Ubuntu guest.

Log back in.

---

### Post by user_stu on 2022-07-05
Thanks re spaces in filenames etc. Did you look at the screenshot (I do not have permission as non root user to the folder) = I didn't/don't believe this is a virtualisation specific question, though I provided the background in case it is.

In any case (for no apparent reason, as I'd already rebooted) I can get access today, prompted by password, so all good.  

> **TheFu said:**
> Don't have spaces in the names.  If you do, you must use "quotes".  Avoid odd characters in share names, filenames, directory names, until you learn more clearly how to use Linux.

Also, the virtualbox manual has a good explanation for how to access files on the hostOS.   [https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders)

No, it isn't a chmod thing. That is extremely unlikely.

Are you asking how to access CDROMs or the hostOS storage?  For non-native file systems, the only way to control permissions, ownership, groups, etc. .. is by telling Linux specifically which you want for each of those things in the mount command (or the /etc/fstab settings).

BTW, this question is strictly related to virtualbox, so it belongs in the virtualization subfolder.  A moderator will move it. You shouldn't do anything about that now.
And .... inline images are to be avoided here. Don't force people who pay for internet by the byte to was it on things that are easily addressed via text.  For example, to always mount storage from the hostOS into a guest VM, the best/only way I know is through the fstab file.

---

### Post by user_stu on 2022-07-05
Thanks. Today (no idea why as I'd already rebooted Ubuntu multiple times, though not the host OS) I can access the folder in Ubuntu - it does prompt me for root password. 

Does the command below result in the local Ubuntu account being trusted for all things related to virtual box (and therefore in theory I won't then be prompted for a password for the shared folder)?

Edit: I just tried the command and it does indeed remove the need for a password -- thank you.

Absolutely needed, as I was being asked to authenticate on a per file basis. 

Thanks again.

> **Morbius1 said:**
> ```
sudo gpasswd -a your-ubuntu-username vboxsf
```
Log out of your Ubuntu guest.

Log back in.

---

### Post by TheFu on 2022-07-05
> **user_stu said:**
> Thanks re spaces in filenames etc. Did you look at the screenshot (I do not have permission as non root user to the folder) = I didn't/don't believe this is a virtualisation specific question, though I provided the background in case it is.

In any case (for no apparent reason, as I'd already rebooted) I can get access today, prompted by password, so all good.

If you are using vboxsf, then it most definitely **is** a virtualization issue.  Without virtualbox, you'd never have that storage driver.
The screen shots don't help me since I'd never use a GUI to mount storage anyway.

It is really helpful if your replies include a bit of a quote for the post you are replying to.  I strip out the parts that I don't know the answer to or that were just extra information, so the nesting doesn't get crazy.

Ubuntu doesn't have a root password.  We use sudo instead, not root.

Also, every time Ubuntu has a new kernel installed, the vbox guest additions need to be reinstalled (to link into the new kernel), so don't forget to do that. I don't know if a reboot is needed after the guest additions are reinstalled, but I think it is.

---

### Post by user_stu on 2022-07-07
> **TheFu said:**
> ...

It is really helpful if your replies include a bit of a quote for the post you are replying to.  I strip out the parts that I don't know the answer to or that were just extra information, so the nesting doesn't get crazy....

...Also, every time Ubuntu has a new kernel installed, the vbox guest additions need to be reinstalled (to link into the new kernel), so don't forget to do that. I don't know if a reboot is needed after the guest additions are reinstalled, but I think it is.


OK, thanks again

---

