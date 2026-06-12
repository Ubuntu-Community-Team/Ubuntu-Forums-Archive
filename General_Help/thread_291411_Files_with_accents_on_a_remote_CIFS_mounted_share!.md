---
title: "Files with accents on a remote CIFS mounted share! HELP!"
date: 2006-11-02
forum: General Help
---

### Post by ShiftyPowers on 2006-11-02
Hey all, I've searched long and hard for answer to this but can't find something that works.  Maybe if I explain my unique situation someone can help me out.  

I've got a main linux server at home running Ubuntu 6.06.  On that box I keep all my music files.  Many of those files have characters with accents on them (brazilian music and other foreign music).  The files are kept on an LVM volume that is set to be shared using CIFS.  The following is the readout from the /etc/fstab that mounts the Music drive:

```
/dev/HTPCvg/HTPClv /MainDrive/ reiserfs defaults 0 0
```

On my main desktop (running Edgy 6.10) I have the remote drive mount automatically on bootup with the following lines in my /etc/fstab:

```
//192.168.1.104/HTPCShare /home/shifty/HTPCDrive cifs username=htpc,password=htpc,user 0 0
```

Now, when I go into Nautilus and surf through "Network Servers" all the way to the Music directory on the remote system, the filenames include all characters even the ones with accents.  However, if I instead go through the mounted directory ("/home/shifty/HTPCDrive"), the characters that should have accents are replaced instead with weird characters such as questions marks, black diamonds, etc.  

Even more weird is that if I click on a file that has a weird character the file then disappears in Nautilus.  I can't click on the file long enough to rename the odd character.

I know this has something to do with charsets and the fact that the remote system might have different encoding. 

Does anyone have a simple HOWTO on how to get a CIFS mounted share to read properly all character types?  The HTPCShare is accessed by both windows and linux machines which can all add music to them at any time.

Thanks in advanced,
Shifty

---

