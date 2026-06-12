---
title: "How to make a TAR file and then transmit it via Telnet"
date: 2007-04-11
forum: General Help
---

### Post by shameer on 2007-04-11
Hi All,

Any Body Can help me to discribe the way How to make a TAR file and then transmit it via Telnet 
Thanks in Advance

---

### Post by Zwalther on 2007-04-11
To create a tar file, do the following:
tar -cf output.tar inputdirectory
-cf means create a file (followed by the output filename)
You can also type 'man tar' on the command-line

I don't know about telnet, but you should use ssh anyway (it's safe and telnet isn't).

You should install openssh-server on the machine you are copying to. Then type
scp localfile.tar othercomputer:/path/on/other/computer/

Or you can install openssh-server on the source computer. Then you type from the destination computer
scp sourcecomputer:/path/on/source/computer/file.tar /destpath/on/this/computer

hope this helps

---

### Post by girishv on 2007-04-11
Hi,

telnet is not for sending (receiving ) files between different computers. You can use ftp for it. But as already mentioned, it is not safe and you are better off with scp.

A simple ftp session would be like:

ftp comp_address
ftp> bi
ftp> put filename
ftp> bye


the second command bi to change the transfer into binary mode (default in linux)

You can put (get) multiple files by mput *.tar (mget *.tar)

type '?' at the ftp prompt for other commands 

Girish

---

