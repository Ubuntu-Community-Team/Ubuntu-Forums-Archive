---
title: "apt-cacher?  REally slow"
date: 2008-05-06
forum: General Help
---

### Post by shane2peru on 2008-05-06
Ok, I tried apt-proxy to no avail, and then stumbled across apt-cacher, seemed easier to setup, however the update process is taking an eternity.  I have to 64bit machines both running Hardy.  So I thought I would setup apt-cacher to help the update process go quickly and easily.  I followed these two links:

[http://ubuntu-tutorials.com/2007/01/08/save-bandwidth-during-updates-with-apt-cacher-ubuntu-610/](http://ubuntu-tutorials.com/2007/01/08/save-bandwidth-during-updates-with-apt-cacher-ubuntu-610/)
[http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher-p2](http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher-p2)
  

Now, when I do an update on the other machine, it has been updating for about 5 minutes!  It is really slow, and has had several time outs here is what I get:
```

Hit http://ubuntu.mirror.frontiernet.net hardy-security/multiverse Sources
Err http://192.xxx.x.xxx hardy Release.gpg                                     
  Connection timed out
Get:2 http://192.xxx.x.xxx hardy/main Translation-en_US
Err http://192.xxx.x.xxx hardy/main Translation-en_US                          
  Connection timed out
Get:3 http://192.xxx.x.xxx hardy/restricted Translation-en_US [2093B]
99% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://192.xxx.x.xxx hardy/restricted Translation-en_US
Get:4 http://192.xxx.x.xxx hardy/universe Translation-en_US
Err http://192.xxx.x.xxx hardy/universe Translation-en_US                      
  Connection timed out
Get:5 http://192.xxx.x.xxx hardy/multiverse Translation-en_US                  
Err http://192.xxx.x.xxx hardy/multiverse Translation-en_US                    
  Connection timed out
Get:6 http://192.xxx.x.xxx hardy-security Release.gpg
Err http://192.xxx.x.xxx hardy-security Release.gpg                            
  Connection timed out
Get:7 http://192.xxx.x.xxx hardy-security/main Translation-en_US [2102B]
50% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://192.xxx.x.xxx hardy-security/main Translation-en_US
Get:8 http://192.xxx.x.xxx hardy-security/restricted Translation-en_US
80% [8 Translation-en_US 17227] 
```
If you have any ideas, I would greatly appreciate the help.  Also, I have a 32bit laptop running Hardy, I don't think they use the same repository lists, so I probably shouldn't setup apt-cacher to run on the 32bit laptop and get its updates etc from the 64bit machine correct?  Thanks.

Shane

---

### Post by fahadsadah on 2008-05-06
The repositories are the same; it is the downloaded packages that are sometimes difference.
I would suggest setting apt-cacher on the 32bit, and seeing if it times out too.

---

### Post by shane2peru on 2008-05-06
> **fahadsadah said:**
> The repositories are the same; it is the downloaded packages that are sometimes difference.
I would suggest setting apt-cacher on the 32bit, and seeing if it times out too.

I will have to give that a try, it is just odd that it times out.  Thanks for the info.

Shane

---

### Post by shane2peru on 2008-05-06
Ok, after trying the 32bit laptop with apt-cacher I get the same response, it times out after 99%.  Hmm, perhaps it is how I set it up????  Any ideas would be greatly appreciated.  I know it isn't my firewall, because it would have blocked it completely.  Any ideas????  Perhaps changing ports, would that help????  

Shane

Ok, tried another port, and it is still dreadfully sloooooow!  Any ideas pleas???

---

### Post by saru411 on 2008-05-07
every time i try to dl updates with apt-get on either of my 2 8.04 amd64 pcs i get the same errors as you do. i have decided to downgrade to gutsy because i need stable systems. 8.04 has really let down the community.

---

### Post by shane2peru on 2008-05-07
> **saru411 said:**
> every time i try to dl updates with apt-get on either of my 2 8.04 amd64 pcs i get the same errors as you do. i have decided to downgrade to gutsy because i need stable systems. 8.04 has really let down the community.

I'm not sure you read the whole thread, this is about apt-cacher, not apt-get.  If you have a slow connection, then try a different server.  The servers for hardy have been verrrrrry busssssy because of everyone using them and accessing the data.  I don't think Hardy has been a let down at all.  It has run great on the three computers I have running it.  One has been a little problematic, but that is because of the ATI drivers.  I never ran apt-cacher on Gutsy, so I don't know if it worked or not.  All seems to be good with Hardy here, just the apt-cacher, I'm having a problem getting setup to run correctly.  That could very well be because of my setup.

Shane

---

### Post by saru411 on 2008-05-07
> **shane2peru said:**
> I'm not sure you read the whole thread, this is about apt-cacher, not apt-get.  If you have a slow connection, then try a different server.  The servers for hardy have been verrrrrry busssssy because of everyone using them and accessing the data.  I don't think Hardy has been a let down at all.  It has run great on the three computers I have running it.  One has been a little problematic, but that is because of the ATI drivers.  I never ran apt-cacher on Gutsy, so I don't know if it worked or not.  All seems to be good with Hardy here, just the apt-cacher, I'm having a problem getting setup to run correctly.  That could very well be because of my setup.

Shane

ah I have mistaken your apt-catcher for apt-get. I have been recently reading alot about how Asus Mother boards and Dell laptops have been having internet connection issues. I thought my horrid connection that consistently drops off was due to 8.04 since one of my computers has an Asus board and the laptop is a Dell Vostro.

The things that brought me to this thread were your error messages in the first post.

> Get:2 [http://192.xxx.x.xxx](http://192.xxx.x.xxx) hardy/main Translation-en_US
Err [http://192.xxx.x.xxx](http://192.xxx.x.xxx) hardy/main Translation-en_US 
Ign [http://192.xxx.x.xxx](http://192.xxx.x.xxx) hardy/restricted Translation-en_US
Get:4 [http://192.xxx.x.xxx](http://192.xxx.x.xxx) hardy/universe Translation-en_US
Err [http://192.xxx.x.xxx](http://192.xxx.x.xxx) hardy/universe Translation-en_US                      
  Connection timed out
Get:5 [http://192.xxx.x.xxx](http://192.xxx.x.xxx) hardy/multiverse Translation-en_US                  
Err [http://192.xxx.x.xxx](http://192.xxx.x.xxx) hardy/multiverse Translation-en_US                    
  Connection timed out
Get:6 [http://192.xxx.x.xxx](http://192.xxx.x.xxx) hardy-security Release.gpg
Err [http://192.xxx.x.xxx](http://192.xxx.x.xxx) hardy-security Release.gpg                            
  Connection timed out
Get:7 [http://192.xxx.x.xxx](http://192.xxx.x.xxx) hardy-security/main Translation-en_US

I'm receiving the same errors while using apt-get

---

### Post by shane2peru on 2008-05-07
> **saru411 said:**
> ah I have mistaken your apt-catcher for apt-get. I have been recently reading alot about how Asus Mother boards and Dell laptops have been having internet connection issues. I thought my horrid connection that consistently drops off was due to 8.04 since one of my computers has an Asus board and the laptop is a Dell Vostro.

The things that brought me to this thread were your error messages in the first post.



I'm receiving the same errors while using apt-get

Right I could see how someone could confuse this issue with your issue.  Not a problem. :)

Shane

---

