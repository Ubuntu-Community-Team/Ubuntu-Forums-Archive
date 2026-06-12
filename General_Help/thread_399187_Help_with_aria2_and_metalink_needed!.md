---
title: "Help with aria2 and metalink needed!"
date: 2007-04-02
forum: General Help
---

### Post by outofnicks on 2007-04-02
Has anyone tried aria2 successfully? 

I have compiled the latest aria2 (2007-03-29 aria2-0.10.2+1) and also c-ares-1.3.2 to go with it, and tried using a metafile to get DamnSmall Linux but after this command:
```
kenn@kenn-desktop:~$ aria2c -p -t 10 --lowest-speed-limit 4000 -M DamnSmallLinux-3.2.metalink
```
I get this error in the terminal:
```
Sun Apr  1 23:28:07 2007 - NOTICE - No URI to download. Download aborted.
```

I am in the root of my home folder, as is the metafile. I have an ~/.aria2 directory, with the file aria2.conf . I have tried both with and without the config file.

The metafile has a whole list of URL's  in it, isn't that what aria2 is supposed to be looking for? I know I'm missing something, What am I doing wrong?

---

### Post by antini on 2007-04-06
You might want to post in the aria2 forum - [http://aria2.sourceforge.net/](http://aria2.sourceforge.net/)

I would try it out w/ no options besides '-M file.metalink' and then maybe log it if you are still getting the same error. Also, posting the metalink or the URL to it might help.

---

### Post by icheyne on 2007-04-30
I can't get this working either.

x-(

---

### Post by antini on 2007-04-30
can you post the output of 'aria2c --v' and the URL to the metalink?

---

### Post by outofnicks on 2007-04-30
Hi, thanks for the offer of help.
Here is my output of aria2c --v:
```
aria2c version 0.10.2+1
**Configuration**
http: yes
https: no
ftp: yes
bittorrent: no
metalink: no
message digest: no
async dns: yes
```

I'm using a metalink file downloaded from [http://www.metalinker.org/samples.html](http://www.metalinker.org/samples.html) , the URL for the metalink I/m trying to use, for DamnSmall Linux, is: 
[http://www.metalinker.org/samples/dsl-3.3.iso.metalink](http://www.metalinker.org/samples/dsl-3.3.iso.metalink)

I tried using a local metalink file like this:
```
aria2c -p -t 10 --lowest-speed-limit 4000 -M dsl-3.3.iso.metalink
```

(This is a newer version of DSL since my first post)

and an http metafile:

```
aria2c -p -t 10 --lowest-speed-limit 4000 -M http://www.metalinker.org/samples/dsl-3.3.iso.metalink
```

Also without any options besides -M, as you suggested:

```
aria2c -M dsl-3.3.iso.metalink
```

And I get this error:

```
NOTICE - No URI to download. Download aborted.
```

---

### Post by antini on 2007-05-01
> aria2c version 0.10.2+1
**Configuration**
metalink: no

metalink:no most likely means you don't have a recent enough version of libxml2. can you upgrade to the latest version?

are you compiling aria2 or using a binary from somewhere else?

---

