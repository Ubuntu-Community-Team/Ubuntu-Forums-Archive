---
title: "SSH problems"
date: 2012-12-24
forum: General Help
---

### Post by joblafors on 2012-12-24
Hello.
I used to be able make ssh connection from my ubuntu 12.04, but now I'm getting this error:

```
usr@usr-HP:~$ ssh usr@myhost.lv
The authenticity of host 'myhost.lv (89.111.xx.xxx)' can't be established.
RSA key fingerprint is a2:54:eb:34:a9:61:e5:e0:1f:da:df:ff:0e:15:46:08.
Are you sure you want to continue connecting (yes/no)? 
Host key verification failed.

```

I get the same error when connecting to server on my local network.
And that other local network server cant ssh to my pc or remote server. Could that be my local network(router) problem?

Thank you for any help.

---

### Post by agillator on 2012-12-24
This 'error' simply means your machine does not recognize the key that the remote machine has sent. This can happen if you have never connected to that machine before, the key of that machine has changed, your known_hosts file has changed, or the remote machine is not, in fact, the one you think it is (i.e. a sloppy man in the middle attack, a mistake in the remote host name/address, etc.). You need to decide why and what to do. Has the remote machine regenerated its key for some reason? Has something happened to your known_hosts file, for example has it been accidentally deleted or was a key in it removed? If you are satisfied that you are actually connecting to the correct host you can answer yes. It is possible that you will then get an error, depending upon configuration, that refuses to connect because the key is different than that in the known hosts file. If so, it will tell you which key by line number in the file is at fault. Then you again have to decide what to do. Either you are being attacked/spoofed in which case get out of there, or there has been a change in which case delete the offending key and try again.

---

### Post by spynappels on 2012-12-24
> **joblafors said:**
> 
```
usr@usr-HP:~$ ssh usr@myhost.lv
The authenticity of host 'myhost.lv (89.111.xx.xxx)' can't be established.
RSA key fingerprint is a2:54:eb:34:a9:61:e5:e0:1f:da:df:ff:0e:15:46:08.
Are you sure you want to continue connecting (yes/no)? 
Host key verification failed.

```


I presume you selected no here to get the "Host Key Verification Failed" message?

If you are getting the same thing when connecting to a local (LAN) server, and you are confident that your LAN is secure, it is more likely to be an issue with your known_hosts file.

If the host key for the remote hosts changed you would more than likely get a different message as StrictHostKeyChecking is enabled by default and it would not allow you to connect until you removed the offending entry from your known_hosts file.

Have you made any changes in your home folder which may have changed something in your known_hosts file, or even deleteed it altogether?

---

### Post by joblafors on 2012-12-24
> **agillator said:**
> This can happen if you have never connected to that machine before 
Perhaps I have re-installed my system since last time I connected successfully.

One thing I forgot to mention - I can connect to both servers using putty. Why is putty working ?

> **agillator said:**
> The key of that machine has changed 
It's a VM I'm renting from hosting company. Don't think they would change anything like that, I sure haven't done it. But don't know how to check this.

> **agillator said:**
> Your known_hosts file has changed
*Modified: Sun 23 Dec 2012*, I'm sure I did this when trying to fix the problem using everything I could find in google. Don't know if this is the source of the problem.

> **agillator said:**
> 
Or the remote machine is not, in fact, the one you think it is (i.e. a sloppy man in the middle attack, a mistake in the remote host name/address, etc.).
How could I check for this? Sounds unlikely that someone would do that.

> **spynappels said:**
> 
If you are getting the same thing when connecting to a local (LAN) server, and you are confident that your LAN is secure, it is more likely to be an issue with your known_hosts file.

I'm quite sure my LAN is secure.

> **spynappels said:**
> 
Have you made any changes in your home folder which may have changed something in your known_hosts file, or even deleteed it altogether?
*Modified: Sun 23 Dec 2012* I followed few tutorials on how to fix this, I'm sure that changed it.

---

### Post by joblafors on 2012-12-24
So I just managed to connect using "Remmina remote desktop client"
It asked me:
> The server is unknown. The public key fingerprint is:
xx.xx.xx.xx.xx.xx.xx.xx
Do you trust the new public key?
Then he connected me. And now ssh from terminal works just fine.

Thank you for your help.

---

### Post by rnerwein on 2012-12-24
> **joblafors said:**
> Perhaps I have re-installed my system since last time I connected successfully.

One thing I forgot to mention - I can connect to both servers using putty. Why is putty working ?

 
It's a VM I'm renting from hosting company. Don't think they would change anything like that, I sure haven't done it. But don't know how to check this.


*Modified: Sun 23 Dec 2012*, I'm sure I did this when trying to fix the problem using everything I could find in google. Don't know if this is the source of the problem.


How could I check for this? Sounds unlikely that someone would do that.


I'm quite sure my LAN is secure.


*Modified: Sun 23 Dec 2012* I followed few tutorials on how to fix this, I'm sure that changed it.
hi
you just login as another user before. got exeactly the same message when i loged in from my laptop to my server with my "test_user"
and test_user wasn't already set up for ssh usage.
cheers

---

### Post by spynappels on 2012-12-24
> **rnerwein said:**
> hi
you just login as another user before. got exeactly the same message when i loged in from my laptop to my server with my "test_user"
and test_user wasn't already set up for ssh usage.
cheers

This is correct, because the known_hosts file is  in a hidden ssh directory in your home directory, so when a host is added to your known_hosts file, it is not automatically added to any other user's  known_hosts file.

---

### Post by spynappels on 2012-12-24
> **joblafors said:**
> So I just managed to connect using "Remmina remote desktop client"
It asked me:

Then he connected me. And now ssh from terminal works just fine.

Thank you for your help.

Ok, that all makes sense, I believe Remmina also uses the same known_hosts file in the .ssh directory in your home directory. You could recreate the problem by naming your known_hosts file to something else, you'll get the same messages.

Glad it now works anyway.

---

### Post by rnerwein on 2012-12-24
> **spynappels said:**
> Ok, that all makes sense, I believe Remmina also uses the same known_hosts file in the .ssh directory in your home directory. You could recreate the problem by naming your known_hosts file to something else, you'll get the same messages.

Glad it now works anyway.
hi
just answer with "yes" that's all.
ciao

---

### Post by markbl on 2012-12-24
> **joblafors said:**
> 
It's a VM I'm renting from hosting company. Don't think they would change anything like that, I sure haven't done it. But don't know how to check this.

If you are using dreamhost then see [https://discussion.dreamhost.com/thread-56363.html](https://discussion.dreamhost.com/thread-56363.html).

---

