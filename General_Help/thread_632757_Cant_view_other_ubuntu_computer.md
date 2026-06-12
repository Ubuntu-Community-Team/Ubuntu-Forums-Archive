---
title: "Cant view other ubuntu computer"
date: 2007-12-05
forum: General Help
---

### Post by jasonpeinko on 2007-12-05
I cannot get my laptop and desktop both running ubuntu to reconize the other on the network. Any idea?

---

### Post by stalker145 on 2007-12-05
> **jasonpeinko said:**
> I cannot get my laptop and desktop both running ubuntu to reconize the other on the network. Any idea?

What exactly do you mean by 'recognize the other'? Are you wishing to SSH, file share, VNC?

---

### Post by jasonpeinko on 2007-12-05
file sharing, when i go under network neither computer finds the other.

---

### Post by HermanAB on 2007-12-05
Well, at least one side has to run a server and by default Ubuntu runs none - well except for Xorg.  So install openssl, or proftpd at least on one of the machines. If you are adventurous, install Samba, but that is not so easy as it should be.

Cheers,

Herman

---

### Post by BLTicklemonster on 2007-12-05
Look at my sig, see if that helps any.

---

### Post by jasonpeinko on 2007-12-05
i have samba on my desktop one, should i try openssl or proftpd?

---

### Post by BLTicklemonster on 2007-12-05
Would it be better to have samba on both of the machines?

---

### Post by jasonpeinko on 2007-12-05
i think i have it on my laptop too just not configured

---

### Post by stalker145 on 2007-12-05
> **BLTicklemonster said:**
> Would it be better to have samba on both of the machines?

Depending on the setup... 

at least one should be the Samba server and one should be the Samba client. You could always install both on both and have it both ways... man, can I use the word 'both' any more there?

There are a couple of good Samba HowTo's floating around the forum somewhere.

---

### Post by jasonpeinko on 2007-12-05
well i have my samba on my desktop setup fine, so why does it now show up?

---

### Post by stalker145 on 2007-12-05
> **jasonpeinko said:**
> well i have my samba on my desktop setup fine, so why does it now show up?

Which Samba are you saying is set up on the desktop? Is it the 'samba' package or the 'smbclient' package?

I would suggest using this [HowTo]("http://ubuntuforums.org/showthread.php?t=202605"). I don't have any Windows machines commonly on my network (just Ubuntu) and it works perfectly for me. Just make sure that any computers you wish to use to access the shared files have the smbclient installed.

---

### Post by HermanAB on 2007-12-05
Here you go: [http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

