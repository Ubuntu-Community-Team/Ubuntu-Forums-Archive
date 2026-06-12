---
title: "problem installing wget in ubuntu 14.04 LTS"
date: 2015-05-26
forum: General Help
---

### Post by thomas52 on 2015-05-26
hi friends,
 i have problem instaling wget in ubuntu 14.04  LTS 32 bit.  can u please help me out.
thanks.

---

### Post by Lars Noodén on 2015-05-26
wget is already part of the base system.  What are you trying to do?

---

### Post by thomas52 on 2015-05-26
thanks, yes i know that it is included in the base system but i want wget with a complete GUI just like the image i have attached. thanks

---

### Post by thomas52 on 2015-05-26
please refer to the image attached, thanks.

---

### Post by Lars Noodén on 2015-05-26
***g**wget* is something different from wget and from the looks of it is for GNOME2.  Ubuntu no longer uses GNOME 2 and the latest gwget seems to be from 2009.  It will be some work to [port](https://en.wikipedia.org/wiki/Porting) it to Unity.  

What are you looking for in a download manager?  There are add-ons for your browser that might meet those needs.

---

### Post by thomas52 on 2015-05-26
> **Lars Noodén said:**
> ***g**wget* is something different from wget and from the looks of it is for GNOME2.  Ubuntu no longer uses GNOME 2 and the latest gwget seems to be from 2009.  It will be some work to [port]("https://en.wikipedia.org/wiki/Porting") it to Unity.  

What are you looking for in a download manager?  There are add-ons for your browser that might meet those needs.

thanks.

you are right. i have no idea about the exact difference between two of them. below are the commands i executed in terminal as root in order to install both of them one by one.

```


root@thomas-H61M-DS2:~# apt-get install gwget
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gwget
root@thomas-H61M-DS2:~# 
root@thomas-H61M-DS2:~# 
root@thomas-H61M-DS2:~# apt-get install wget
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wget is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 567 not upgraded.
root@thomas-H61M-DS2:~# ^C
root@thomas-H61M-DS2:~# 



```

---

### Post by thomas52 on 2015-05-26
> **Lars Noodén said:**
> There are add-ons for your browser that might meet those needs.

ok. can you please suggest me a few good and reliable download managers that can be installed as Firefox add-ons ?
thanks

---

### Post by Lars Noodén on 2015-05-26
> **thomas52 said:**
> 
```

root@thomas-H61M-DS2:~# apt-get install wget
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wget is already the newest version.

```

As mentioned, [wget](http://manpages.ubuntu.com/manpages/trusty/en/man1/wget.1.html) is already the installed in the base system.  What capabilities are you looking for in a download manager?  There are [over 700 download managers for Firefox](https://addons.mozilla.org/en-US/firefox/extensions/download-management/?sort=popular) alone.  I only use the one built into Firefox which does start/stop/resume already.

---

### Post by v3.xx on 2015-05-26
Over 700, thats a lot!  Anyhow, here's one

[https://addons.mozilla.org/en-US/firefox/addon/downthemall/](https://addons.mozilla.org/en-US/firefox/addon/downthemall/)

---

### Post by thomas52 on 2015-05-26
> **v3.xx said:**
> Over 700, thats a lot!  Anyhow, here's one

[https://addons.mozilla.org/en-US/firefox/addon/downthemall/](https://addons.mozilla.org/en-US/firefox/addon/downthemall/)

thankyou this add-on solved my problem.

---

### Post by v3.xx on 2015-05-26
Welcome and don't forget

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

