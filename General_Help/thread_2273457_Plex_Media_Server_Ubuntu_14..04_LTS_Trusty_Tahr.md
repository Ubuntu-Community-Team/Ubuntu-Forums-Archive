---
title: "Plex Media Server Ubuntu 14..04 LTS Trusty Tahr"
date: 2015-04-13
forum: General Help
---

### Post by mdavis1231 on 2015-04-13
My Synaptic Package Manager is showing that there's an update for Plex Media Server on my Ubuntu 14.04 LTS Trusty Tahr, but it won't let me upgrade to 0.9.11.16.  What could possibly be wrong?  I'm getting the error message "E: /var/cache/apt/archives/plexmediaserver_0.9.11.16.958-80f1748-debian_amd64.deb: subprocess new pre-removal script returned error exit status 1". :confused:

---

### Post by papibe on 2015-04-13
Hi mdavis1231.

In case it is a problem with the packaging system, try this:
```
sudo apt-get clean
sudo apt-get update
```
If that gives you no error, then:
```
sudo apt-get upgrade
```
If you are still experimenting the same error, try this:
```
sudo dpkg --configure -a
sudo apt-get -f install
```
If that doesn't work, you may try this fix from the plex forums.
```
sudo mv -v /etc/init.d/plexmediaserver /etc/init.d/plexmediaserver.old
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by ajgreeny on 2015-04-13
You have to download and install updates manually for Linux, I think.  I have just gone to my plex management page in firefox ->Settings ->Server and it tells me there is a new version but to "Please install manually" and incidentally, I do not get any notification in synaptic for my 14.04 ubuntu install.  Go to [https://plex.tv/downloads](https://plex.tv/downloads) to get the server

Did you install manually in the first place or have you enabled a plexmediaserver ppa that I'm not aware of?  I thought only the plex-theatre was available from a ppa.

---

### Post by mdavis1231 on 2015-04-13
After I run "sudo mv -v /etc/init.d/plexmediaserver /etc/init.d/plexmediaserver.old" in terminal, what do I do then?  Try and upgrade again?

---

### Post by papibe on 2015-04-13
Yes:
```
sudo apt-get upgrade plexmediaserver
```
Let us know how that goes.
Regards.

---

### Post by mdavis1231 on 2015-04-13
Worked like a charm!!!  You solved my problem, and thank you SO MUCH!!!

---

### Post by mdavis1231 on 2015-04-14
I'm sorry that I don't have the exact website address, but you can Google it and follow the instructions to add the 2 PPA's to your Ubuntu Software Sources.  I do know that they are actually Debian Wheezy PPA's, and it does involve installing Curl on your Ubuntu.  But you want to be REALLY careful with this, because it broke some of my packages and I spent about 1/2 a day getting everything sorted out.

OK, I did manage to find the website.  It's "http://www.htpcguides.com/install-plex-media-server-ubuntu-14-04/".  But like I said, be very careful, and only use the instructions on this website if you're willing to do a little work afterwards on getting all the packages sorted out in your Synaptic Package Manager.  But I think that after it was all over, that for me it was worth it, because I have the absolute newest version on my Ubuntu 14.04 LTS Trusty Tahr, and I didn't have to fool with the .deb packages.

---

### Post by ajgreeny on 2015-04-14
I've just looked at your ppa link and I think I would prefer to keep manual control over updating the server; it requires nothing more than an occasional look at the settings of plexmediaserver in a web browser and then manually downloading and installing the deb file if an update is available.

It takes only a couple of minutes at most and has never yet caused me any difficulties of any sort.

---

