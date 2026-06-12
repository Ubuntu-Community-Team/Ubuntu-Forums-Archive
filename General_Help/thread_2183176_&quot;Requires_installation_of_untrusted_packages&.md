---
title: "&quot;Requires installation of untrusted packages&quot; error while using ubuntu softwarecenter"
date: 2013-10-23
forum: General Help
---

### Post by coffeepenguin on 2013-10-23
Whennever I try to download something from ubuntu software center I always get and erro with the title "Requires installation of untrusted packages" and the subtitle "This requires installing packages from unauthenticated sources." 

The details vary though. While downloading ubuntu restricted extras I got
 "s-2.0-0 libmpeg2encpp-2.0-0 libmplex2-2.0-0 ubuntu-restricted-extras unrar"
"streamer0.10-plugins-bad-multiverse libfaac0 libmjpegutils-2.0-0 libmpeg2encpp-2.0-0 libmplex2-2.0-0 ubuntu-restricted-extras unrar"
"gstreamer0.10-plugins-bad-multiverse libfaac0 libmjpegutils-2.0-0 libmpeg2encpp-2.0-0 libmplex2-2.0-0 ubuntu-restricted-extras unrar"
and so on.

I have the option to either click ok to abort or repair whitch displays the next error. No matter whitch one I click I never succeed in downloading anything from the software center.

Edit: I am also using ubuntu version 13.10

---

### Post by coffeepenguin on 2013-10-23
I have been looking through the forums for a few hours, and I still can't figure out how to get it to work.

