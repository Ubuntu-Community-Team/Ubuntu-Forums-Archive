---
title: "Encrypt single files vs compressed file"
date: 2013-11-06
forum: General Help
---

### Post by blacknred0 on 2013-11-06
I have a quick question to the community..... I am currently going to encrypt an important folder that is about 2GB with its content inside. I am planning to upload this remotely via ssh and keep the script running everyday to make sure that the content is sync from local to remote server.  Now, what I am struggling is with the following... should I use gpg to encrypt each files within that folder or should I compress the folder and then encrypt that compressed file?  ...of course then send them to the remote server ;)

Note that overtime that 2GB folder is going to increase as I add content and bandwidth might be an issue since the backups will be getting longer.  Also my current setup is by using private and public keys to encrypt and decrypt the files - if this info matters :).

Any suggestions will be appreciated.

---

### Post by sudodus on 2013-11-06
Welcome to the Ubuntu Forums :-)

gpg will compress the file, so there is no need to compress before running gpg.

If you plan to use the cloud storage for backup and intend to restore the whole batch if/when necessary, it might be faster or simpler to make an image file and compress the whole image file. But if it is an advantage to add or recover single files or small groups of files, it might be better to encrypt each file and store the data like that in the cloud.

There is an option to do that automatically. If you use encrypted home, everything in your home directory is encrypted (and decrypted on the fly when accessed). I does not seem encrypted, when you use it, but log out and log in with another user id or boot from a CD/DVD/USB drive, and you will see the encrypted files where you would expect your well known own directories and files :-)

So this way, you can upload what is seen by another user, and it will be encrypted.

-o-

It is important to have a good ***password*** and also to remember it. Nobody else can find it for you if you forget it.

It is also important to ***test*** the system, so that you know that it really works to restore from the cloud storage.

---

### Post by blacknred0 on 2013-11-06
Thanks sudodus!  I was part of the community in the past, just different username :)

I think I am going to go with making the compressed (tar.gz) file and then encrypting that file and uploading it to the remote server, since I don't know what I will need.  I know that the bigger the file the longer it will take to recover due to download speeds or limitations.  Later one I could rewrite the script to encrypt each file if needed.

---

### Post by sudodus on 2013-11-06
If you go with a tarball you can consider different compression methods. gzip (--> ball.tar.gz) is fast. xz (--> ball.tar.xz) is slow but gives smaller tarballs, 20-30% smaller than with gzip compression.

If you plan to compress one partition, you can use the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971") and its shell-script ***mktbl*** for this purpose. And then encrypt it with ***gpg***.

---

### Post by SeijiSensei on 2013-11-06
Just a hint that **rsync** will automatically invoke SSH for file transfers, making rsync the simplest method for backing up that file to your remote location.

---

### Post by papibe on 2013-11-07
Hi blacknred0.

As mention by sudodus, tar and encrypt, would only work for not-so-often backups. This is because even if just one file changed, the new encrypted tar file will be so much different than the original, that rsync will end up uploading the entire file (no diff efficiency ).

I wonder what kind of service/server are you uploading to.

If it is a VPS. You may either encrypt after the upload, or upload directly to an encrypted partition or even a encrypted folder (e.g. [ecryptfs]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") or [encfs]("https://help.ubuntu.com/community/FolderEncryption")).

Just a thought.
Regards.

---

### Post by blacknred0 on 2013-11-07
papibe - I understand....  I was more trying to figure out what would be more feasible in the long rung as my 2GB of content increases over time.  Right now my current design is to compress the folder, encrypt it, and then uploading using rsync.  With my connection it not that bad in terms of speed, but I was worried that overtime it was going to be much slower since the folder will increase... so kind of debating if single files encryption with a loop and then rsync would be better fit in this case.  But like sudodos mention, I think the key is, how I would like to perform the restore.  Full restore if something gets damage or partially files and restore only those damage files.

thank you all for you inputs!

---

