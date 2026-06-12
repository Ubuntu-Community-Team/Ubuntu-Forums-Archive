---
title: "Ubuntu One Account not recognized by &quot;Software&quot;"
date: 2017-01-07
forum: General Help
---

### Post by thomasweiss92 on 2017-01-07
Hi guys,

I have a tiny problem. I recently installed Xubuntu and wanted to install VLC, 'cause Xubuntu doesn't have it. In order to download VLC I need an Ubuntu One Account, which I have. But, Software doesn't recognize my account at al. I tried changing my password, even deleted the account and registered again. Still the same. I also restarted Software, only to make sure it's not because of that. Well, it was the same as before. Can someone tell me how to get my Ubuntu One Account to be recognized by Software? Thanks so much :)

---

### Post by howefield on 2017-01-07
Sounds like you are trying to install the snap version of VLC from the Software Centre which unlike the .deb packages will require logging in with an SSO account ?

If that is the case then there is a problem installing any snap package from the Software Centre, I'd suggest installing it from the command line... eg

```
sudo snap login xxxxxxxx@xxxxx.com
[sudo] password for hugh: 
Password: 
Login successful
snap install vlc
vlc (stable) daily from 'videolan' installed
```

After using the sudo snap login command you may be asked for your sudo password and then your SSO login password, easy to get confused ;)

If it is the "traditional" VLC package that you are looking for then install it, again at the command line with..

```
sudo apt-get install vlc
```

---

### Post by Impavidus on 2017-01-07
An Ubuntu One account to install vlc? I don't think so. Maybe for paid software, I don't know as I never used any of that, but not vlc. You need your ordinary password, that you also use to login and for sudo.

I know Software may be a little buggy sometimes. Synaptic is better and used to be the standard. You can also install from terminal. To install vlc:```
sudo apt install vlc
```To install synaptic:```
sudo apt install synaptic
```That is assuming you run 16.04 or 16.10, on 14.04 it's still apt-get instead of apt, but in that case you better upgrade because Xubuntu 14.04 is almost end-of-life.

Edit: OK, I didn't know about snap. Never used that either.

---

### Post by howefield on 2017-01-07
If this is the screen (attached image) that you are getting, then it is the snap version that you are trying to install... the difference between this and the .deb package version is that the snap version is a "daily" snapshot of the software whilst the deb package is the version released with 16.04 last year.

Please note in the screenshot that there are 2 icons for vlc. Revealing the details for each would show one marked as the "daily" version, in other words the snap package. It won't install without an SSO account which in any event will fail due to a current bug regarding installing snaps from the Software Centre, the other package should install just fine, either from the Software Centre or as I mentioned above, from the command line.

---

