---
title: "Using SCP to transfer files over SSH?!!"
date: 2008-05-22
forum: General Help
---

### Post by FilmAficionado on 2008-05-22
I'm going to do my best to try to explain the complex situation I'm in:

My hostnames:
LAPTOP
HOMEPC

Username: sysadmin on both LAPTOP and HOMEPC

My goal was to use my LAPTOP from another state (and another isp) to access my HOMEPC in California. I've configured my HOMEPC to wakeonlan through the internet using dyndns.org and I can ssh to my HOMEPC through my LAPTOP from another isp just fine. I can browse the directories, etc.

I am having trouble figuring out how to copy files from my HOMEPC to my LAPTOP through ssh as both are on different isps and not on a wlan.

I tried using scp but I get the following output:
```

[B]sysadmin@LAPTOP:~$ ssh XXXX.dyndns.org
sysadmin@XXXX.dyndns.org's password:
[/B]
Linux HOMEPC 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Thu May 22 20:12:34 2008 from adsl-XXXXXX.net

[B]sysadmin@HOMEPC:~$ scp oc.mov sysadmin@HOMEPC:/Desktop sysadmin@LAPTOP:/Desktop
ssh: LAPTOP: Name or service not known
lost connection[/B]
```

So it seems like it's not recognizing my hostname of LAPTOP, which is the actual computer I am on and using... I noticed that my "hostnames" change while I am on the LAPTOP: when I open a console it says sysadmin@LAPTOP but as I ssh into my HOMEPC, the console title changes to sysadmin@HOMEPC, as shown above.

Again, through ssh I can browse through my LAPTOP all the files on HOMEPC, but I can't figure out how to copy them over through the internet using ssh... There's something trivial missing here I think.

What am I doing wrong?

Thanks in advance. If you need more info please request.

---

### Post by tamoneya on 2008-05-22
dont put the hostname in. instead put in the local ip. This would be something like 192.168.1.101

---

### Post by RAOF on 2008-05-22
I'm not entirely sure what you're trying to do.  Are you trying to copy the file 'oc.mov' on HOMEPC to your laptop?

What your command is actually asking to do is to copy 'oc.mov' and the contents of /Desktop on HOMEPC to /Desktop on LAPTOP.  This is unlikely to work, for a number of reasons, but the reason that you probably care about the most is **it requires an SSH server on your laptop**.

Probably what you *meant* to say was
```

user@LAPTOP> scp username@HOMEPC:~/Desktop/oc.mov .

```
to copy the ~/Desktop/oc.mov file on HOMEPC to the current directory.  This **won't** require an SSH server on your laptop.

In particular, you **don't** need to be logged in to the remote system with SSH before you can use scp.  SCP creates its own SSH connection.

---

### Post by FilmAficionado on 2008-05-22
> **tamoneya said:**
> dont put the hostname in. instead put in the local ip. This would be something like 192.168.1.101

Thanks for the quick reply.

If I use 
```
scp oc.mov 192.168.1.100
```
it just does it and doesn't display anything. So I'm not sure anything got copied over. Where would I look since no directory was specified?

If I specify the directory:
```
scp oc.mov 192.168.1.100:/Desktop
ssh: connect to host 192.168.1.100 port 22: Connection refused
lost connection

```

---

### Post by ryanhaigh on 2008-05-22
Just to clarify what RAOF said you use this command WITHOUT first connecting to HOMEPC with ssh. Incase you were unaware there are much easier ways to do this, for example with nautilus you can open ssh://HOMEPC or if your laptop uses windows you can use winSCP, both of these will give you normal file browser interfaction (although they may be a little slow depending on your connection)

---

### Post by FilmAficionado on 2008-05-22
> **RAOF said:**
> I'm not entirely sure what you're trying to do.  Are you trying to copy the file 'oc.mov' on HOMEPC to your laptop?

What your command is actually asking to do is to copy 'oc.mov' and the contents of /Desktop on HOMEPC to /Desktop on LAPTOP.  This is unlikely to work, for a number of reasons, but the reason that you probably care about the most is **it requires an SSH server on your laptop**.

Probably what you *meant* to say was
```

user@LAPTOP> scp username@HOMEPC:~/Desktop/oc.mov .

```
to copy the ~/Desktop/oc.mov file on HOMEPC to the current directory.  This **won't** require an SSH server on your laptop.

In particular, you **don't** need to be logged in to the remote system with SSH before you can use scp.  SCP creates its own SSH connection.

Owch my mind is boggling. Ok it's good that I know what I was doing was wrong.

Ok so I won't connect to SSH first. Just a clean terminal now..
So yes, what I'm trying to do is "copy 'oc.mov' on HOMEPC to your laptop?"

OK perfect. So I did exactly what you suggested and after some trial and error implanting the dyndns url, it WORKS..:

```
sysadmin@LAPTOP:~$ scp sysadmin@XXXX.dyndns.org:~/Desktop/oc.mov 192.168.1.100
sysadmin@XXXX.dyndns.org's password: 
oc.mov                                        100%   34MB   1.9MB/s   00:18

```

Success! Thank you both so much!
I'm a fairly new Linux user and I love all the support that I've been getting. 
Thanks again. This is awesome :)

---

### Post by pdwerryhouse on 2008-05-23
> **FilmAficionado said:**
> Thanks for the quick reply.

If I use 
```
scp oc.mov 192.168.1.100
```
it just does it and doesn't display anything. So I'm not sure anything got copied over. Where would I look since no directory was specified?


That's because you didn't put a colon on the end of the IP address, so all it did was copy the file locally.

Try:

```
scp oc.mov 192.168.1.100:
```

---

### Post by FilmAficionado on 2008-05-23
> **pdwerryhouse said:**
> That's because you didn't put a colon on the end of the IP address, so all it did was copy the file locally.

Try:

```
scp oc.mov 192.168.1.100:
```

Oops. So I spoke too soon.
So the file did indeed get copied over as my post before showed.

But I browsed around my laptop and found it in /home/sysadmin/ named 192.168.1.100 (with the extension being .100 instead of .mov :() VLC still played it, but now what code would I use to actually get it copied over with the right file name and extension onto my desktop folder on my laptop?

---

### Post by ryanhaigh on 2008-05-23
```

scp sysadmin@XXXX.dyndns.org:~/Desktop/oc.mov .


```

This just copies the file to the current directory, because you specified 192.168.1.100 as the target scp renamed the copied file to that.

---

### Post by FilmAficionado on 2008-05-23
> **ryanhaigh said:**
> ```

scp sysadmin@XXXX.dyndns.org:~/Desktop/oc.mov .


```

This just copies the file to the current directory, because you specified 192.168.1.100 as the target scp renamed the copied file to that.

Ahh. That was me being stupid.

```
scp sysadmin@XXXX.dyndns.org:~/Desktop/oc.mov Desktop/oc.mov
```

Works perfectly now.
Thanks for pointing that out.

Thanks again all!

---

