---
title: "Using SCP to send large encrypted file from Ubuntu to Mac - how to?"
date: 2014-11-22
forum: General Help
---

### Post by Marcus Aurelius on 2014-11-22
Hello,

I am rather new to security.  I have an 80mb file on my desktop that I need to send to another computer not on my network.  I need this file to be encrypted, and the person I am sending the file to is less computer literate than me.  So this needs to be simple on both ends.  

I read that SCP automatically encrypts during sending and is decrypted upon arrival.  So this sounded good.  Also, I have ubuntu and I am sending to a MAC computer, so they both work well with SCP.  

Now can I email a link to the MAC User that they can just click, that will allow them to access and download this file from my computer?  Something like the following?  The mac user will click the link I format for them  which automatically from the email tells scp to access my ubuntu machine, take my file and dump it on their desktop?

scp ubuntu_username@ubuntu_server:/home/ubuntu_username/large_file 

I know the above is not correct, but something along these lines?  Will a command have problems with my cable modem or IP or anything?

I do not want to use a webbased email (sendthisfile.com) who might store/keep my file.
Thanks

---

### Post by nerdtron on 2014-11-22
I'm not sure if MAC supports scp but your syntax for scp is in complete.
Syntax is 
```
scp [source] [destination] 
```

In this case the source is the ubuntu server and destination is a folder on their mac.
From the MAC machine:
```
scp ubuntu_username@ubuntu_server:/home/ubuntu_username/large_file /path/to/save/on/mac 
```

Have you also considered using FileZilla? It's a GUI tool that can connect to the Ubuntu server and users can download/upload files to and from their machine.

---

