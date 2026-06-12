---
title: "Error message when updating"
date: 2016-06-07
forum: General Help
---

### Post by UncleMonty on 2016-06-07
I get the following error message when updating. Advice please: 


W: [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:) Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:) Signature by key 3B068FB4789ABE4AEFA3BB491397BC53640DB551 uses weak digest algorithm (SHA1)

---

### Post by uRock on 2016-06-07
Looks like Debian and Ubuntu recently started enforcing a requirement for stronger algorithms. We will have to wait for Google to upgrade on their end to meet the requirements. They are no less secure than they were in the past.

More info found [here]("https://askubuntu.com/questions/760796/how-to-fix-apt-signature-by-key-uses-weak-digest-algorithm-sha1-after-install")  and [here]("https://juliank.wordpress.com/2016/03/14/dropping-sha-1-support-in-apt/").

---

### Post by QDR06VV9 on 2016-06-07
Thanks uRock this is the first I have seen this fix.
> Adding this to the gpg.conf on the repository machine avoids this problem

cert-digest-algo SHA256
digest-algo SHA256


Kind Regards

---

### Post by UncleMonty on 2016-06-07
I hate to sound like a noob, but how do I access the gpg.conf please?

---

### Post by uRock on 2016-06-07
That's a good question. I just search the / and the /home and didn't find a gpg.conf file.

---

### Post by QDR06VV9 on 2016-06-07
It is in /etc/apt...But it is rather complex to change.
But this has been working so far.
```
**wget -q -O - [https://dl.google.com/linux/linux_signing_key.pub](https://dl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -**

```
Let us know if it no longer works.

---

### Post by uRock on 2016-06-07
> **runrickus said:**
> It is in /etc/apt...But it is rather complex to change.
But this has been working so far.
```
**wget -q -O - [https://dl.google.com/linux/linux_signing_key.pub](https://dl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -**

```
Let us know if it no longer works.

I ran it, it said Ok, but I still get the message about the strength. Hopefully Google and the other vendors having this issue will get with the game soon.

---

### Post by QDR06VV9 on 2016-06-07
I may be just spitting in the wind now..but do you want to try this one also?
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 1397BC53640DB551
```
These two commands have been working at least till now.

---

