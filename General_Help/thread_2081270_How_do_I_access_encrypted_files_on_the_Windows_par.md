---
title: "How do I access encrypted files on the Windows partition?"
date: 2012-11-06
forum: General Help
---

### Post by JamesTheAwesomeDude on 2012-11-06
I want to access some files on my Windows partition. I encrypted them a while back, just because I was young and it made me feel like a spy or ninja or something. The thing is, that makes them impossible to access from Ubuntu. I'd prefer not to remove the encryption (I'm still a child at heart,) but rebooting is a pain and I can't get VirtualBox to work. I have the username and password to the user (it's my User, after all,) so I'm not trying to do anything illegal. Is there any sort of command that would mount with a password? I'm thinking something along the lines of this: (see the final argument)```
sudo mount -t ntfs -rw nls=utf8,umask=0222 /dev/sda1 "/media/Windows XP Professional" -ntfsKey=username,password
```The Ubuntu is Ubuntu 12.04 LTS 64-bit, and the Windows is Windows XP Professional 32-bit, with service pack 3. (I'm mentioning this incase the Windows version and/or service pack influences the encryption at all. The reason that the Windows is 32-bit is that the guy I bought it from was a noob who didn't know the computer was 64-bit. I didn't even realize it for a few months.)

---

### Post by jerome1232 on 2012-11-06
You log into Windows and decrypt them.

Seriously, ntfs3g doesn't support NTFS encryption.

---

### Post by Cheesemill on 2012-11-06
+1

The only way to access files that are using Windows' native encryption technology is to use Windows.

You could look at using something like TrueCrypt to encrypt your files instead, as versions are available for both Linux and Windows.

---

