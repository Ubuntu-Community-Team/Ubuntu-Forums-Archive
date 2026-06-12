---
title: "Unable to connect to US and Main Repositories"
date: 2007-12-17
forum: General Help
---

### Post by emptythevoid on 2007-12-17
For some reason, I am unable to get anything from the US or the Main Repositories (I'm in the US).  When I hit Reload, everything it tries to load gets a Failed.   I have a good 1mbps internet connection (I'm using it right now).  I told Synaptics to use "other" and to scan for the best repository.  Most of the time it says that no good repositories can be found, but it finally showed a server in the Netherlands (???).  I don't know what's up, but I figured I would make a note here and see if there's anything going on that's out of my control.  It's 9:45pm Eastern time at the moment, but I've been experiencing this problem for the past two hours or so.  Thanks for any feedback you all may have!

BTW, I'm not sure what would have changed on my end.  I can't think of anything I've done that would have caused this to suddenly start, so I'm hoping that it's something I didn't do.

---

### Post by emptythevoid on 2007-12-17
UPDATE:  It looks like if I manually tell it to use a repository and set it to do FTP instead of HTTP, I have better results.  I haven't had to do this before.  Any idea what might be up?

---

### Post by 52rockwell on 2007-12-17
Meee 2.  Trying to install from the 710 mini ISO cd.  No good mirrors for hours now.

---

### Post by emptythevoid on 2007-12-17
I'm sorry we're both having problems, but that makes me feel a little better.  

I have gotten things to work for now, though.  I went into Synaptics->Settings->Repositories

On the "Ubuntu Software" tab, I clicked on the drop-down menu for "Download From" and chose Other.  I chose a US server that let me switch the HTTP to FTP and it seems to be doing OK for now.  Still don't know what's going on.  Guess the internets are breaking. :P

---

### Post by 52rockwell on 2007-12-17
Im leaning more to the 
Its a neo-cabalistic NWO conspiracy between the Reptillians at the Underground base in Dulce and the Ancient Aryans in the bases at Antartica...:)
   Hey we have to blame it on somebody.

---

### Post by emptythevoid on 2007-12-17
My girlfriend suggested it was a denial of service attack by Microsoft. :P

---

### Post by 52rockwell on 2007-12-17
Im leaning more to the 
Its a neo-cabalistic NWO conspiracy between the Reptillians at the Underground base in Dulce and the Ancient Aryans in the bases at Antartica...:)   Who are the ones Microsofft outsourses the Denial of Service work to
   Hey we have to blame it on somebody.

---

### Post by emptythevoid on 2007-12-17
It's 11:18 Eastern here in the US and the US repository (HTTP) is still not responding.

---

### Post by emptythevoid on 2008-01-02
I'm still not able to connect to the Main or the US servers when using apt-get or synaptic.  Manually setting an FTP server works OK, but I get a lot of the security repositories timing out.  Does anyone have any thoughts?  Have I messed something up?

---

### Post by emptythevoid on 2008-01-03
Welp, I have a final confirmation for my problem - it's definitely my laptop.  I have no idea what the problem is, but I've tested the updates using a different Ubuntu 7.10 laptop with same networking conditions and it works fine.  So while I have no idea what's wrong, it's something wrong on my end.  Guess I'll be re-installing on my main laptop.

---

