---
title: "Problem using apt-get update"
date: 2008-05-27
forum: General Help
---

### Post by Avinash.Rao on 2008-05-27
Hi Guys,

I just finished the installation of Ubuntu 7.0. There was no internet connection during installation. The installation was completed without any error. 

After the installation, i am not able to install any package using apt-get or aptitude. I have configured the network and internet and they are working fine. 

When i execute sudo apt-get update - i get the following error.

Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz)  Could not resolve 'archive.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

How do i solve this and configure my machine to download and install updates using apt-get

Thanks
Avinash

---

### Post by 505 on 2008-05-27
Somehow it seems that your computer cannot find the update server. The server might be down (try again later), or something at your side is wrong. First try the ping the update server by running
```
ping archive.ubuntu.com
```
If that doesn't work, try to ping [www.google.com](www.google.com), just to make sure that works. If you can ping google but not the update server the request is blocked by your computer. Do you have any firewalls or port blockers running on either your computer or router?

---

### Post by Avinash.Rao on 2008-05-27
I am able to browse the internet. Infact, i am writing from the same computer.

I am not able to ping archive.ubuntu.com not google.com But, i am able to access these sites using a browser.

the ping command returns the following error. ping: unknown host archive.ubuntu.com

Yes, the internet works through a proxy. But, other computers are able to access these sites through the proxy.

Thanks
Avinash

---

### Post by sdennie on 2008-05-27
Depending on where you live, I think the local ubuntu archives aren't always stable.  I would try the following:

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak

```

Then,

```

gksudo gedit /etc/apt/sources.list

```

Change all the "archive.ubuntu.com" urls to something like "us.archive.ubuntu.com".  Then,

```

sudo apt-get update

```

If if doesn't work, just:

```

sudo cp /etc/apt/sources.list.bak /etc/apt/sources.list

```

And no harm done.

---

### Post by danwood76 on 2008-05-27
I think your issue is with the Proxy, Im assuming youve setup firefox to run through the proxy aswell.

What sort of proxy are you running through and what is its purpose?

---

### Post by Avinash.Rao on 2008-05-27
I made the changes but the problem still exists.

I am using proxy to share the internet connection. But, when i am able to access archive.ubuntu.com using a browser, why is apt-get update not working?

I doubt if its a problem with the proxy.

Avinash

---

### Post by sdennie on 2008-05-27
I've never used a proxy before but, does configuring System->Preferences->Network Proxy help the situation?

---

### Post by danwood76 on 2008-05-27
Check that you have the proxy setup correctly in the network manager control panel.
It does sound like a proxy issue, firefox can be setup seperatly to use a proxy which I assume you have done.

---

### Post by Avinash.Rao on 2008-05-28
> **vor said:**
> I've never used a proxy before but, does configuring System->Preferences->Network Proxy help the situation?


Yes, it worked, i entered the proxy server address in the Network Proxy tool. 
Now, i am able to use apt-get command!

Thanks :)
Avinash

---

