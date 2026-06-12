---
title: "Picture sharing over the internet with the family"
date: 2017-03-14
forum: General Help
---

### Post by 5h4d3 on 2017-03-14
Dear all,

I'm looking for a way of granting access to my pictures to the rest of my family over the internet and vice versa (few hundred of GB each, living several hundred miles apart from each other). Ideally - the solution would include some kind of preview function for pictures [let me dream: for raw files, too].

Initially, I was thinking of setting up a privat & password protected Direct Connect Hub on my ubuntu server, as you could log in from any system/OS and download/upload whenever the other one is online anyways.
Unfortunately, Direct Connect seems to be quite dead recently (at least I didn't find a hub software that did get a security patches or updates in the last year) & I couldn't find a package which would then be easily maintained on the server ;).

I feel like not seeing the elephant in the room, as I'm probably not the first one with thet kind of idea/requirement. Hence my question: Is there a ubuntu package I could have a closer look at which would allow this kind of setup?

Thank you very much,
Mat

---

### Post by TheFu on 2017-03-14
Not Ubuntu specific, but here are many "gallery" web-apps. You'll need to run a web server.  Use HTTPS and if you can, block any IPs that you don't know other family will use.  Adding "basic authentication" (a password) to access the web areas would be smart too.  Just be aware that these webapps are highly hackable and need manual maintenance if there is ever any issues with the code.

There is also Nextcloud/Owncloud. Same issues - want HTTPS, block IPs that shouldn't have access and use passwords for the different users. Nextcloud has a gallery photo app which shows previews.  In the last 3 months, I've updated Nextcloud 3 times.  For my needs, we don't allow direct access over the internet without using a full VPN.

There is a project called sovereign on github for all your self-hosting needs.  [https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign) lots of great things in there.

None of these are "install and forget."  Running a server has inherent risks and demands security considerations.

If you want, you could also use something like rsync over ssh to push/pull files.  I use rsync to replicate my password manager DB across multiple devices (6).

---

### Post by HereInOz on 2017-03-14
If you have an Ubuntu server which is on all the time, consider ownCloud.  I run an ownCloud server and it is so easy to create several user profiles, with usernames and passwords, then share particular files and folders which are in your profile with other users of the system.

You will have to install apache2 to run the web server side of things.

ownCloud runs as default using an SQLite database, but works a heap better if you take the trouble to install MariaDB or MySQL and configure it to use that database.  I set it up as a plaything a few years ago, and now I wouldn't be without it.

---

### Post by mastablasta on 2017-03-15
you definitelly need MariaDB or MySQL on owncloud.

alternatively the Piwigo galery app will also do what you need.

> Piwigo 2.8 supports multiple format. It means you can provide several versions of the very same photo. For example a RAW file, a TIFF, a CMYK profile and a zip. In Piwigo 2.8, multiple format is only available on synchronization. We will make web upload compatible in next versions of Piwigo.

[SIZE=2]http://piwigo.org/
[/SIZE]

---

### Post by 5h4d3 on 2017-03-15
Hi all,

Thank you very much for the tips, they look very interesting (i think of installing owncloud for me now :) ). However, the reason I was looking into file sharing solutions is due to 2 limitations I have:

1) my server does not have enough storage space to support all the pictures
2) even if it had it would take ages to upload all pictures as the internet connection's upload speed is limited. 

Best regards,
Mat

---

### Post by sp40140 on 2017-03-15
I suggest Tonido.
[http://www.tonido.com/](http://www.tonido.com/)
I have been using it for few years now. Very good. Plus all the mobile platforms have good apps. Similar to dropbox with one essential difference that all the files are hosted on your machine and no limit to storage.

Cheers

---

### Post by SeijiSensei on 2017-03-15
> **5h4d3 said:**
> 1) my server does not have enough storage space to support all the pictures
2) even if it had it would take ages to upload all pictures as the internet connection's upload speed is limited.

One possibility might be to leave the photos where they are now and set up a [static OpenVPN tunnel]("http://openvpn.net/static.html") between the server and the machine where the pictures are stored.  Most photo gallery apps have a thumbnailing function which would create much smaller images on the server, while requests for the full-size images would be fulfilled by the current server over the tunnel.

---

### Post by mastablasta on 2017-03-15
> **5h4d3 said:**
> 
1) my server does not have enough storage space to support all the pictures
2) even if it had it would take ages to upload all pictures as the internet connection's upload speed is limited. 




what do you want the server to be doing then?

if it is not serving the pictures, then you can use any of the available commercial cloud (Google pics or whatever it is called now, dropbox...)

the only other option woul dbe you would rent space somewhere and then use home server to direct traffic there via a web app. in the end this could prove more expencive.

do the Pictures need to be in some large format to enjoy them? if not you could reduce them (en masse) in size and then host them. a galery app would display thumbnails before loading them.

a few hunderd GB is a alot of data to transfer...

---

### Post by HermanAB on 2017-03-15
Retroshare is probably the best:
[http://retroshare.net/](http://retroshare.net/)

It does everything and it is secure.

---

### Post by 5h4d3 on 2017-03-15
Hi Herman,

Thank you very much,

this looks like what I'm looking for! 

Cheers,
Mat

---

### Post by TheFu on 2017-03-15
Retroshare is interesting. [http://secushare.org/comparison](http://secushare.org/comparison) shows it favorably if you use TOR too.
If security isn't THAT important, Opera has a file-sharing mode (or at least it did 5 yrs ago).

---

