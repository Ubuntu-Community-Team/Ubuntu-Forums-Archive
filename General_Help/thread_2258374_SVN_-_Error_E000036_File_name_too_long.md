---
title: "SVN - Error E000036: File name too long"
date: 2014-12-27
forum: General Help
---

### Post by DigNative on 2014-12-27
Hi,


I have to work with a Subversion repository containing files with long file names (up to 157 chars including file extension). This works perfectly fine on Windows using TortoiseSVN. However, if I try to checkout a working copy using the CLI of the Apache Subversion client 1.8.10-1ubuntu2 on Ubuntu 14.10, I get the following error:

```

$ svn up /home/dignative/folder/
Updating 'folder':
svn: E000036: Can't check path '/home/dignative/folder/[FILE NAME REDACTED BECAUSE OF PRIVACY REASONS]': File name too long

```

The working copy is located on an ext4 partition. According to my research, file names on ext4 file systems can be up to 255 bytes long, while there is no explicit limit on the length of the entire path. I am wondering if I hit this limit somehow, but the file name is 157 chars long and the absolute full path including file name and file extension is 240 chars long (all ASCII chars). However, the file name contains spaces, as well as some elements (folders) in the path.

I don't have this kind of problems using the CLI of the Apache Subversion client v1.8.10 on Windows 7.

Any help is appreciated.

---

### Post by ajgreeny on 2014-12-27
> **DigNative said:**
> Hi,


I have to work with a Subversion repository containing files with long file names (up to 157 chars including file extension). This works perfectly fine on Windows using TortoiseSVN. However, if I try to checkout a working copy using the CLI of the Apache Subversion client 1.8.10-1ubuntu2 on Ubuntu 14.10, I get the following error:

```

$ svn up /home/dignative/folder/
Updating 'folder':
svn: E000036: Can't check path '/home/dignative/folder/[FILE NAME REDACTED BECAUSE OF PRIVACY REASONS]': File name too long

```

The working copy is located on an ext4 partition. According to my research, file names on ext4 file systems can be up to 255 bytes long, while there is no explicit limit on the length of the entire path. I am wondering if I hit this limit somehow, but the file name is 157 chars long and the absolute full path including file name and file extension is 240 chars long (all ASCII chars). However, the file name contains spaces, as well as some elements (folders) in the path.

I don't have this kind of problems using the CLI of the Apache Subversion client v1.8.10 on Windows 7.

Any help is appreciated.
I don't really know anything about all that you are asking but I wonder if you are aware of the need to either use an escape  character in names with spaces, or to use quotation marks, ie, 
/path/to/file\ name\ with\ spaces
or
"/path/to/file name with spaces"

I may be talking complete rubbish here but I note you have only a very low number of posts on the forum and may therefore be very new to Linux.

---

### Post by DigNative on 2014-12-27
> **ajgreeny said:**
> I don't really know anything about all that you are asking but I wonder if you are aware of the need to either use an escape  character in names with spaces, or to use quotation marks, ie, 
/path/to/file\ name\ with\ spaces
or
"/path/to/file name with spaces"

Thank you very much for your reply! Yes, I am aware of the necessity of escaping --- but since I really just do an `svn up .' or `svn up [FOLDER WITHOUT SPACES IN PATH]', respectively, the aforementioned error can't be related to that.

> **ajgreeny said:**
> 
I may be talking complete rubbish here but I note you have only a very  low number of posts on the forum and may therefore be very new to Linux.


Your reasoning is completely understandable, but I am not new to Linux; I have a strong background in Linux programming and server administration.

Anyway, thank you for your efforts! Maybe you have another idea?

---

### Post by ajgreeny on 2014-12-27
Sorry; none, but welcome to the forums here.

I think you will find other people who may be much more able to help you than I.

---

### Post by DigNative on 2014-12-28
After some investigation and literature research I was able to resolve the problem: The SVN working copy was stored on an encrypted home folder using eCryptfs with filename encryption enabled (this is the default setting if the box "encrypt my home folder" is checked during Ubuntu installation). The implementation design of eCryptfs imposes a filename length limit for encrypted files, i.e., filenames of files in encrypted locations must not be longer than 143 chars if filename encryption is enabled (cf. [this official statement]("https://bugs.launchpad.net/ecryptfs/+bug/344878") and [this explanation of one of the eCryptfs developers]("http://unix.stackexchange.com/a/32834")).

To mitigate these problems one can choose either to turn off filename encryption for eCryptfs-encrypted folders or to store working copies outside of eCryptfs-encrypted paths.

---

