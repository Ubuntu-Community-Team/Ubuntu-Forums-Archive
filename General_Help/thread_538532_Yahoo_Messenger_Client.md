---
title: "Yahoo Messenger Client"
date: 2007-08-30
forum: General Help
---

### Post by bogdan_5844 on 2007-08-30
hello,i don't think that i posted in the correct section,but i didn't found another one to fit well...
My question: 
Can somebody recommend a Yahoo messenger client wich supports Offline Messages,the BUZZ feature and avatars?I tried Kopete,GAIM and Gyiache(i think this is what it is spelled like)
Thanks in advance

---

### Post by jusmurph on 2007-08-30
Have you tried pidgin?

Pidgin is the new version of GAIM, Just i don't use yahoo so i have no idea about its support for these things.

[http://www.getdeb.net/release.php?id=1308](http://www.getdeb.net/release.php?id=1308)

---

### Post by be4truth on 2007-08-30
GyachI is a Yahoo! Messenger client for Linux operating system supports almost all of the features you would expect to find on the official Windows Yahoo! client: Voice chat, webcams, faders, 'nicknames', audibles, avatars, display images, and more. Yet, it remains very light-weight and memory-friendly. GyachE Improved uses Gtk-2 for its user interfaces

```
sudo apt-get install gyachi
```

---

### Post by bogdan_5844 on 2007-08-30
i use pidgin...it's great but i miss the Buzz feature :( Gyachi is too cluttered

---

### Post by z0mbie on 2007-08-30
I wonder why Yahoo discontinued their Unix/Linux client.

---

### Post by bogdan_5844 on 2007-08-30
me to...even the mac version is in development....i think they don't know that they are losing an important part of marketing...oh well....i hope that with the rewrite of ver.9 for win,they will update the linux ver....or at least delete the page:)

---

### Post by por100pre1 on 2007-08-30
> **be4truth said:**
> GyachI is a Yahoo! Messenger client for Linux operating system supports almost all of the features you would expect to find on the official Windows Yahoo! client: Voice chat, webcams, faders, 'nicknames', audibles, avatars, display images, and more. Yet, it remains very light-weight and memory-friendly. GyachE Improved uses Gtk-2 for its user interfaces

```
sudo apt-get install gyachi
```

I don't think gyachi is in the repos. [This link]("http://prdownloads.sourceforge.net/gyachi/gyachi_1.0.5-1_edgy_i386.deb?download") should do the job.

---

### Post by kuja on 2007-08-30
> **bogdan_5844 said:**
> hello,i don't think that i posted in the correct section,but i didn't found another one to fit well...
My question: 
Can somebody recommend a Yahoo messenger client wich supports Offline Messages,the BUZZ feature and avatars?I tried Kopete,GAIM and Gyiache(i think this is what it is spelled like)
Thanks in advance
Kopete *does* support those features. In fact I use them to death.

> **z0mbie said:**
> I wonder why Yahoo discontinued their Unix/Linux client.

Who cares, it sucked anyway ...

---

### Post by bogdan_5844 on 2007-08-30
i know that kopete supports those features,but it annoys me that you have to put smileys between two spaces(try typing something like: "hello:)" in kopete,then type the same thing in GAIM/Pidgin,you'll see what I'm talking about)

---

### Post by kuja on 2007-08-30
> **bogdan_5844 said:**
> i know that kopete supports those features,but it annoys me that you have to put smileys between two spaces(try typing something like: "hello:)" in kopete,then type the same thing in GAIM/Pidgin,you'll see what I'm talking about)

I always considered that to be more of a feature myself, take this for example, how the forum would display it:

(67 - 58) * 4
( 67 - 58 ) * 4
 
(Just using something random for an example)

---

### Post by por100pre1 on 2007-08-30
> **kuja said:**
> I always considered that to be more of a feature myself, take this for example, how the forum would display it:

(67 - 58) * 4
( 67 - 58 ) * 4
 
(Just using something random for an example)

Agree. i think it is a feature. :)

---

### Post by linux.spider on 2007-09-01
I cannot for the life of me get into a yahoo chat room using gyachi...must be one of there newest security blunders blocking me :(

---

### Post by loell on 2007-09-01
actually you can but inconviniently, by launching it in the terminal, then enable packet debugging, when you enter into the room, the captcha is displayed into the terminal, copy and paste it into the browser and answer the captcha.

this has been fixed in gyachi's cvs though.

---

### Post by sabitha on 2007-09-01
> **loell said:**
> actually you can but inconviniently, by launching it in the terminal, then enable packet debugging, when you enter into the room, the captcha is displayed into the terminal, copy and paste it into the browser and answer the captcha.

this has been fixed in gyachi's cvs though.
so when gyachi (.deb) come with this fix loell. sorry if i ask that because all of my customers (internet cafe) complains about that too :( ...

---

### Post by jrusso2 on 2007-09-01
> **loell said:**
> actually you can but inconviniently, by launching it in the terminal, then enable packet debugging, when you enter into the room, the captcha is displayed into the terminal, copy and paste it into the browser and answer the captcha.

this has been fixed in gyachi's cvs though.

Loell did you update your version of gyachi with this fix?  If so where can we download your sidetrack version?

---

### Post by loell on 2007-09-02
hi all gyachi room chatters, instead of updating the sidetrack version, i just built the cvs version, which have some noticeable imrovements along with the captcha fix.

here is the download link [http://www.mediafire.com/?1gvxzt47p9j]("http://www.mediafire.com/?1gvxzt47p9j")

---

### Post by sabitha on 2007-09-02
thanks loell but it just can open with opera how can i make gyachi open firefox. anyway thanks for the new CVS version.

---

### Post by loell on 2007-09-02
> **sabitha said:**
> thanks loell but it just can open with opera how can i make gyachi open firefox. anyway thanks for the new CVS version.

you can set it to firefox by going to setup menu --> options tab -->  click the mozilla button

---

