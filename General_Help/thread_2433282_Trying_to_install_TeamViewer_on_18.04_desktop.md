---
title: "Trying to install TeamViewer on 18.04 desktop"
date: 2019-12-16
forum: General Help
---

### Post by cenriq on 2019-12-16
Hi All,

Tried to install TeamViewer on my Ubuntu 18.04 desktop, but it did not work. I followed  this link: [https://community.teamviewer.com/t5/Knowledge-Base/How-to-install-TeamViewer-on-Ubuntu/ta-p/45](https://community.teamviewer.com/t5/Knowledge-Base/How-to-install-TeamViewer-on-Ubuntu/ta-p/45)

It seems to be doing the install but when it done, it does not show up in Activities as suggested in the how to.  Pls advise. Thanks.

---

### Post by gsahli on 2019-12-16
I don't see anything about activities in the guide. Maybe they updated the guide?
Which desktop are you using? (where you need to look depends on this info)

---

### Post by howefield on 2019-12-17
If you don't mind using the terminal, do you get a response to the following command..

```
which teamviewer
```

---

### Post by Autodave on 2019-12-17
Did you look under the "internet" in "places" to find it?  I have it running on several machines here and never an issue.

---

### Post by cenriq on 2019-12-17
no response to "which teamviewer".

Don't seem to have "Internet" and "Places" on machine.

---

### Post by howefield on 2019-12-17
> **cenriq said:**
> no response to "which teamviewer".

Seems not to have been installed after all ?

The response should have been something like 

```
/usr/bin/teamviewer
```

I'd suggest downloading again in case you have a corrupt download and use the terminal to install. You can simulate an install with the following.. (change your username, file name and download path to suit)

```
sudo apt install -s /home/hugh/Downloads/teamviewer_15.1.3937_amd64.deb
```

If all goes well and there seem to be no errors, you can repeat the command without the -s switch to install for real.

---

### Post by cenriq on 2019-12-17
had tried downloading a couple times, but had same results. Will try  to simulate the install.

E: Unsupported file /home/tine/downloads/teamviewer_15.0.8397_amd64.deb given on commandline


That's the response I receive when I try to simulate the install.

My bad. Downloads should have had a capital "D".

Will try the real install now.

Wow it worked!!!!! Thanks for your assistance. Don't know why it doesn't work using the other method.

---

### Post by howefield on 2019-12-17
> **cenriq said:**
> E: Unsupported file /home/tine/downloads/teamviewer_15.0.8397_amd64.deb....

The current downloadable version from teamviewer.com is 15.1.3937, released today. You seem to be getting the previous version, should still work well enough.

It's usually best to copy/paste the actual terminal code to your postings. The downloads folder is usually capitalised.. is this a mistake in your post ?

PS. Cool, we posted simultaneously, glad it worked :)

---