I read about  sudo apt-get update in another post, but it isn't working, here are the results.
```
han_solo@MilleniumFalcon:~$ sudo apt-get update
Ign http://us.archive.ubuntu.com saucy InRelease
Ign http://us.archive.ubuntu.com saucy-updates InRelease
Ign http://security.ubuntu.com saucy-security InRelease
Ign http://extras.ubuntu.com saucy InRelease   
Ign http://us.archive.ubuntu.com saucy-backports InRelease
Get:1 http://security.ubuntu.com saucy-security Release.gpg [933 B]
Get:2 http://us.archive.ubuntu.com saucy Release.gpg [933 B]          
Get:3 http://extras.ubuntu.com saucy Release.gpg [72 B]               
Get:4 http://us.archive.ubuntu.com saucy-updates Release.gpg [933 B]  
Hit http://security.ubuntu.com saucy-security Release                 
Ign http://security.ubuntu.com saucy-security Release                 
Get:5 http://us.archive.ubuntu.com saucy-backports Release.gpg [933 B]
Hit http://extras.ubuntu.com saucy Release                            
Err http://extras.ubuntu.com saucy Release                            
  
Hit http://us.archive.ubuntu.com saucy Release                        
Ign http://us.archive.ubuntu.com saucy Release                        
Ign http://security.ubuntu.com saucy-security/main Sources/DiffIndex  
Get:6 http://us.archive.ubuntu.com saucy-updates Release [49.6 kB]
Err http://us.archive.ubuntu.com saucy-updates Release                
  
Hit http://us.archive.ubuntu.com saucy-backports Release              
Ign http://us.archive.ubuntu.com saucy-backports Release              
Ign http://security.ubuntu.com saucy-security/restricted Sources/DiffIndex
Ign http://security.ubuntu.com saucy-security/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com saucy/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com saucy/restricted Sources/DiffIndex
Ign http://security.ubuntu.com saucy-security/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com saucy/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com saucy/multiverse Sources/DiffIndex
Ign http://security.ubuntu.com saucy-security/main amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy/main amd64 Packages/DiffIndex
Ign http://security.ubuntu.com saucy-security/restricted amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy/restricted amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy/universe amd64 Packages/DiffIndex
Ign http://security.ubuntu.com saucy-security/universe amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy/multiverse amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy/main i386 Packages/DiffIndex
Ign http://security.ubuntu.com saucy-security/multiverse amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy/restricted i386 Packages/DiffIndex
Ign http://security.ubuntu.com saucy-security/main i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy/universe i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy/multiverse i386 Packages/DiffIndex
Ign http://security.ubuntu.com saucy-security/restricted i386 Packages/DiffIndex
Hit http://us.archive.ubuntu.com saucy/main Translation-en
Ign http://security.ubuntu.com saucy-security/universe i386 Packages/DiffIndex
Hit http://us.archive.ubuntu.com saucy/multiverse Translation-en
Ign http://security.ubuntu.com saucy-security/multiverse i386 Packages/DiffIndex
Hit http://us.archive.ubuntu.com saucy/restricted Translation-en
Hit http://security.ubuntu.com saucy-security/main Translation-en
Hit http://us.archive.ubuntu.com saucy/universe Translation-en
Ign http://us.archive.ubuntu.com saucy-backports/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com saucy-backports/restricted Sources/DiffIndex
Ign http://us.archive.ubuntu.com saucy-backports/universe Sources/DiffIndex
Hit http://security.ubuntu.com saucy-security/multiverse Translation-en
Ign http://us.archive.ubuntu.com saucy-backports/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com saucy-backports/main amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy-backports/restricted amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy-backports/universe amd64 Packages/DiffIndex
Hit http://security.ubuntu.com saucy-security/restricted Translation-en
Ign http://us.archive.ubuntu.com saucy-backports/multiverse amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy-backports/main i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy-backports/restricted i386 Packages/DiffIndex
Hit http://security.ubuntu.com saucy-security/universe Translation-en
Ign http://us.archive.ubuntu.com saucy-backports/universe i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy-backports/multiverse i386 Packages/DiffIndex
Hit http://security.ubuntu.com saucy-security/main Sources
Hit http://us.archive.ubuntu.com saucy-backports/main Translation-en
Hit http://security.ubuntu.com saucy-security/restricted Sources
Hit http://security.ubuntu.com saucy-security/universe Sources
Hit http://us.archive.ubuntu.com saucy-backports/multiverse Translation-en
Hit http://security.ubuntu.com saucy-security/multiverse Sources
Hit http://security.ubuntu.com saucy-security/main amd64 Packages
Hit http://us.archive.ubuntu.com saucy-backports/restricted Translation-en
Hit http://security.ubuntu.com saucy-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com saucy-backports/universe Translation-en
Hit http://us.archive.ubuntu.com saucy/main Sources
Hit http://security.ubuntu.com saucy-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com saucy/restricted Sources
Hit http://security.ubuntu.com saucy-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com saucy/universe Sources
Hit http://us.archive.ubuntu.com saucy/multiverse Sources
Hit http://security.ubuntu.com saucy-security/main i386 Packages
Hit http://us.archive.ubuntu.com saucy/main amd64 Packages
Hit http://us.archive.ubuntu.com saucy/restricted amd64 Packages
Hit http://security.ubuntu.com saucy-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com saucy/universe amd64 Packages
Hit http://us.archive.ubuntu.com saucy/multiverse amd64 Packages
Hit http://security.ubuntu.com saucy-security/universe i386 Packages
Hit http://us.archive.ubuntu.com saucy/main i386 Packages
Hit http://us.archive.ubuntu.com saucy/restricted i386 Packages
Hit http://us.archive.ubuntu.com saucy/universe i386 Packages
Hit http://security.ubuntu.com saucy-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com saucy/multiverse i386 Packages
Hit http://us.archive.ubuntu.com saucy-backports/main Sources         
Hit http://us.archive.ubuntu.com saucy-backports/restricted Sources   
Hit http://us.archive.ubuntu.com saucy-backports/universe Sources     
Hit http://us.archive.ubuntu.com saucy-backports/multiverse Sources   
Hit http://us.archive.ubuntu.com saucy-backports/main amd64 Packages  
Hit http://us.archive.ubuntu.com saucy-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com saucy-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com saucy-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com saucy-backports/main i386 Packages   
Hit http://us.archive.ubuntu.com saucy-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com saucy-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com saucy-backports/multiverse i386 Packages
Ign http://security.ubuntu.com saucy-security/main Translation-en_US  
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_US
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_US
Ign http://security.ubuntu.com saucy-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com saucy/main Translation-en_US         
Ign http://us.archive.ubuntu.com saucy/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com saucy/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com saucy/universe Translation-en_US     
Ign http://us.archive.ubuntu.com saucy-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com saucy-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com saucy-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com saucy-backports/universe Translation-en_US
Fetched 3,805 B in 10s (372 B/s)                                      
Reading package lists... Done
W: GPG error: http://security.ubuntu.com saucy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: GPG error: http://us.archive.ubuntu.com saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com saucy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32

W: GPG error: http://us.archive.ubuntu.com saucy-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/saucy/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by oldos2er on 2013-10-24
You can add the missing keys with ```
sudo apt-key adv --keyserver hkp://subkeys.pgp.net --recv-keys 40976EAF437D05B5 
``` Replace the alphanumeric string given with each warning. After you've added them all run ```
sudo apt-get update
```

---

### Post by coffeepenguin on 2013-10-24
Thanks you so much!!!! I did what you said and when I finished I was able to receive downloads from the software center!

---

